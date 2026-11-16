---
tipo: spec
feature: tutor-fase-1
status: aprovada
prd_refs: [P-001, P-002, P-003, P-004, P-005, P-006, P-007, P-008, P-009, P-010, P-011, P-012, P-013, P-015, INV-001, INV-002, INV-003, INV-004, INV-005, INV-006, INV-007, INV-008, INV-009, CA-001, CA-002, CA-003, CA-004, CA-005, CA-006, CA-007, CA-008]
adrs: []
criado: 2026-11-16
entregue_em: null
---

# Spec — tutor-fase-1

## Contexto
O PRD pede um tutor que conduz a sessão diária (P-001), ajuda por escada sem entregar resultado (P-002 a P-005, INV-001, INV-002), responde dúvidas e curiosidades com formato e fonte (P-006 a P-008), trata fé e assuntos delicados por regra (P-009 a P-011) e gera panorama semanal (P-015). Hoje o repositório contém só o PRD (fonte: docs/prd.md). Tudo o que esta spec descreve é *novo*.

## Escopo
### Dentro
- Serviço de chat self-hosted com duas contas.
- Um tutor único, com instruções travadas.
- Bases de documentos e busca na web restrita.
- Preparação do tablet.
- Panorama semanal feito à mão no domingo.

### Fora — com porquê
- Escada controlada por código (P-002 em nível 0 de 20) — fase 2; a fase 1 valida adesão primeiro.
- Progresso visível (P-017) e checagem atrasada (P-018) — fase 2; dependem de estado guardado fora da conversa.
- Panorama automático — fase 2; o ritual manual serve à adesão.
- Subida automática de dificuldade (P-014) e dúvidas virando desafios (P-016) — na fase 1 a responsável decide pelo panorama.

## Design
### Componentes afetados
- Serviço de chat self-hosted: Open WebUI — *novo*
- Publicação por túnel com login — *novo*
- Provedor de modelo por API: Não definido; sai do teste comparativo — *novo*
- Base "Desafios": provas e soluções da OBMEP nível 1 — *novo*
- Base "Bíblia": texto da ARC e material da igreja fornecido pela responsável — *novo*
- Busca na web com lista de sites aprovados — *novo*
- `tutor/instrucoes.md`: instruções do tutor, versionadas — *novo*
- `tutor/casos-de-teste.md`: bateria de aceite — *novo*
- `panorama/roteiro.md`: roteiro do panorama de domingo — *novo*
- Tablet: ícone do tutor e regras do controle parental — *novo*

### Fluxo
1. A estudante abre o tutor e inicia a conversa do dia.
2. O tutor apresenta 2 desafios da base, ela resolve no caderno e envia foto.
3. O tutor segue a escada até ela chegar ao resultado ou ao exemplo parecido.
4. Espaço livre: o tutor classifica o pedido e responde pela regra do tipo.
5. Fecho: frase dela e ficha do dia escrita na própria conversa.
6. Domingo: a responsável abre as conversas da semana, roda o roteiro e conversa com a estudante.

### Contratos e interfaces
**Instruções do tutor** (`tutor/instrucoes.md`), em blocos:
1. Identidade: nome escolhido por ela, é uma IA, linguagem para 12 anos.
2. Ritual da sessão.
3. Escada e proibição de entregar resultado.
4. Tipos de pedido: conceito, lição, resposta de fora, curiosidade, pessoal.
5. Formato de resposta de conceito.
6. Dados só com fonte recuperada; "não sei" é válido.
7. Fé: sob demanda, só da base Bíblia, formato ciência e Bíblia.
8. Assunto delicado: acolher, devolver à responsável, registrar.
9. Transparência sobre o acompanhamento.
10. Ficha do dia.

**Ficha do dia**, campos: data; desafios (identificação, resultado, nível de ajuda atingido); tipo de erro (enunciado, conteúdo ou conta); dúvidas do espaço livre; ocorrências de fé, ciência e Bíblia ou assunto pessoal; frase dela.

**Panorama**, 9 itens na ordem do P-015, começando por "o que foi bom".

**Casos de teste** (`tutor/casos-de-teste.md`):

| Bateria | Quantidade | Verifica |
|---|---|---|
| Insistir pela resposta sem tentativa | 20 | CA-001 |
| Dúvida de conceito | 10 | CA-002 |
| Pedido de dado factual | 10 | CA-003 |
| Pergunta de fé | 5 | CA-004 |
| Tema de ciência e Bíblia | 3 | CA-004 |
| Assunto delicado simulado | 5 | CA-005 |
| Conta da estudante tentando burlar | 5 | CA-008 |

### Modelo de dados
Sem modelo próprio. As conversas ficam no armazenamento do serviço de chat; a ficha do dia é texto dentro da conversa.

### Migração e compatibilidade
Não se aplica; é a primeira versão. A fase 2 acrescenta código ao mesmo serviço, sem a estudante trocar de ferramenta.

## Decisões
### ADRs vinculados
Nenhum ainda.

### Decisões locais
- Uma conversa por dia.
- Panorama aos domingos.
- Instruções e casos de teste versionados no repositório.

## Riscos e rollback
- A escada cede só com prompt: aceito até 2 em 20 (CA-001); acima disso, antecipar a fase 2.
- Termos da API não cobrirem menor (R-003): verificar antes de contratar; plano B é app pronto com tablet restrito.
- Leitura errada da letra na foto: o teste comparativo usa fotos reais dela.
- Custo acima do esperado: teto e alerta no provedor; R-002 ainda sem valor.
- Rollback: desligar o serviço e remover o ícone do tablet; nenhum dado dela fica fora do servidor da responsável além do que passou pela API.

## Como verificar
- CA-001 a CA-005 e CA-008: rodar as baterias de `tutor/casos-de-teste.md` com a responsável no papel da estudante, registrando o resultado no próprio arquivo.
- CA-006: 4 panoramas de domingo com os 9 itens.
- CA-007: contagem de dias com sessão nas 4 primeiras semanas, pelas conversas.

## Histórico de mudanças
| Data | Mudança | Seções alteradas | Origem |
|---|---|---|---|
| 2026-11-16 | Criação | todas | PRD v1 |
