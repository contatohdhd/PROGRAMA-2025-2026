# PROGRAMA 2025-2026 · Gestão de Projetos (PMI)

Repositório de trabalho do programa **2025-2026**. Reúne a planilha de gestão de projetos (abordagem PMI preditiva, da abertura ao encerramento) e o fluxo de preenchimento **por área**, em que as informações chegam em Markdown e são registradas na planilha com um assistente (Claude).

> A planilha é *PMI-alinhada*, não um formulário oficial do PMI.

---

## Sumário

1. [Estrutura do repositório](#estrutura-do-repositório)
2. [Como a planilha funciona](#como-a-planilha-funciona)
3. [Mapa das áreas e status do preenchimento](#mapa-das-áreas-e-status-do-preenchimento)
4. [Workflow de preenchimento](#workflow-de-preenchimento)
5. [Regras de registro](#regras-de-registro)
6. [Convenções de formato](#convenções-de-formato)
7. [Limites conhecidos da planilha](#limites-conhecidos-da-planilha)

---

## Estrutura do repositório

```
.
├── README.md                                  ← este arquivo (guia + status)
├── planilha/
│   └── Workbook_Gestao_Projetos_PMI.xlsx      ← planilha mestre (fonte única de dados)
├── areas/                                     ← modelos MD, um por área de preenchimento
│   ├── 01_identificacao.md
│   ├── …
│   └── 16_aceite-e-encerramento.md
└── entradas/                                  ← MDs recebidos, arquivados após o registro
    └── AAAA-MM-DD_NN_<area>.md
```

| Pasta | Função |
|---|---|
| `planilha/` | Contém a única versão válida da planilha. O histórico do Git é o controle de versões — não há cópias `_v2`, `_final` etc. |
| `areas/` | Modelos prontos para preencher: cada um lista os campos, as dicas da planilha, os valores permitidos e o formato esperado. |
| `entradas/` | Trilha de auditoria: o MD original que você enviou fica guardado aqui, para qualquer valor da planilha ser rastreável até a sua fonte. |

---

## Como a planilha funciona

São **16 abas**. Uma só recebe dados; as outras 15 são documentos gerados por fórmula.

- **`00_ENTRADAS` — única aba de entrada.** Células **cinzas** são de preenchimento; células brancas com fórmula são automáticas (não digitar nelas).
- **`01_PAINEL` a `15_ENCERRAMENTO` — documentos vinculados.** Leem tudo de `00_ENTRADAS`. **Nunca se edita nessas abas.**

| Aba | Documento | Aba | Documento |
|---|---|---|---|
| `01_PAINEL` | Painel do projeto (indicadores) | `09_RESPOSTAS` | Respostas aos riscos |
| `02_ABERTURA` | Termo de abertura (Project Charter) | `10_ORCAMENTO` | Orçamento e controle de custos |
| `03_ESCOPO` | Declaração de escopo | `11_QUALIDADE` | Plano de qualidade |
| `04_EAP` | Estrutura analítica (WBS) | `12_COMUNICACAO` | Plano de comunicação |
| `05_RACI` | Matriz de responsabilidades | `13_MUDANCAS` | Controle de mudanças |
| `06_INTERESSADOS` | Registro de partes interessadas | `14_CONTROLE` | Monitoramento e controle |
| `07_GANTT` | Cronograma Gantt (eixo mensal de 12 meses) | `15_ENCERRAMENTO` | Encerramento e aceite |
| `08_RISCOS` | Registro e avaliação de riscos | | |

**Campos calculados automaticamente** (não preencher): `Fim` da atividade (início + duração − 1), `Exposição` do risco (probabilidade × impacto), `Total previsto` e `Desvio` do orçamento, `Desvio %` do monitoramento.

**Identificadores.** Os IDs já vêm impressos na planilha e são a chave de rastreabilidade entre as áreas:

| Prefixo | Significado | Prefixo | Significado |
|---|---|---|---|
| `F01`–`F61` | Campos únicos (identificação, termo, escopo, planos, encerramento) | `OR` | Itens de orçamento |
| `PR` | Premissas e restrições | `QU` | Requisitos de qualidade |
| `ST` | Partes interessadas | `CO` | Itens de comunicação |
| `EA` | EAP e atividades | `MU` | Solicitações de mudança |
| `RA` | Linhas da matriz RACI | `MO` | Monitoramento |
| `RI` | Riscos | `IS` | Problemas |

---

## Mapa das áreas e status do preenchimento

O preenchimento segue 16 áreas, na ordem abaixo (respeita as dependências entre elas). Cada linha aponta para o modelo MD da área, as células de destino em `00_ENTRADAS` e as abas que passam a refletir o que for registrado.

Legenda de status: ⬜ não iniciada · 🟨 parcial · ✅ registrada e conferida

| # | Área (modelo MD) | Células em `00_ENTRADAS` | IDs | Abas que refletem | Status |
|---|---|---|---|---|---|
| 01 | [Identificação](areas/01_identificacao.md) | `D10:D23` | F01–F14 | `01_PAINEL`, `02_ABERTURA`, `03_ESCOPO`, `07_GANTT`, `15_ENCERRAMENTO` | ⬜ |
| 02 | [Termo de abertura](areas/02_termo-de-abertura.md) | `D25:D39` | F15–F29 | `02_ABERTURA`, `03_ESCOPO`, `15_ENCERRAMENTO` | ⬜ |
| 03 | [Escopo e requisitos](areas/03_escopo-e-requisitos.md) | `D41:D51` | F30–F40 | `03_ESCOPO` | ⬜ |
| 04 | [Planos e governança](areas/04_planos-e-governanca.md) | `D53:D63` | F41–F51 | `11_QUALIDADE`, `12_COMUNICACAO`, `13_MUDANCAS`, `14_CONTROLE` | ⬜ |
| 05 | [Premissas e restrições](areas/05_premissas-e-restricoes.md) | `A77:H86` | PR01–PR10 | `03_ESCOPO` | ⬜ |
| 06 | [Partes interessadas](areas/06_partes-interessadas.md) | `A90:L101` | ST01–ST12 | `06_INTERESSADOS` | ⬜ |
| 07 | [EAP e atividades](areas/07_eap-e-atividades.md) | `A105:O128` | EA01–EA24 | `01_PAINEL`, `04_EAP`, `07_GANTT` | ⬜ |
| 08 | [Matriz de responsabilidades (RACI)](areas/08_raci.md) | `A132:I147` | RA01–RA16 | `05_RACI` | ⬜ |
| 09 | [Registro de riscos](areas/09_riscos.md) | `A151:O168` | RI01–RI18 | `01_PAINEL`, `08_RISCOS`, `09_RESPOSTAS` | ⬜ |
| 10 | [Orçamento e custos](areas/10_orcamento.md) | `A172:K183` | OR01–OR12 | `01_PAINEL`, `10_ORCAMENTO` | ⬜ |
| 11 | [Qualidade e aceite](areas/11_qualidade.md) | `A187:K198` | QU01–QU12 | `11_QUALIDADE` | ⬜ |
| 12 | [Comunicação](areas/12_comunicacao.md) | `A202:J213` | CO01–CO12 | `12_COMUNICACAO` | ⬜ |
| 13 | [Solicitações de mudança](areas/13_mudancas.md) | `A217:K228` | MU01–MU12 | `01_PAINEL`, `13_MUDANCAS` | ⬜ |
| 14 | [Monitoramento e desempenho](areas/14_monitoramento.md) | `A232:L247` | MO01–MO16 | `14_CONTROLE` | ⬜ |
| 15 | [Registro de problemas](areas/15_problemas.md) | `A251:I262` | IS01–IS12 | `14_CONTROLE` | ⬜ |
| 16 | [Aceite e encerramento](areas/16_aceite-e-encerramento.md) | `D65:D74` | F52–F61 | `15_ENCERRAMENTO` | ⬜ |

### Fases e dependências

| Fase | Áreas | Observação |
|---|---|---|
| **Planejamento** | 01 a 12 | 01 → 02 → 03 → 04 formam a base. A área 07 (EAP) é pré-requisito de 08, 10, 11 e 14, que apontam para IDs `EA`. A área 06 é pré-requisito de 08 e 12. |
| **Execução e controle** | 13, 14, 15 | Preenchidas e atualizadas durante o projeto. |
| **Encerramento** | 16 | Só ao final do projeto. |

Áreas 05 e 15 não têm pré-requisito e podem ser feitas a qualquer momento.

---

## Workflow de preenchimento

O ciclo se repete **uma área por vez**:

```
 você                                        assistente (Claude)
  │                                                │
  ├─ 1. escolhe a área (ou aceita a próxima) ─────▶│
  ├─ 2. envia as informações em MD ───────────────▶│
  │                                                ├─ 3. valida: pré-requisitos, listas, formatos, IDs
  │◀──────── 4. devolve dúvidas e pendências ──────┤      (não inventa dado; pergunta)
  ├─ 5. responde / confirma ─────────────────────▶│
  │                                                ├─ 6. arquiva o MD em entradas/
  │                                                ├─ 7. registra em 00_ENTRADAS (só células de entrada)
  │                                                ├─ 8. recalcula e confere as abas vinculadas
  │◀──────── 9. relatório: o que foi gravado ──────┤
  │                                                └─ 10. commit + push direto em main; atualiza o status
```

**Como enviar.** Use o modelo da área em [`areas/`](areas) ou mande texto livre em MD — o assistente faz o mapeamento para os IDs. Campos únicos (áreas 01–04 e 16) usam um bloco por ID (`### F15 · …`); áreas em tabela (05–15) usam uma tabela MD com uma linha por registro.

**Publicação.** Cada área registrada vira um commit em `main`, sem PR. A mensagem do commit identifica a área e os IDs gravados. O histórico do Git é o registro de quem mudou o quê e quando.

---

## Regras de registro

O assistente segue estas regras em todo registro:

1. **Só grava em `00_ENTRADAS`**, nas células de entrada (cinzas). Fórmulas e abas `01`–`15` não são tocadas.
2. **Não inventa dado.** O que não foi informado fica em branco — a planilha aceita campos vazios até a aprovação. Dúvida vira pergunta, não suposição.
3. **Respeita as listas de validação.** Valor fora da lista não é gravado; o assistente devolve as opções permitidas (ver [Convenções](#convenções-de-formato)).
4. **Não sobrescreve sem avisar.** Se a célula já tem valor diferente do novo, o assistente mostra o antes e o depois e confirma antes de substituir.
5. **Confere a integridade entre áreas.** IDs `EA` citados em RACI, orçamento, qualidade e monitoramento precisam existir na área 07; públicos de comunicação precisam existir na área 06.
6. **Confere depois de gravar.** A planilha é recalculada e as abas vinculadas são verificadas (sem erros de fórmula, totais coerentes). O relatório informa o que foi gravado, o que ficou em branco e o que exige decisão.
7. **Preserva o arquivo.** Formatação, mesclagens, listas e fórmulas permanecem como no original.

---

## Convenções de formato

| Tipo | Como informar | Exemplo |
|---|---|---|
| Data | `DD/MM/AAAA` | `15/03/2025` |
| Percentual | Com `%` | `40%` |
| Valor em reais | Número, ponto ou vírgula decimal, sem símbolo | `12500,00` |
| Probabilidade / impacto | Inteiro de 1 a 5 | `4` |
| Duração | Dias corridos (inteiro) | `30` |
| IDs de ligação | Exatamente como na planilha | `EA07` |

**Listas de valores permitidos** (validadas pela planilha):

| Campo | Valores |
|---|---|
| Status geral (`F08`) | Planejamento · Em execução · Suspenso · Encerrado |
| Prioridade (`F09`) | Alta · Média · Baixa |
| Abordagem (`F10`) | Preditiva · Híbrida · Adaptativa |
| Situação do aceite (`F54`) | Pendente · Aprovado · Reprovado |
| Premissas — Tipo | Premissa · Restrição · Dependência |
| Premissas — Status | Não validada · Validada · Revisar |
| Partes — Influência | Alta · Média · Baixa |
| Partes — Interesse | Alto · Médio · Baixo |
| EAP — Tipo | Entrega · Atividade · Marco |
| EAP — Status | Não iniciado · Em andamento · Concluído · Bloqueado · Cancelado |
| Riscos — Estratégia | Evitar · Mitigar · Transferir · Aceitar · Explorar · Melhorar · Compartilhar |
| Riscos — Status | Aberto · Monitorando · Mitigado · Encerrado |
| Qualidade — Status | Pendente · Em avaliação · Aprovado · Reprovado |
| Comunicação — Status | Previsto · Enviado · Atrasado · Cancelado |
| Mudanças — Decisão | Pendente · Aprovada · Rejeitada |
| Mudanças — Status | Aberta · Em análise · Implementada · Encerrada |
| Monitoramento — Status | No prazo · Atenção · Atrasado · Concluído |
| Problemas — Status | Aberto · Em tratamento · Resolvido · Encerrado |

---

## Limites conhecidos da planilha

Pontos do arquivo original que afetam o preenchimento e que convém conhecer desde já:

| # | Limite | Efeito | Encaminhamento |
|---|---|---|---|
| 1 | **Gantt de 12 meses.** O eixo de `07_GANTT` começa no mês de `F11` (Início previsto) e cobre só 12 meses. | Atividades após o 12º mês não aparecem como quadrados no Gantt, embora existam nas demais abas. | Se o programa passar de 12 meses, decidir entre estender o eixo ou dividir por ciclos. |
| 2 | **Capacidade fixa de linhas** por tabela (ex.: 24 atividades, 18 riscos, 12 itens de custo). | Registros além do limite não cabem. | O assistente avisa antes de gravar; estender a planilha exige ajustar também a aba vinculada. |
| 3 | **Papéis do RACI fixos.** Os cabeçalhos "Papel 1–4" são texto fixo em `00_ENTRADAS` e em `05_RACI`. | Os nomes dos papéis não se propagam sozinhos. | Ao registrar a área 08, o assistente propõe os nomes e os altera nas duas abas, com a sua confirmação. |
| 4 | **Interesse × Influência com gênero diferente** (Alto/Médio/Baixo × Alta/Média/Baixa). | Erro comum de digitação. | O assistente normaliza para a lista correta de cada coluna. |
| 5 | **Sem proteção de aba.** | Fórmulas podem ser sobrescritas por engano se a planilha for editada à mão. | Preferir o fluxo por MD; edições manuais devem ser feitas só nas células cinzas. |
