# EletroGest

PWA de gestão de manutenção elétrica: clientes, avaliação técnica, contratos com assinatura digital, agenda, ordens de serviço, relatórios, financeiro, deslocamentos e horas trabalhadas. Funciona no computador e no celular, e pode ser instalado.

## Arquivos

- `index.html`: o aplicativo inteiro (HTML, CSS e JS num único arquivo)
- `manifest.webmanifest`: nome, cores e ícones para instalação
- `sw.js`: service worker (funciona sem internet depois do primeiro acesso)
- `icons/`: ícones do app

## Publicar no GitHub Pages

1. Crie um repositório e envie todos os arquivos mantendo a pasta `icons/`.
2. Em **Settings > Pages**, escolha a branch `main` e a pasta `/ (root)`.
3. Acesse `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.
4. Para instalar: no PC, use o ícone de instalar na barra de endereço ou vá em Configurações > Instalar aplicativo. No Android, use o menu do Chrome > Instalar app. No iPhone, use Compartilhar > Adicionar à Tela de Início.

## Atualizações

Ao publicar mudanças, altere `CACHE = 'eletrogest-v1'` em `sw.js` (por exemplo, para `v2`).

## Dados

Os dados ficam salvos no `localStorage` do aparelho (chave `eletrogest-v2`). Dados da versão anterior são migrados automaticamente na primeira abertura. Em Configurações é possível restaurar os dados de exemplo.
