# Case: plataforma de gestão operacional — Polícia Militar do Estado de São Paulo

> Sistema governamental confidencial. Não há código, nomes internos, endereços nem dados neste documento: apenas o problema, o que construí e os resultados.
> Para ver os mesmos padrões em código aberto, veja o projeto de vitrine fixado no perfil.

## Contexto
Plataforma web usada por unidades de todo o estado para planejar e acompanhar operações (eleições, operações sazonais, escalas de serviço, férias, efetivo). Equipe de 2 desenvolvedores; atuo desde 2023, com mais de 160 commits próprios em uma base de quase 900.

**Stack:** Laravel 12 · PHP 8.5 · Inertia.js + Vue 3 · Tailwind · MariaDB 11 · Redis/Valkey + Laravel Horizon · Docker/Sail · GitHub Actions

## O que construí

### Migração do legado
Remake de um sistema em PHP puro para a stack **VILT** (Vue, Inertia, Laravel, Tailwind): SPA guiada pelo servidor, componentes Vue reutilizáveis e permissões por perfil e módulo.

### Capacidade comprovada com teste de carga
Antes do período de maior uso (inscrição de efetivo em locais de votação), conduzi um **teste de carga com k6** em homologação:

| Métrica | Resultado |
|---|---|
| Usuários simultâneos | **450** |
| Requisições | **29.018**, com **0,00% de erro** |
| Registros gravados | 99,97%, conferidos no banco |
| Diagnóstico | gargalo de **CPU** (load average acima do número de núcleos), sem pressão de memória nem de rede |

A partir das métricas (p95, throughput, load), escrevi o **plano de otimização de performance** e o comunicado técnico à diretoria de TI.

### CI/CD
Pipeline com **GitHub Actions e runners self-hosted**: o merge em cada branch (desenvolvimento → homologação → produção) dispara um deploy com modo manutenção, migrations, build de assets, cache de configuração e restart das filas.

### Integrações e resiliência
- Autenticação corporativa via **LDAP**, substituindo a integração SOAP anterior
- Cliente do WebService de RH com **failover entre 7 nós**
- Acesso a banco legado **Sybase via FreeTDS** (imagem Docker customizada)
- **Monitor de disponibilidade** do sistema de RH: checagens agendadas, linha do tempo, alertas por e-mail e runbook de contingência

### Módulos de negócio
- Distribuição de vagas por **sorteio em dois passes**, com listas temporária e definitiva
- Escalas de serviço, plano de férias, painéis gerenciais com drill-down (comando → batalhão → companhia)
- **Leitura automatizada de boletins em PDF** cruzada com o efetivo
- **Mapa com 14 camadas geográficas** (MapLibre GL + PMTiles), com funcionamento offline
- Exportações em PDF e Excel e **jobs em fila** com barra de progresso (Horizon)
- **Backup e restore automatizados**, auditoria com retenção e isolamento de dados por unidade

### Forma de trabalhar
Documentação por microssistema, runbooks e uso intensivo de **Claude Code com múltiplos agentes**: demandas que levariam meses saem em dias, com revisão por pull request.

[← voltar ao perfil](https://github.com/Porzelt)
