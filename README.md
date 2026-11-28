# Projeto DevOps: dupla-12

Site: https://colacco.github.io/projeto-devops-dupla-12/ (status em /status.html)

Imagem: ghcr.io/colacco/projeto-devops-dupla-12

## O fluxo completo
1. O git push na main dispara o CI (testes e build) e a publicação do site com status.
2. O envio de uma tag v* dispara o fluxo "Publicar imagem".
3. O fluxo roda os testes e constrói a imagem, gravando a versão pela tag.
4. A imagem é publicada no ghcr.io com o nome da tag.
5. No Codespace, docker pull e docker run sobem o contêiner, e o curl em /saude confirma a versão.

## Linha do tempo
- v1: primeira imagem publicada, respondendo em /saude na porta 5000.
- v2: a API passou a escutar na porta 5001. Os testes passaram, mas o contêiner não respondia na porta 5000.
- v3: o git revert desfez a mudança da porta, sem apagar o histórico.

## O que os testes não pegaram
Os testes usam o cliente de teste do Flask, que não abre a porta de rede. Para verificar, o pipeline subiria o contêiner e chamaria /saude com curl na porta 5000 antes de publicar a imagem.

## Quem fez o quê
Gabriel Ramos Colaço (aluno A, dupla-12, porta 5000): criei a página de status com testes antes da publicação, conferi a visibilidade da imagem, fiz o rollback no repositório com git revert, publiquei a v3 e criei este README.

A completar pelo aluno B