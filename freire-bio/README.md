# Bio — Freire Educação

Página de links da bio do Dr. Lauro e da Dra. Renata, publicada em https://bio.1mesemumdia.com/.

Este diretório é **independente da landing page que está na raiz deste repositório**. O workflow de publicação lê apenas `freire-bio/site/` e envia esses arquivos ao projeto Cloudflare Pages da bio.

## Destinos

- Imersão 1 Mês em 1 Dia: https://imersao.1mesemumdia.com/
- SDOLab: https://maquina-faturamento-freire.floot.app/ (mantido)

## Configuração inicial necessária

1. No painel Cloudflare, abra **Workers & Pages**, escolha o projeto que atende ao domínio `bio.1mesemumdia.com` e copie o **nome técnico exato do projeto**. Não presuma que é igual ao domínio.
2. No GitHub deste repositório, acesse **Settings → Secrets and variables → Actions → Variables → New repository variable** e crie `CLOUDFLARE_BIO_PROJECT`, com o nome técnico do projeto Cloudflare Pages como valor.
3. Na conta Cloudflare, crie um **API Token** restrito à conta com permissão **Account → Cloudflare Pages → Edit**. Não copie o token no chat nem em um arquivo do repositório.
4. No GitHub, em **Settings → Secrets and variables → Actions → Secrets → New repository secret**, cadastre `CLOUDFLARE_API_TOKEN` com o token e `CLOUDFLARE_ACCOUNT_ID` com o **Account ID** da conta Cloudflare (não o Zone ID).
5. Abra **Actions → Publicar bio Freire no Cloudflare Pages → Run workflow** e execute na branch `main`.
6. Após o deploy ter sido concluído com sucesso, visite https://bio.1mesemumdia.com/ e teste ambos os botões. O endereço da Imersão deve começar com https://imersao.1mesemumdia.com/ (com parâmetros UTM).

## Publicações posteriores

Quando os segredos e a variável estiverem configurados, atualizações em `freire-bio/site/**` na branch `main` disparam o workflow automaticamente. O workflow também pode ser iniciado manualmente.

O job de publicação fica **ignorado** enquanto a variável `CLOUDFLARE_BIO_PROJECT` estiver vazia, para impedir que o GitHub publique em um projeto errado. Nenhum DNS ou domínio é modificado por essa configuração.

**Atenção:** o fluxo prepara o deploy no projeto Cloudflare Pages existente; ele não configura domínio, DNS ou credenciais automaticamente.

Referências oficiais:

- https://developers.cloudflare.com/pages/how-to/use-direct-upload-with-continuous-integration/
- https://github.com/cloudflare/wrangler-action
