# Canais de atualização do Berou

Este documento define o **contrato proposto** para o cliente Berou descobrir novas versões no GitHub Releases. **Não significa que o atualizador já esteja integrado.** O código do atualizador deve ser implementado e validado separadamente nos repositórios privados.

## Fonte de versões

Repositório de distribuição: `IgorSantFerreira/berou-releases`.

```text
GET https://api.github.com/repos/IgorSantFerreira/berou-releases/releases?per_page=30
```

Para acessar um repositório privado, é necessário autenticação autorizada. **Não incluir PAT ou token de acesso privado dentro do instalador.** Na eventual abertura pública do repositório, a leitura das releases poderá ser feita sem credenciais, respeitando os limites da API.

## Como escolher a versão

| Canal no Berou | Seleção proposta |
| --- | --- |
| **Beta** | Release publicada e não rascunho, com `prerelease = true`, versão superior à instalada e asset Windows válido |
| **Estável** | Release publicada e não rascunho, com `prerelease = false`, versão superior à instalada e asset Windows válido |

Regras:

1. Ler apenas as releases do repositório oficial; ignorar drafts, versões incompatíveis e releases sem instalador reconhecido.
2. Interpretar as tags conforme a convenção de versionamento efetivamente usada no Berou (por exemplo, SemVer com sufixo `-beta.N`).
3. Comparar versões **semanticamente**, não apenas datas de publicação, textos ou ordem da resposta da API.
4. Exibir versão, notas e confirmação ao usuário antes da instalação, conforme a UX aprovada.
5. Baixar o instalador por `browser_download_url` retornado pela API, sem montar URLs por suposição.
6. Verificar SHA-256 contra o manifesto publicado, além de aplicar as verificações de assinatura e origem que o cliente suportar.
7. Tratar falhas de rede, rate limit, arquivo ausente, hash incorreto e instalação interrompida sem quebrar a versão atual.
8. Não fazer downgrade automático e não aceitar asset de outra arquitetura/sistema operacional.

O manifesto SHA-256 publicado no **mesmo repositório** protege contra erros de transferência e inconsistências, mas não substitui uma cadeia de assinatura confiável nem mecanismos de autenticidade contra comprometimento do próprio repositório.

## Por que não usar `/releases/latest` no beta?

O GitHub considera a *latest release* a publicação completa mais recente; **pré-releases não entram** em seu endpoint dedicado de última release. Isso significa que:

- `/releases/latest` e `/releases/latest/download/arquivo.exe` servem para versões estáveis publicadas.
- Um aplicativo inscrito no canal **beta** precisa listar releases e filtrar `prerelease = true`, ou usar um manifesto de canal específico sob controle do projeto.
- O link humano do README aponta para `/releases`, que permite localizar os lançamentos disponíveis.

Referências oficiais: [API de releases](https://docs.github.com/en/rest/releases/releases), [links de releases](https://docs.github.com/en/repositories/releasing-projects-on-github/linking-to-releases).

## Pendências para integração real

- Definir e congelar o padrão de tag e a identificação exata do asset do instalador.
- Escolher onde ficará a preferência de canal beta/estável.
- Implementar o cliente HTTP e as verificações de integridade no Berou.
- Testar uma sequência real **Beta 10 → Beta 11** com e sem rede.
- Definir política de rollout e rollback antes de habilitar atualização automática.

**Responsável:** Igor Santana Ferreira.
