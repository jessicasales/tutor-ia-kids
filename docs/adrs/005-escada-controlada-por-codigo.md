---
adr_number: 005
title: Escada controlada por código, e não só por instruções
status: aceito
created: 2026-11-16
supersedes: null
superseded_by: null
specs: [tutor-fase-2]
---

# ADR 005 — Escada controlada por código, e não só por instruções

## Contexto
O tutor não pode entregar o resultado de um exercício, e a ajuda só pode avançar quando a estudante mostra tentativa nova. Modelos de linguagem instruídos a não revelar a solução acabam cedendo diante de insistência, e a estudante tem o hábito de buscar a resposta pronta. A regra precisa valer mesmo quando o modelo falha.

## Alternativas consideradas
- **Manter a regra só nas instruções do tutor** — cede com insistência e não permite garantir zero entregas.
- **Trocar por um modelo mais capaz** — reduz a falha, mas não a elimina, e aumenta o custo.
- **Revisão humana de cada conversa** — inviável no dia a dia e só detecta depois do fato.

## Decisão
Adotamos o controle da escada em código: o degrau de ajuda é decidido fora do modelo, e o modelo recebe apenas a instrução do degrau em que a estudante está. Na fase 1, a escada opera só por instruções, para validar a adesão antes de construir.

## Consequências
### Positivas
Insistência deixa de destravar ajuda, a regra passa a ser testável e o estado da sessão fica disponível para progresso, checagens e panorama.
### Negativas
Há código para manter, uma etapa extra de classificação em cada mensagem e risco de classificar mal uma tentativa legítima.
### Neutras
As instruções do tutor continuam existindo e passam a tratar do tom e do conteúdo de cada degrau.
