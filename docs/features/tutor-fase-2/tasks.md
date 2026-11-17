---
tipo: tasks
spec: tutor-fase-2
atualizado: 2026-11-16
---

# Tasks — tutor-fase-2

| ID | Task | Spec (seção) | Depende de | Status | Critério de pronto |
|---|---|---|---|---|---|
| T-01 | Confirmar o mecanismo de filtro do serviço de chat e o local de armazenamento | Componentes afetados; Modelo de dados | — | pendente | Premissa do filtro confirmada ou corrigida na Spec; local de armazenamento definido na Spec |
| T-02 | Criar as estruturas de dados | Modelo de dados | T-01 | pendente | As 6 estruturas existem e aceitam um registro de teste cada |
| T-03 | Escrever os textos de instrução por degrau | Contratos e interfaces | — | pendente | 4 textos (degraus 0 a 3) no repositório, cada um reafirmando que o resultado não é entregue |
| T-04 | Implementar o classificador de mensagem | Contratos e interfaces | T-01 | pendente | Em 40 mensagens rotuladas à mão, acerta ao menos 36; erro ou dúvida devolve `insistencia` |
| T-05 | Implementar o filtro da escada | Fluxo | T-02, T-03, T-04 | pendente | Degrau sobe só em `tentativa_nova`; bateria 1 dá 0 falhas em 20 (CA-001) |
| T-06 | Gravar o registro estruturado no fecho | Fluxo; Modelo de dados | T-05 | pendente | Uma sessão de teste gera sessao, tentativa_exercicio, duvida e ocorrencia corretas |
| T-07 | Mostrar o progresso na abertura | Contratos e interfaces | T-06 | pendente | Sequência e total exibidos batem com os registros em 3 sessões de teste |
| T-08 | Implementar a checagem atrasada | Contratos e interfaces | T-06 | pendente | Tema trabalhado gera checagem de 3 a 5 dias depois, sem escada, com resultado registrado |
| T-09 | Implementar a rotina semanal do panorama | Fluxo; Contratos e interfaces | T-06 | pendente | Panorama com os 9 itens chega à responsável no domingo; falha gera alerta |
| T-10 | Implementar a proposta do plano da semana | Contratos e interfaces | T-06 | pendente | Proposta com 2 desafios por dia aplica a regra de dificuldade e a de dúvidas repetidas |
| T-11 | Atualizar `tutor/instrucoes.md` e `panorama/roteiro.md` | Componentes afetados | T-05, T-09 | pendente | Bloco 3 e bloco 10 ajustados; roteiro marcado como contingência |
| T-12 | Rodar todas as baterias com o filtro ligado | Como verificar | T-05, T-11 | pendente | CA-001 0 de 20; demais baterias com as metas da fase 1 |
| T-13 | Acompanhar 4 semanas e a medição de 3 meses | Como verificar | T-08, T-09, T-12 | pendente | CA-006: 4 de 4 panoramas automáticos; CA-009: comparação registrada |

## Notas
- 2026-11-16 — Tasks geradas com a Spec ainda em `rascunho`. Só começam depois de a Spec ser aprovada e de a fase 1 atingir a condição de entrada descrita no Contexto da Spec.
