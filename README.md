# Plantão Zen

Aplicação de cuidado pessoal com check-in, contatos, análises, plano de segurança e recursos de emergência. Inclui a revisão visual completa, temas claro e escuro e navegação responsiva.

## Tecnologias
React 19, TypeScript, Vite, Tailwind CSS, Express, tRPC, Drizzle e MySQL.

## Executar
Use Node.js 22.12+ ou 24 e pnpm 10.18.0.

1. Execute `pnpm install --frozen-lockfile`.
2. Copie `.env.example` para `.env` e preencha os dados do seu ambiente original.
3. Execute `pnpm dev`.

O login depende da configuração OAuth Manus existente. Este pacote não cria automaticamente o banco nem fornece credenciais.

```sh
pnpm check
pnpm test
pnpm build
pnpm start
```

`pnpm db:migrate` aplica as migrações ao banco configurado; confira o destino e faça backup antes de executar em produção.

## Enviar ao GitHub
Extraia o ZIP. Envie o conteúdo da pasta `plantao-zen` para a raiz do repositório, incluindo `.gitignore` e `.env.example`. Não envie o ZIP como se fosse o código.

Para um repositório novo e vazio, abra o terminal na pasta extraída:

```sh
git init
git add .
git commit -m "Adiciona Plantão Zen com interface renovada"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/plantao-zen.git
git push -u origin main
```

Substitua SEU_USUARIO pelo seu usuário. Se o repositório já existe e possui arquivos, clone-o primeiro e copie estes arquivos para a pasta clonada, sem apagar a pasta `.git`. Não use push forçado.

## Estrutura
- `client/`: interface web atualizada.
- `server/`: API e autenticação.
- `shared/`: tipos compartilhados.
- `drizzle/`: esquema e migrações.
- `patches/`: patch de dependência usado pelo pnpm.
- `desktop/`: wrapper desktop original, sem executáveis. Configure PLANTAO_ZEN_URL para sua implantação.
- `REDESIGN.md`: mudanças visuais e validações da entrega anterior.

## Publicação
GitHub armazena o código. GitHub Pages sozinho não executa o backend Express nem o MySQL. Para usar o sistema completo, publique em um ambiente com Node.js e configure o banco e OAuth.

Este pacote contém os fontes web e desktop. Vídeos, APKs, instaladores, cache, node_modules e arquivos de ambiente reais não foram incluídos. As referências a binários preservados em REDESIGN.md dizem respeito ao pacote completo anterior, não a este ZIP para GitHub.
