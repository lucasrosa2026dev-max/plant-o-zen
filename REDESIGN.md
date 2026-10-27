# Plantão Zen — revisão visual de todas as páginas

Atualização de 26/10/2026 sobre o projeto completo enviado em 21/10/2026.

## O que mudou

- Identidade consistente em azul-petróleo e verde, com cores específicas para emergência, avisos e sucesso.
- Menu lateral organizado em dia a dia, rede de apoio e preferências.
- Navegação móvel com cinco atalhos; o menu “Mais” dá acesso a todas as páginas.
- Login e cadastro redesenhados, preservando o provedor de autenticação existente.
- Visão geral com acesso rápido ao check-in e à emergência.
- Contatos, análises e detalhes, check-in, plano de segurança, mensagens, perfil, smartwatch e configurações com componentes compartilhados.
- Página 404 em português, estados vazios e foco de teclado revisados.
- Temas claro e escuro com tokens semânticos; zoom do navegador liberado.
- Menu móvel com foco contido, fechamento por Escape e nomes acessíveis. Alternâncias e seleções expõem seu estado às tecnologias assistivas.
- Os dados, endpoints, consultas, mutações, autenticação e regras de negócio existentes foram preservados. A mudança do atalho principal da visão geral leva ao check-in; emergência continua disponível em destaque.

## Arquivos principais

- `client/src/components/zen/Primitives.tsx`: cartão, botão, campos e marca compartilhados.
- `client/src/components/zen/AppShell.tsx`: estrutura, menus, navegação móvel e alternância de tema.
- `client/src/components/zen/AuthScreen.tsx`: login e cadastro.
- `client/src/index.css`: tokens de cor, temas e estilos responsivos.
- `client/src/pages/Portal.tsx`, `Wellbeing.tsx` e `NotFound.tsx`: aplicação do sistema visual.
- `client/index.html` e `client/public/manifest.webmanifest`: zoom e cores do navegador.

## Executar

Use Node.js 22.12+ ou 24 LTS e a versão de pnpm definida no package.json.

```sh
pnpm install --frozen-lockfile
pnpm dev
```

Mantenha a configuração de ambiente do projeto original, incluindo banco de dados e OAuth. Nenhuma credencial nova foi criada ou incluída nesta atualização. Para o frontend isolado, `pnpm dev:static` precisa que a API existente esteja acessível na mesma origem; não é um modo de demonstração sem backend.

```sh
pnpm check
pnpm test
pnpm build
```

Para aplicar em outra cópia da mesma versão, substitua os arquivos de interface acima e adicione a pasta `client/src/components/zen`. Em seguida, compile e publique conforme o processo atual do projeto. Não substitua arquivos de ambiente.

## Validação

- TypeScript: verificação sem erros.
- Build Vite de produção: concluído.
- Testes existentes: 6 aprovados em 2 arquivos.
- Interface: 78 combinações de páginas, resoluções e temas, mais 7 verificações de menu, alternância de tema e estados vazios. Larguras 1440, 390 e 320 px. Nenhum overflow horizontal, falha de verificação ou erro de execução capturado.
- As verificações visuais usaram respostas de API simuladas e dados fictícios apenas no navegador de teste. Não há bypass de autenticação, mocks nem contas de demonstração no código de produção.

## Limites desta entrega

Não foi publicado um site nem feita migração de banco. OAuth real, envio de notificações, chamadas, mensagens e persistência em produção não foram exercitados com credenciais reais. Os testes existentes não equivalem a uma auditoria de segurança.

O Vite ainda informa um bundle principal acima de 500 kB (aproximadamente 552 kB / 159 kB gzip), um ponto futuro para separação de código por rota. O aviso sobre `/api/platform/config.js` corresponde ao script clássico de configuração já existente; ele é gerado pelo plugin do projeto.

O ZIP original também contém vídeos e binários antigos de desktop/Android. Eles foram preservados, mas não recompilados. O novo visual está no código-fonte web; para aplicativos empacotados, faça uma nova compilação a partir dele. O tamanho do pacote continua próximo ao original devido a esses arquivos.
