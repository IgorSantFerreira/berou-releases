# Publicação de releases do Berou

Este repositório hospeda **apenas os arquivos de distribuição**. Os componentes de desenvolvimento permanecem em seus repositórios privados. Nenhuma etapa deste procedimento depende de GitHub Actions.

## 1. Preparar a versão

- Concluir e validar os testes locais do candidato.
- Confirmar a versão efetiva embutida no aplicativo e no instalador.
- Gerar o instalador Windows pelo fluxo oficial de build do Berou.
- Conferir a assinatura Authenticode e suas limitações de confiança.
- Realizar um smoke test de instalação, inicialização, conexão, transmissão e encerramento, conforme o checklist do projeto.
- Verificar se o instalador não inclui credenciais, artefatos internos, dados pessoais ou configuração restrita.

> Não publicar um instalador que ainda não passou na validação local. A criação deste repositório não significa que a Beta 10 já esteja pronta.

## 2. Gerar hash de integridade

No PowerShell, dentro da pasta que contém o instalador:

```powershell
Get-FileHash -LiteralPath ".\NOME-REAL-DO-INSTALADOR.exe" -Algorithm SHA256
Get-AuthenticodeSignature -LiteralPath ".\NOME-REAL-DO-INSTALADOR.exe" |
    Format-List Status,StatusMessage,SignerCertificate
```

Salve o SHA-256 no arquivo `SHA256SUMS.txt` da **mesma release** no formato abaixo (sem os colchetes):

```text
[sha256_em_hexadecimal]  NOME-REAL-DO-INSTALADOR.exe
```

O hash deve ser calculado **depois** da assinatura e de todas as alterações do instalador. Um certificado de teste pode produzir uma assinatura criptograficamente presente, mas não confiável no Windows.

## 3. Criar release manualmente

1. Abra [Releases](https://github.com/IgorSantFerreira/berou-releases/releases) e escolha **Draft a new release**.
2. Crie a tag com a **versão real** do build, por exemplo `vX.Y.Z-beta.N`. Não assuma números de versão a partir do nome da rodada Beta 10.
3. Selecione `main` como branch de destino da tag.
4. Informe um título claro: `Berou vX.Y.Z — Beta N`.
5. Para builds beta, marque **Set as a pre-release / This is a pre-release**.
6. Preencha as notas usando [RELEASE_NOTES_TEMPLATE.md](RELEASE_NOTES_TEMPLATE.md).
7. Anexe o instalador `.exe` e o `SHA256SUMS.txt` à release — **não adicione esses binários ao histórico Git**.
8. Revise os nomes, versões, hash e observações antes de publicar.

Enquanto o repositório for **privado**, downloads e a API de releases exigirão acesso autorizado. Mudar a visibilidade será uma decisão separada.

## 4. Validar após publicar

- [ ] A release aparece com a tag e o canal corretos.
- [ ] O instalador e o arquivo de hash estão em **Assets**.
- [ ] O instalador baixado possui o mesmo SHA-256 do arquivo publicado.
- [ ] O instalador efetivamente informa a versão pretendida.
- [ ] Um Windows de teste consegue baixar, instalar e iniciar o Berou.
- [ ] As notas de versão refletem o que foi validado.
- [ ] Nenhum segredo ou componente privado foi incluído.

## 5. Política de atualização

- Nunca dependa de `/releases/latest` para o canal **beta**: ele ignora pré-releases.
- Para a listagem de versões, use a [API de Releases](https://docs.github.com/en/rest/releases/releases#list-releases) e aplique a política descrita em [UPDATE_CHANNELS.md](UPDATE_CHANNELS.md).
- Recomenda-se **manter um nome de asset previsível** por canal se o cliente for usar links de download automatizados. O nome definitivo deve ser combinado com o fluxo de build, sem renomear instaladores às cegas.
- Publicar uma release não modifica automaticamente o atualizador dentro do aplicativo: essa integração precisa ser implementada e testada no cliente Berou.

## 6. Boas práticas

- Não usar GitHub Actions enquanto a política atual de testes locais estiver vigente.
- Não adicionar `.pfx`, chave privada, token ou segredo, mesmo num repositório privado.
- Não sobrescrever silenciosamente binários de releases já distribuídas. Uma correção deve preferencialmente gerar nova versão/tag.
- Manter as notas objetivas: novidades, correções, problemas conhecidos e compatibilidade.

**Responsável:** Igor Santana Ferreira.
