## Olá, eu sou o Henrique 👋

**Desenvolvedor full stack** em São Paulo · PHP/Laravel · Vue.js · React Native

Desde 2023 construo e sustento sistemas de missão crítica para a **Polícia Militar do Estado de São Paulo**, do banco de dados ao deploy. Fora do trabalho, publico apps Android próprios na Google Play.

🇺🇸 *Full stack developer (Laravel, Vue, React Native) building mission-critical public safety systems. Open to remote work.*

---

### 🏛️ No trabalho: plataforma de gestão operacional da PMESP
> Código confidencial. Abaixo, o que construí e os resultados. **[Ler o case completo →](cases/ecoordop.md)**

- **Sistema da operação eleitoral** (VILT): usado por quase **600 unidades**, com painéis de efetivo por escola (**33 mil policiais em 12 mil escolas**)
- **Operação Verão:** troquei planilhas por um sistema único e reduzi o planejamento anual da operação de **12 para 3 meses**
- **Sorteio de distribuição de efetivo** (mais de 3 mil policiais): bug corrigido em **48 horas**, antes da abertura das inscrições
- **Servidor Linux legado** que caía toda semana, estabilizado após meses de diagnóstico sem documentação
- **Migração de legado para VILT** (Vue 3, Inertia, Laravel 12, Tailwind), com mais de 160 commits próprios em uma base de quase 900
- **Teste de carga com k6:** 450 usuários simultâneos e 29 mil requisições com **0% de erro**
- **CI/CD com GitHub Actions** e runners self-hosted; integrações com LDAP, WebService de RH com **failover entre 7 nós** e banco legado Sybase; monitoramento próprio com alertas e runbook

### 📱 Projetos próprios

| Projeto | O que é | Stack |
|---|---|---|
| [**Escala Plantão**](https://github.com/Porzelt/escala-plantao) | Gestão de escalas de plantão: distribuição justa com sorteio reprodutível, RBAC por módulo, isolamento por unidade, exportação em fila e auditoria. CI verde, 87,8% de cobertura, k6 com 450 usuários e 0% de erro | Laravel 12 · Inertia · Vue 3 · MariaDB e PostgreSQL · Redis/Horizon · GitHub Actions · k6 |
| [**Entregador Demo**](https://github.com/Porzelt/entregador-demo) · [demo ao vivo](https://porzelt.github.io/entregador-demo-web/) | Protótipo de app de entregador (online/offline, pedidos, aceitar e recusar, status da entrega, histórico). Dados simulados, camadas separadas e 13 testes unitários | React Native · Expo · TypeScript · Jest |
| [**Novo Testamento Sem Anúncios**](https://github.com/Porzelt/nt-sem-anuncios) | App Android offline, sem anúncios e sem nenhuma permissão de rede, em teste fechado na Google Play | React Native · Expo · TypeScript · SQLite |
| **MPA — Método Porzelt de Aprendizado** · [case](cases/mpa.md) | App de estudos para concursos com simulados por assinatura | React Native · Google Play Billing · Cloudflare Workers/R2/KV |
| **NutriParceiro** · [case](cases/nutriparceiro.md) | SaaS para nutricionistas: IA lê exames por imagem e gera planos alimentares | Laravel 13 · Sanctum · React Native · API da Anthropic |
| [**Nutri Hellen**](https://github.com/Porzelt/Nutri-Hellen-Site) | Site com agendamento de consultas, [em produção](https://nutrihellenfatima.com.br) | Laravel 12 · Livewire · Tailwind v4 · Docker · Coolify |

### 🛠️ Stack

- **Backend:** PHP 8 · Laravel · Livewire · Inertia · APIs REST · filas/Horizon
- **Frontend:** Vue 3 · React · Angular · TypeScript · Tailwind
- **Mobile:** React Native · Expo · publicação na Google Play
- **Dados:** MySQL · MariaDB · PostgreSQL · SQLite · Redis · SQL avançado
- **DevOps:** Docker · GitHub Actions · Linux · Nginx · Cloudflare Workers
- **IA:** Claude Code com múltiplos agentes · integração com LLMs em produto

### 📫 Contato
[LinkedIn](https://linkedin.com/in/henriqueporzelt) · henrique.porzeltneto@gmail.com · disponível para PJ ou CLT, remoto
