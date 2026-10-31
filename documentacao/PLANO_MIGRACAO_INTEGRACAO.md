# Migração e integração — Facilita (FrontEnd e BackEnd)

## Objetivo
Manter o FrontEnd e o BackEnd em repositórios **separados na conta JotaMaciel**, preservando os respectivos autores e históricos. O Mobile fica para uma etapa posterior.

## Repositórios de origem
- FrontEnd: https://github.com/fritute/facilita-front-end
- BackEnd: https://github.com/gioxavier7/servidor-facilita
- Mobile (posterior): https://github.com/kbueno011/Facilita--Mobile--TCC

## Destinos desejados (ainda não criados)
- `JotaMaciel/facilita-frontend`
- `JotaMaciel/facilita-backend`

**Importante:** importar/fazer fork preservando histórico, verificar licenças e manter créditos de autoria. Não copiar tokens, arquivos .env reais, dados pessoais ou segredos de produção.

## Achados da análise inicial (não são testes de execução)
1. O FrontEnd usa React 18, Vite 5, Socket.IO Client e TypeScript; o BackEnd usa Express 5, Prisma 6, MySQL e Socket.IO. A compatibilidade efetiva das rotas e eventos ainda precisa de teste.
2. O FrontEnd apresenta nomes de variáveis de ambiente diferentes no README (`VITE_API_BASE_URL`, `VITE_WEBSOCKET_URL`) e no `.env.example` (`VITE_API_URL`, `VITE_WS_URL`). É necessário identificar quais nomes o código realmente consome e padronizar a documentação.
3. O `.env.example` do FrontEnd aponta a API para um endereço Azure e o WebSocket para `ws://localhost:3001`. Essa combinação pode não funcionar em produção sem configuração adicional.
4. O BackEnd exige Node.js >=22 no `package.json`, mas seu README informa Node.js 16+. Atualizar para a versão suportada e testar.
5. O README do FrontEnd documenta `npm run test` e `npm run type-check`, ausentes do `package.json` atual. Corrigir scripts ou documentação após verificar a suíte real.
6. O README do BackEnd instrui copiar `.env.example`, mas esse arquivo não apareceu na listagem da raiz. Criar um exemplo sem segredos a partir de análise das configurações de código.

## Ordem recomendada
1. Importar os dois repositórios no perfil JotaMaciel, mantendo o histórico.
2. Auditar segredos e variáveis de ambiente; criar modelos seguros de configuração local.
3. Preparar MySQL, executar migrações Prisma e iniciar BackEnd em ambiente de testes.
4. Padronizar URL e base path da API e configuração do Socket.IO no FrontEnd.
5. Testar fluxo mínimo: healthcheck, cadastro/login, busca de serviços e comunicação cliente-servidor.
6. Testar funcionalidades avançadas (chat, pagamentos em sandbox, localização), sem transações reais.
7. Criar commits temáticos, PRs e atualizar README central com os novos repositórios.

## Estado da validação
Somente inspeção de arquivos do GitHub nesta etapa. **Não foi confirmado** que os projetos compilam, iniciam, conectam ao banco ou funcionam ponta a ponta.
