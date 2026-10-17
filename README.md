# Berou

### Compartilhe sua tela. Reúna seus amigos. Assista junto.

O **Berou** é um aplicativo de compartilhamento de tela e áudio para Windows, pensado para quem quer transmitir um jogo, mostrar um aplicativo ou simplesmente compartilhar a tela com amigos — em uma sala própria e com foco em **baixa latência e simplicidade**.

O projeto está em desenvolvimento ativo e é distribuído em **versões beta**. Queremos que assistir ou transmitir seja uma experiência direta, sem a complexidade de configurar um servidor de streaming.

## ⬇️ Baixar o Berou

**[Acessar a versão mais recente e baixar o instalador para Windows →](https://github.com/IgorSantFerreira/berou-releases/releases)**

Para instalar:

1. Clique no link acima para abrir a página **Releases**.
2. Abra a **Beta mais recente** e expanda a seção **Assets**, caso esteja recolhida.
3. Baixe o arquivo do **instalador Windows (`.exe`)**. Não escolha os arquivos automáticos `Source code (zip)` ou `Source code (tar.gz)`: eles não são o instalador.
4. Execute o instalador e siga as instruções.

> **Acesso:** enquanto este repositório for privado, somente contas autorizadas conseguirão visualizar e baixar as releases. O acesso público dependerá de uma futura mudança de visibilidade.

## O que queremos construir

O Berou nasceu da ideia de tornar o compartilhamento de tela entre amigos mais prático e responsivo, especialmente para jogos. Nosso foco é:

- **Baixa latência:** reduzir o atraso entre o que acontece na tela de quem transmite e o que os amigos assistem.
- **Experiência simples:** criar uma sala, convidar pessoas e começar a compartilhar sem uma configuração extensa.
- **Áudio e imagem juntos:** transmitir a tela com o som do aplicativo e permitir que o grupo converse.
- **Conexão adaptável:** buscar conexão direta entre participantes quando possível, com alternativas de transporte quando a rede não permite.

Não buscamos substituir uma plataforma de transmissões públicas. A proposta do Berou é uma experiência mais próxima e direta, voltada a **salas e grupos pequenos**.

## O que o Berou oferece hoje

- **Salas por convite** para reunir participantes.
- **Compartilhamento de tela e áudio** de aplicativos e jogos.
- **Player dedicado** para acompanhar a transmissão.
- **Chat de texto e voz** dentro da experiência de sala.
- **Transporte P2P quando viável**, com fallback por relay conforme as condições da conexão.
- **Instalador para Windows** e desenvolvimento contínuo por versões.

## Limitações atuais

O Berou ainda é um **software beta**, e é importante saber o que esperar:

- **Somente Windows:** não há versões nativas para macOS, Linux ou dispositivos móveis.
- **Instabilidade é possível:** quedas de conexão, falhas de captura, dessincronização de áudio e problemas ao alternar entre aplicações ou jogos podem ocorrer. As correções evoluem de uma beta para outra.
- **Rede e hardware importam:** latência, fluidez e disponibilidade de conexão direta dependem da máquina de quem transmite, da rede dos participantes e do transporte utilizado.
- **Qualidade compartilhada:** o host produz um fluxo de vídeo para os espectadores; ainda não há ajuste independente de qualidade para cada pessoa.
- **Capacidade controlada:** salas e conexões via relay podem sofrer limites técnicos ou operacionais durante os testes.
- **Recursos ainda em evolução:** suporte a câmera e outras expansões não devem ser considerados disponíveis nesta fase.

As limitações específicas de cada build, quando conhecidas, são informadas nas **notas da própria release**.

## Segurança e avisos do Windows

Baixe o Berou **somente pelo repositório oficial**. O Windows pode exibir um aviso do SmartScreen mesmo quando um instalador possui assinatura Authenticode, especialmente durante a fase beta. Confira a origem do arquivo antes de decidir executá-lo.

Quando disponível nos Assets, o `SHA256SUMS.txt` permite conferir a integridade do instalador baixado.

## Sobre este repositório

Aqui ficam **os instaladores e as notas das versões** do Berou. O código-fonte de desenvolvimento e os componentes de infraestrutura não fazem parte deste repositório.

Para conhecer a engenharia e as decisões técnicas do projeto, visite o [showcase técnico do Berou](https://github.com/IgorSantFerreira/berou-showcase).

---

Desenvolvido por **Igor Santana Ferreira**.
