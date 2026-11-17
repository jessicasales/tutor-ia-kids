---
tipo: spec
feature: tutor-fase-2
status: rascunho
prd_refs: [P-002, P-003, P-013, P-014, P-015, P-016, P-017, P-018, INV-001, INV-002, CA-001, CA-006, CA-009]
adrs: [005]
criado: 2026-11-16
entregue_em: null
---

# Spec — tutor-fase-2

## Contexto
O PRD exige que insistência nunca destrave ajuda (P-002, INV-002), que o resultado nunca seja entregue (INV-001, CA-001 em 0 de 20), que a dificuldade suba por regra (P-014), que dúvidas virem desafios (P-016), que a estudante veja seu progresso (P-017), que haja checagem atrasada (P-018, CA-009) e que o panorama chegue toda semana (P-015, CA-006).

Hoje a escada, a ficha do dia e a escolha dos desafios dependem só das instruções do tutor (fonte: tutor/instrucoes.md), o panorama é feito à mão (fonte: panorama/roteiro.md) e os desafios do dia vêm de um plano mantido pela responsável (fonte: docs/features/tutor-fase-1/spec.md). Não há código no repositório. Tudo o que esta spec descreve é *novo*.

Esta fase começa quando a fase 1 completar as 4 semanas de acompanhamento, ou antes disso se a bateria de insistência da fase 1 passar de 2 falhas em 20 *(premissa — confirme ou corrija)*.

## Escopo
### Dentro
- Escada de ajuda controlada por código.
- Registro estruturado de sessões, desafios, dúvidas e ocorrências.
- Panorama semanal gerado e enviado automaticamente.
- Progresso visível para a estudante.
- Checagem atrasada.
- Proposta automática do plano da semana seguinte, para a responsável aprovar.

### Fora — com porquê
- Nivelamento por conteúdo e ano — fora do escopo do PRD.
- Provas antigas dos concursos-alvo — fora do escopo do PRD nesta etapa.
- Troca do serviço de chat — o ADR 001 mantém o serviço da fase 1.
- Aprovação automática do plano da semana — a responsável segue decidindo o foco.
- Notificações para a estudante fora do tutor — não pedido no PRD.

## Design
### Componentes afetados
- `tutor/instrucoes.md` (fonte: tutor/instrucoes.md) — o bloco 3 deixa de decidir o degrau e passa a receber o degrau do código; o bloco 10 passa a espelhar o registro estruturado.
- `panorama/roteiro.md` (fonte: panorama/roteiro.md) — o passo a passo manual vira plano de contingência; o guia da conversa permanece.
- Documento "Plano da semana" (fonte: docs/features/tutor-fase-1/spec.md) — passa a ser proposto pelo sistema e aprovado pela responsável.
- Filtro da escada, executado pelo serviço de chat antes de cada mensagem chegar ao modelo *(premissa — confirme ou corrija: mecanismo de funções de filtro do Open WebUI)* — *novo*
- Classificador de mensagem — *novo*
- Armazenamento de estado e registros — *novo*
- Rotina semanal do panorama, com envio à responsável por Telegram *(premissa — confirme ou corrija)* — *novo*
- Rotina de proposta do plano da semana — *novo*

### Fluxo
1. A estudante envia uma mensagem.
2. O filtro identifica o exercício em aberto e chama o classificador.
3. O classificador devolve o tipo da mensagem: tentativa nova, insistência, pedido de conferência, dúvida de conceito ou outro.
4. O filtro atualiza o estado: o degrau sobe 1 apenas em "tentativa nova"; nos demais tipos, permanece.
5. O filtro acrescenta à mensagem a instrução do degrau atual, e o modelo responde dentro dela.
6. Na abertura da sessão, o filtro acrescenta a sequência de dias, o total de desafios vencidos e as checagens pendentes.
7. No fecho, o filtro grava o registro estruturado da sessão.
8. Aos domingos, a rotina lê os registros da semana, monta o panorama com os 9 itens e envia à responsável.
9. Em seguida, a rotina propõe o plano da semana seguinte, aplicando as regras de dificuldade e de dúvidas repetidas; a responsável aprova ou ajusta.

### Contratos e interfaces
**Tipos do classificador:** `tentativa_nova`, `insistencia`, `conferencia`, `conceito`, `outro`. Entrada: a mensagem atual, as tentativas anteriores do mesmo exercício e o enunciado. Em caso de erro ou dúvida do classificador, o tipo é `insistencia`, para que a falha nunca destrave ajuda.

**Estado por exercício:** identificação do desafio ou do exercício; degrau atual (0 a 3); número de tentativas; situação (em aberto, resolvido sozinha, resolvido com ajuda, não resolvido); tipo de erro.

**Instrução por degrau:** um texto fixo para cada degrau, derivado do bloco 3 das instruções. Em todos os degraus, o texto reafirma que o resultado não é entregue.

**Progresso na abertura:** sequência de dias com sessão e total de desafios vencidos.

**Checagem atrasada:** para cada tema trabalhado, 2 ou 3 questões do banco oficial sobre o mesmo tema, propostas de 3 a 5 dias depois, sem escada. O resultado entra no registro.

**Panorama:** os 9 itens do P-015, na ordem definida no roteiro, com "tempo de uso" calculado pelos horários das mensagens.

**Proposta do plano:** 2 desafios por dia para 7 dias; nível sobe quando há 4 acertos nos últimos 5 sem passar do degrau 1; tema com 2 ou mais dúvidas na semana entra no plano.

### Modelo de dados
Todas as estruturas são *novas*:
- **sessao** — data, início, fim, frase da estudante.
- **tentativa_exercicio** — sessão, identificação, degrau atingido, situação, tipo de erro, número de tentativas.
- **duvida** — sessão, tema, tipo de pedido.
- **ocorrencia** — sessão, categoria (fé, ciência e Bíblia, assunto pessoal), resumo de uma linha.
- **checagem** — tema, data prevista, data feita, acertos, total.
- **plano_semana** — semana, dia, desafios, situação (proposto, aprovado).

Local de armazenamento: Não definido.

### Migração e compatibilidade
- As fichas da fase 1, em texto dentro das conversas, não são convertidas *(premissa — confirme ou corrija)*; a sequência de dias e os totais começam a contar na ativação da fase 2.
- As instruções do tutor ganham nova versão; a anterior fica no histórico do repositório.
- O filtro pode ser desligado sem perda: o tutor volta a operar só com as instruções, como na fase 1.

## Decisões
### ADRs vinculados
- 005 — Escada controlada por código, e não só por instruções

### Decisões locais
- Falha do classificador é tratada como insistência.
- O plano da semana é proposto pelo sistema e aprovado pela responsável.
- O roteiro manual do panorama permanece como contingência.
- Checagem atrasada usa só questões do banco oficial (decorre do ADR 004).

## Riscos e rollback
- Classificador marca tentativa legítima como insistência e ela se frustra: acompanhar no panorama a taxa de mensagens classificadas como insistência; revisar exemplos toda semana no primeiro mês.
- Classificador marca insistência como tentativa nova: coberto pela bateria de 20 casos, que precisa dar 0 de 20.
- Rotina do panorama falha no domingo: alerta à responsável e uso do roteiro manual.
- Custo maior por causa da chamada extra do classificador: medir nas duas primeiras semanas; R-002 do PRD segue sem valor.
- Rollback: desligar o filtro e as rotinas; o tutor volta ao comportamento da fase 1 e nada do que a estudante usa muda de lugar.

## Como verificar
- CA-001: bateria 1 de `tutor/casos-de-teste.md` com o filtro ligado, 0 falhas em 20.
- CA-006: 4 panoramas automáticos seguidos, com os 9 itens, conferidos contra as conversas.
- CA-009: comparar o acerto das checagens do terceiro mês com o da primeira medição.
- P-014 e P-016: em 2 semanas de dados reais, a proposta do plano aplica as duas regras, conferido pela responsável.
- P-017: na abertura, a sequência e o total batem com os registros.
- P-018: toda checagem ocorre de 3 a 5 dias após o tema e sem ajuda.

## Histórico de mudanças
| Data | Mudança | Seções alteradas | Origem |
|---|---|---|---|
| 2026-11-16 | Criação | todas | PRD v1 |
