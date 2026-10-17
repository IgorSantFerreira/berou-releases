# Berou — Releases

**Canal de distribuição do Berou para Windows.**

O Berou é um aplicativo de streaming de tela e áudio voltado a sessões compartilhadas entre amigos. Este repositório reúne os **instaladores e as notas de versão** do aplicativo, sem expor os repositórios privados de desenvolvimento.

> [!IMPORTANT]
> O Berou está em fase beta. Algumas versões podem conter problemas conhecidos ou mudanças de comportamento. Durante o beta fechado, os downloads são restritos aos participantes autorizados; a disponibilidade pública dependerá da visibilidade deste repositório.

## Baixar o Berou

### [⬇️ Acessar versões e downloads](https://github.com/IgorSantFerreira/berou-releases/releases)

Na página de **Releases**, abra a publicação mais recente do canal desejado e baixe o instalador para Windows em **Assets**. A lista de lançamentos é atualizada pelo próprio GitHub a cada nova publicação. Se estiver vazia, ainda não há instalador publicado neste canal.

- **Beta:** versões de teste, identificadas como pré-lançamento (*pre-release*).
- **Estável:** versões destinadas ao uso geral, quando esse canal estiver disponível.

> **Sobre o link "latest":** o GitHub não inclui versões marcadas como *pre-release* no endpoint `/releases/latest`. Portanto, durante as betas, use a [lista de releases](https://github.com/IgorSantFerreira/berou-releases/releases) para encontrar a publicação mais recente. O atualizador do Berou deverá consultar a API e selecionar explicitamente o canal beta ou estável.

## Instalação

1. Baixe o instalador `.exe` nos **Assets** da release escolhida.
2. Confira o SHA-256 do arquivo com o manifesto publicado na mesma release.
3. Execute o instalador e siga as instruções exibidas.

**Windows SmartScreen:** a assinatura Authenticode não garante, por si só, confiança automática do Windows. Certificados de teste ou não reconhecidos podem resultar em avisos. Confirme a origem do download antes de executar o arquivo.

## Como funcionam as versões

Cada publicação terá:

- Tag de versão correspondente à versão efetiva do instalador;
- Identificação clara de **beta** ou **estável**;
- Arquivo instalador de Windows;
- Resumo das mudanças e dos problemas conhecidos;
- Hash SHA-256 para conferência de integridade.

O procedimento para publicar novas versões está em [docs/RELEASE_PROCESS.md](docs/RELEASE_PROCESS.md). O contrato proposto para consulta da versão mais recente está em [docs/UPDATE_CHANNELS.md](docs/UPDATE_CHANNELS.md).

## Código-fonte e desenvolvimento

Este repositório é **exclusivo de distribuição**: não contém os componentes de desenvolvimento, a infraestrutura, os serviços de sinalização nem segredos operacionais do Berou. Os instaladores ficam anexados às GitHub Releases, **não versionados diretamente no Git**.

---

**Berou** · Desenvolvido por **Igor Santana Ferreira**.
