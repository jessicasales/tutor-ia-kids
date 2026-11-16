---
adr_number: 001
title: Chat self-hosted em vez de app pronto
status: aceito
created: 2026-11-16
supersedes: null
superseded_by: null
specs: [tutor-fase-1]
---

# ADR 001 — Chat self-hosted em vez de app pronto

## Contexto
O tutor precisa de regras que a estudante não contorne, conversas visíveis à responsável e espaço para crescer. A estudante já busca respostas prontas quando pode.

## Alternativas consideradas
- **App de IA pronto com instruções fixas** — o modo sem regras fica no mesmo app, o controle parental não mostra conversas e o panorama automático não é possível.
- **Conta da responsável no dispositivo da estudante** — termos restritos a maiores de 18 e exposição das conversas e conexões da responsável.
- **Aplicação construída do zero** — semanas de trabalho antes de a estudante testar.

## Decisão
Adotamos um serviço de chat self-hosted, com modelo acessado por API.

## Consequências
### Positivas
Um ambiente só dela, regras travadas, conversas à vista, evolução sem troca de ferramenta.
### Negativas
A responsável mantém o serviço e paga a API por uso; o uso por menor depende dos termos do provedor.
### Neutras
A escolha do provedor fica para o teste comparativo.
