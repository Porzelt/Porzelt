# Case: NutriParceiro — IA aplicada ao atendimento nutricional

> SaaS B2B com fins comerciais. O código é privado; este case mostra o problema, a arquitetura e as decisões técnicas.

## O problema
Em cada consulta, nutricionistas gastam horas transcrevendo exames laboratoriais e bioimpedância, calculando necessidades energéticas e montando planos alimentares à mão. Essas horas saem do tempo de atendimento.

## A solução
Um app que funciona como o "braço operacional" da profissional. Ele não substitui a decisão clínica, mas faz o trabalho mecânico:
- **Questionário clínico guiado** (wizard com validação por etapa e máscaras de entrada)
- **Upload de exames e bioimpedância por foto**, com armazenamento privado
- **IA com visão computacional** que lê os exames e gera um rascunho de plano alimentar
- **Plano editável pela nutricionista** (com salvamento automático), histórico por paciente e texto pronto para enviar no WhatsApp

## Arquitetura

```
App mobile (React Native + Expo)            API (Laravel 13 + Sanctum)
 ├── auth por token (secure-store)  ──►      ├── pacientes, anamnese, exames, planos
 ├── wizard de anamnese                      ├── storage privado (S3/R2)
 ├── câmera/galeria → upload                 ├── fila assíncrona → job de geração do plano
 └── plano editável                          │      └── driver de IA (Anthropic, visão) | mock
                                             ├── quota freemium por plano de assinatura
                                             └── MySQL/MariaDB · Docker · Coolify
```

## Decisões técnicas de destaque
- **A chave de IA vive só no backend.** O app nunca fala direto com o LLM.
- **Driver de IA trocável** (`real` ou `mock`): desenvolvimento e testes sem custo, e o modelo pode ser trocado sem tocar no domínio.
- **Geração em fila assíncrona**, com estados distintos para carregar e para gerar, porque a IA pode levar segundos.
- **Modelo de negócio no código:** quotas por tier configuráveis por mapa e um endpoint de consumo exibido no app.
- **Controle de custo de IA:** limites de upload, quantidade de exames por geração e prompts que forçam a entrega do plano completo.
- **Decisões registradas em ADRs**; deploy com Dockerfile de produção e Coolify.
- Atenção a **LGPD e às normas do conselho profissional** (dados de saúde, papel da IA, conflito de interesse).

## Stack
Laravel 13 · PHP 8.3 · Sanctum · filas · PHPUnit · MySQL 8/MariaDB · Docker · React Native · Expo SDK 57 · TypeScript · API da Anthropic (visão e geração) · Cloudflare R2/S3 · Coolify

[← voltar ao perfil](https://github.com/Porzelt)
