# C&J Eletric Solutions

PWA de gestão de manutenção elétrica: clientes, planos, avaliação técnica, contratos com assinatura digital, agenda, ordens de serviço, orçamentos (avulsos e de clientes), relatórios, financeiro, deslocamentos e horas trabalhadas. Funciona no computador e no celular e pode ser instalado.

## Arquivos

- `index.html`: o aplicativo inteiro (HTML, CSS e JS num único arquivo)
- `manifest.webmanifest`: nome, cores e ícones para instalação
- `sw.js`: service worker (abre sem internet depois do primeiro acesso)
- `firestore.rules`: regras de segurança do banco de dados
- `icons/`: ícones do app

## 1. Publicar no GitHub Pages

1. Crie um repositório e envie todos os arquivos, mantendo a pasta `icons/`.
2. Em **Settings > Pages**, escolha a branch `main` e a pasta `/ (root)`.
3. O endereço fica `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.

Sem o Firebase configurado, o app já funciona, mas sem login e salvando só no aparelho.

## 2. Configurar o Firebase (login e backup na nuvem)

O plano gratuito (Spark) é suficiente.

1. **Criar o projeto:** acesse https://console.firebase.google.com, clique em *Adicionar projeto* e siga os passos (o Google Analytics pode ficar desativado).
2. **Registrar o app da Web:** em *Configurações do projeto > Seus apps*, clique no ícone `</>`, dê um nome e copie o objeto `firebaseConfig`.
3. **Colar no app:** abra o `index.html`, procure o bloco `CONFIGURAÇÃO DO FIREBASE` no começo do script e preencha `apiKey`, `authDomain`, `projectId`, `storageBucket`, `messagingSenderId` e `appId`.
4. **Ativar os logins:** em *Authentication > Método de login*, ative **Google** e **E-mail/senha**.
5. **Autorizar o endereço do GitHub:** em *Authentication > Configurações > Domínios autorizados*, adicione `SEU-USUARIO.github.io`.
6. **Criar o banco:** em *Firestore Database > Criar banco de dados*, escolha o modo de produção e a região `southamerica-east1 (São Paulo)`.
7. **Regras de segurança:** copie todo o conteúdo de `firestore.rules`, cole em *Firestore Database > Regras* e clique em *Publicar*. Não é preciso editar nada no arquivo.
8. Envie o `index.html` atualizado para o GitHub.
9. **Entre primeiro:** logo depois de publicar, entre no app com o seu e-mail. A primeira pessoa a entrar vira administradora.

### Como funciona

- **Login:** com Google ou com e-mail e senha. Contas de e-mail e senha precisam confirmar o e-mail pelo link enviado antes de acessar.
- **Administradores:** a primeira pessoa a entrar vira administradora. Quem entrar depois aparece em *Configurações > Usuários e acesso* como pedido pendente, e só usa o app depois que um administrador aceitar.
- **Poderes dos administradores:** aceitar ou recusar pedidos, liberar um e-mail antes mesmo de a pessoa entrar, tornar alguém administrador (com os mesmos poderes), tirar de administrador e remover o acesso de qualquer pessoa, inclusive o próprio. Sempre precisa sobrar pelo menos um administrador.
- **Acesso removido:** a pessoa perde o acesso na hora, em todos os aparelhos, e os dados da empresa são apagados do aparelho dela. Ela não consegue pedir acesso de novo até um administrador liberar.
- **Dados compartilhados:** todas as pessoas com acesso usam os mesmos dados da empresa (pasta `empresas/cj-eletric`).
- **Salvamento automático:** cada alteração é gravada no aparelho na hora e enviada para a nuvem em cerca de 1 segundo. Sem internet, fica guardada e sobe sozinha quando a conexão volta.
- **Backup automático:** cada alteração gera um backup (os últimos 30 ficam guardados), e há também um backup por dia (últimos 30 dias). Para restaurar, vá em *Configurações > Conta e backup > Ver e restaurar backups*.
- **Vários aparelhos:** as mudanças feitas no computador aparecem no celular (e vice-versa) sem precisar recarregar.
- **Arquivo de backup:** em Configurações também é possível exportar e importar um arquivo `.json`.

## 3. Gesto de voltar no Android

No app instalado (ou aberto pelo Chrome), o gesto/botão de voltar navega para a tela anterior dentro do app. Na tela de início ele não fecha o aplicativo: permanece no início.

## Atualizações

Ao publicar mudanças, altere `CACHE = 'cj-eletric-v9'` em `sw.js` (por exemplo, para `v5`), para os aparelhos baixarem a nova versão.
