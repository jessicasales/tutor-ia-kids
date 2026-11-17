---
tipo: tasks
spec: tutor-fase-1
atualizado: 2026-11-16
---

# Tasks — tutor-fase-1

| ID | Task | Spec (seção) | Depende de | Status | Critério de pronto |
|---|---|---|---|---|---|
| T-01 | Ler os termos do provedor de API sobre uso por menor | Riscos e rollback | — | pendente | Resultado (cobre ou não cobre) registrado em Notas |
| T-02 | Combinar com a estudante o ritual, o acompanhamento e o nome do tutor | Contratos e interfaces | — | pendente | Nome do tutor registrado em `tutor/instrucoes.md` |
| T-03 | Subir o Open WebUI com túnel e login | Componentes afetados | T-01 | pendente | Acesso externo só entra com login |
| T-04 | Criar as contas de admin e de estudante com restrições | Componentes afetados | T-03 | pendente | Bateria "conta tentando burlar": 0 de 5 (CA-008) |
| T-05 | Comparar 2 modelos com 10 problemas reais e fotos do caderno | Componentes afetados | T-03 | pendente | Provedor escolhido e registrado na Spec |
| T-06 | Escrever `tutor/instrucoes.md` com os 10 blocos | Contratos e interfaces | T-02 | em andamento | Arquivo no repositório, aplicado e travado no serviço |
| T-07 | Carregar a base Desafios | Componentes afetados | T-03 | pendente | Tutor apresenta 2 desafios da base e recupera o gabarito |
| T-08 | Carregar a base Bíblia | Componentes afetados | T-03 | pendente | Pergunta de fé é respondida com texto da base |
| T-09 | Ligar a busca com a lista de sites aprovados | Componentes afetados | T-03 | pendente | Resposta com dado exibe fonte da lista; site fora da lista não aparece |
| T-10 | Escrever `tutor/casos-de-teste.md` e rodar as baterias | Como verificar | T-04, T-06, T-07, T-08, T-09 | em andamento | CA-001 até 2 de 20; CA-002 10 de 10; CA-003 10 de 10; CA-004 5 de 5 e 3 de 3; CA-005 5 de 5 |
| T-11 | Preparar o tablet: ícone e controle parental | Componentes afetados | T-04 | pendente | No horário de estudo só abrem tutor, Reforça e câmera |
| T-12 | Escrever `panorama/roteiro.md` | Contratos e interfaces | T-06 | em andamento | Roteiro produz os 9 itens a partir de uma semana de conversas |
| T-13 | Primeira semana com a estudante e primeiro panorama | Fluxo | T-10, T-11, T-12, T-15 | pendente | 1 panorama de domingo com os 9 itens |
| T-14 | Acompanhar as 4 primeiras semanas | Como verificar | T-13 | pendente | CA-006: 4 de 4 panoramas; CA-007: 5 de 7 dias por 4 semanas |
| T-15 | Criar o documento "Plano da semana" na base Desafios | Componentes afetados | T-07 | pendente | Plano com 2 desafios por dia para 7 dias; na abertura, o tutor apresenta os 2 da data de hoje |

## Notas
- 2026-11-16 — T-06, T-10 e T-12: rascunhos v0.1 gravados no repositório, aguardando revisão da responsável. T-06 ainda depende do nome do tutor (T-02) e de aplicar no serviço; T-10 ainda depende de rodar as baterias; T-12 ainda depende de testar com uma semana real de conversas.
- 2026-11-16 — Spec alterada em Componentes afetados e Fluxo (inclusão do "Plano da semana"). Criada a T-15; T-13 passou a depender dela. Conferidas sem impacto: T-03, T-04, T-05, T-08, T-09 e T-11 (componentes distintos do plano) e T-07 (a carga da base não muda; o plano é um documento à parte).
