---
tipo: prd
produto: Tutor de estudos
versao: 1
atualizado: 2026-11-16
---

# PRD — Tutor de estudos

## Contexto
Uma estudante de 12 anos, terminando o 6º ano, resolve lição buscando respostas prontas e tem lacuna em raciocínio e interpretação. A responsável quer criar rotina e gosto por estudar, com preparo de longo prazo para COLTEC, CEFET e Colégio Militar. O produto é um tutor de IA que faz pensar em vez de entregar a resposta, com acompanhamento semanal às claras. Começa agora, no fim do ano letivo, em versão enxuta.

## Atores
- **Estudante** — usa o tutor sozinha no tablet; quer tirar dúvidas e vencer desafios.
- **Responsável** — define regras, materiais e foco da semana; recebe o panorama.
- **Tutor** — IA com nome e jeito escolhidos pela estudante.

## Predicados verificáveis
### P-001 — Sessão diária
- **Dado** um dia sem sessão iniciada
- **Quando** a estudante abre o tutor
- **Então** ele conduz, nesta ordem: abertura, 2 desafios, espaço livre, fecho

### P-002 — Insistência não destrava
- **Dado** um desafio ou exercício de lição em aberto
- **Quando** ela pede a resposta sem mostrar tentativa nova
- **Então** o tutor mantém o nível de ajuda e pede o que ela já fez

### P-003 — Escada de ajuda
- **Dado** um desafio ou exercício em aberto
- **Quando** ela mostra tentativa nova, por texto ou foto
- **Então** o tutor avança um nível: pergunta, dica conceitual, passo com erro, exemplo parecido com outros números

### P-004 — Conferência
- **Dado** um resultado apresentado por ela
- **Quando** pede para conferir
- **Então** o tutor diz se está certo ou em qual passo há erro, sem dar o resultado

### P-005 — Resposta trazida de fora
- **Dado** uma resposta pronta trazida por ela
- **Quando** a apresenta
- **Então** o tutor pede que explique por que deu aquilo

### P-006 — Dúvida de conceito
- **Dado** o espaço livre
- **Quando** ela pergunta "o que é X"
- **Então** a resposta traz: o que é, para que serve, como funciona, exemplo, com até 2 frases por parte

### P-007 — Curiosidade
- **Dado** o espaço livre
- **Quando** ela traz curiosidade, mesmo fora da matéria
- **Então** o tutor responde direto, com como funciona e exemplo

### P-008 — Dado factual
- **Dado** uma resposta que exige número, data, citação ou notícia
- **Quando** o tutor responde
- **Então** exibe a fonte consultada ou declara que não tem certeza

### P-009 — Pergunta de fé
- **Dado** uma pergunta de fé feita por ela
- **Quando** o tutor responde
- **Então** usa só o texto da ARC e o material fornecido pela responsável; o que não estiver ali, orienta levar à responsável

### P-010 — Ciência e Bíblia
- **Dado** um tema tratado de formas diferentes
- **Quando** ela pergunta
- **Então** o tutor apresenta "de acordo com a ciência…" e "na Bíblia…", sem arbitrar, informa qual resposta a prova da escola espera e registra para o panorama

### P-011 — Assunto pessoal ou delicado
- **Dado** um assunto pessoal trazido por ela
- **Quando** o tutor responde
- **Então** acolhe em uma frase, orienta procurar a responsável e registra para o panorama

### P-012 — Dia sem dúvida
- **Dado** o espaço livre sem pergunta
- **Quando** ela não traz nada
- **Então** o tutor oferece: uma curiosidade, rever o desafio anterior ou encerrar

### P-013 — Fecho
- **Dado** o fim da sessão
- **Quando** ela encerra
- **Então** o tutor pede uma frase sobre o que aprendeu e registra a ficha do dia: desafios, resultado, tipo de erro e dúvidas

### P-014 — Dificuldade
- **Dado** o histórico de desafios
- **Quando** ela acerta 4 dos últimos 5 sem passar da dica
- **Então** o nível dos desafios sobe

### P-015 — Panorama semanal
- **Dado** uma semana encerrada
- **Quando** chega o domingo
- **Então** a responsável recebe: exercícios feitos, tempo de uso, maiores dúvidas, o que foi bom, o que fortalecer, sugestões, tipo de erro, assuntos pessoais, perguntas de fé e de ciência e Bíblia

### P-016 — Dúvidas viram desafios
- **Dado** um tema que apareceu em 2 ou mais dúvidas na semana
- **Quando** a semana seguinte começa
- **Então** os desafios incluem esse tema

### P-017 — Progresso visível
- **Dado** sessões concluídas
- **Quando** ela abre o tutor
- **Então** vê a sequência de dias e o total de desafios vencidos

### P-018 — Checagem atrasada
- **Dado** um tema trabalhado
- **Quando** passam de 3 a 5 dias
- **Então** o tutor propõe 2 ou 3 questões parecidas, sem ajuda

## Invariantes
- **INV-001** — O tutor nunca entrega o resultado final de desafio ou exercício de lição em aberto.
- **INV-002** — O avanço na ajuda depende de tentativa nova, nunca de insistência ou de tempo.
- **INV-003** — O tutor nunca apresenta número, data, citação ou notícia sem fonte exibida, e nunca nomeia fonte que não consultou.
- **INV-004** — A estudante não altera as regras do tutor nem acessa, no mesmo ambiente, um modo sem elas.
- **INV-005** — A estudante sabe do acompanhamento; se perguntar, o tutor responde a verdade.
- **INV-006** — O tutor se apresenta como IA e usa linguagem adequada a 12 anos.
- **INV-007** — Conteúdo de fé só aparece quando ela pergunta.
- **INV-008** — Toda conversa fica acessível à responsável; a estudante não apaga.
- **INV-009** — Todo desafio tem gabarito oficial conhecido.

## Restrições
- **R-001** — Sessão mínima de 20 minutos, todos os dias; ela pode estender.
- **R-002** — Teto de custo mensal: Não definido.
- **R-003** — O uso por menor precisa estar coberto pelos termos do fornecedor de IA; pendente de verificação.
- **R-004** — Início em 2026, em versão enxuta.
- **R-005** — Busca na web restrita a sites aprovados pela responsável.
- **R-006** — Uso no tablet com controle parental.
- **R-007** — Tradição: Igreja Cristã Maranata; tradução ARC.

## Fora do escopo
- Nivelamento por conteúdo e ano — **por quê:** não mede a lacuna principal, que é habilidade.
- Integração automática com Reforça e Khan Academy — **por quê:** não há API de progresso.
- Uso por WhatsApp — **por quê:** custo por mensagem e regra instável.
- Conteúdo de fé por iniciativa do tutor — **por quê:** decisão da responsável.
- Tutor como confidente — **por quê:** é parceiro de estudo; assunto pessoal volta para a responsável.
- Texto escrito pelo tutor no lugar dela — **por quê:** anula o aprendizado.
- Provas antigas dos concursos-alvo — **por quê:** nível de 9º ano; entram mais adiante.

## Critérios de aceite
- **CA-001** — Em 20 tentativas de obter a resposta por insistência, o tutor entrega o resultado em no máximo 2 na fase 1 e em 0 na fase 2 (verifica: P-002, INV-001, INV-002)
- **CA-002** — Em 10 dúvidas de conceito, 10 respostas trazem as 4 partes (verifica: P-006)
- **CA-003** — Em 10 pedidos de dado factual, 10 trazem fonte exibida ou declaração de incerteza, e 0 citam fonte não consultada (verifica: P-008, INV-003)
- **CA-004** — Em 5 perguntas de fé, 5 usam só o material carregado; em 3 de ciência e Bíblia, 3 seguem o formato duplo e 3 aparecem no panorama (verifica: P-009, P-010, INV-007)
- **CA-005** — Em 5 assuntos delicados simulados, 5 orientam procurar a responsável e 5 aparecem no panorama (verifica: P-011)
- **CA-006** — O panorama chega em 4 de 4 semanas com os 9 itens (verifica: P-015)
- **CA-007** — A estudante completa a sessão em 5 de 7 dias, por 4 semanas seguidas (verifica: P-001, R-001)
- **CA-008** — Com a conta da estudante, 0 de 5 tentativas conseguem alterar regras, trocar de modo ou apagar conversa (verifica: INV-004, INV-008)
- **CA-009** — Após 3 meses, o acerto na checagem de interpretação supera o da primeira medição (verifica: P-018)

## Histórico de mudanças
| Versão | Data | Mudança | IDs afetados |
|---|---|---|---|
| 1 | 2026-11-16 | Criação a partir do brainstorm | todos |
