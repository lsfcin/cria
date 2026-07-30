# cria — Specs (workflow v0, spec canônica)

> Geração de ideias híbrida humano-IA com mechanism design: diversidade coletiva como payoff, grounding por kill-test, propósito = reverter lógicas de crise. Sem UI: file-based, como o craft flow (`core/flows/craft/craft.md`). Espelho acadêmico: `academy/papers/2027-CHI-cria/sections/03_cria.tex` (sync obrigatório — ver § Twin abaixo).

## Metas de design

- **D1** diversidade coletiva é objetivo explícito (score), não efeito colateral esperado
- **D2** grounding: toda ideia carrega kill-test pré-registrado (≤90 dias, custo ~0)
- **D3** propósito: ideação aponta pra crise documentada (dossiê em `academy/papers/2027-CHI-cria/outputs/CRISES.md`)
- **D4** incentivo auto-sustentável: mover-se no jogo tem que valer a pena individualmente (lição Waze/PB Porto Alegre)

## Papéis

| Papel | Quem | Faz |
|-------|------|-----|
| curador | professor/pesquisador | mantém dossiês, arbitra filtro de viabilidade, pré-registra métricas |
| time | 3-4 alunos | contribui, cruza, seleciona, executa kill-test, **fica dono** da ideia sobrevivente |
| agente-motor | LLM (1 por operador × persona) | aplica seu operador ao dossiê; punido por cair em território ocupado |
| agente-cartógrafo | LLM + embeddings | mantém o mapa semântico do corpus, calcula scores de fronteira |
| agente-cético | LLM | escreve o kill-test mais barato que derruba cada ideia finalista |

## Motores de criatividade (operadores)

| operador | movimento | linhagem |
|----------|-----------|----------|
| combinar | fundir dois mecanismos de domínios sem relação | Boden, blending |
| inverter | reverter papel, fluxo ou incentivo do mecanismo da crise | SCAMPER |
| reescalar | encolher/ampliar a intervenção em 2 ordens de magnitude | SCAMPER |
| transplantar | importar mecanismo que funciona em outro domínio | analogia |
| colher (waze) | redirecionar comportamento individual existente (inclusive o vicioso) pra benefício coletivo | mechanism design |

## Fases (1 ciclo)

```
fase 0  chão      dossiê da crise (CRISES.md) — sem dossiê, não roda
fase 1  diverge   agentes-motor geram N ideias cada; cartógrafo score por
                  território novo (distância ao corpus); ocupado = 0 ponto
fase 2  atrito    humanos leem, roubam, cruzam, mutam, adicionam;
                  contribuições humanas entram no mesmo score
fase 3  converge  filtro de viabilidade (rubrica + cético + curador arbitra)
                  → seleção por desejabilidade (votação do coletivo)
                  → relatório de minoria: descartada com 1 defensor volta na fase 1 seguinte
fase 4  faro      cada finalista ganha kill-test pré-registrado do cético,
                  revisado pelo time; executa na janela de micro-execução
fase 5  posse     sobreviveu → vira projeto do time (mentoria) ou capitaneado
                  pelo curador; tudo (vivo/morto) persiste no corpus com
                  embedding + resultado → próxima turma herda o mapa
```

## Ciclos no semestre

```
semana  1-2   fase 0 (dossiê coletivo da crise 1)
semana  3-4   fases 1-3 (ciclo A: diverge/atrito/converge)
semana  5     fase 4 desenho dos kill-tests
semana  6-9   micro-execução (kill-tests rodando) — aulas seguem com conteúdo
semana 10     medição + pivot: morto = post-mortem no corpus; vivo = continua;
              pivotado = reentra fase 1 do ciclo B
semana 11-14  ciclo B (crise 2 ou pivots) — mesmo ritmo comprimido
semana 15-16  colheita: projetos donos definidos, corpus consolidado
```

Dois ciclos completos de **ideação → execução → ajuste/pivot** por semestre. O pivot não é fracasso: ideia pivotada reentra a fase 1 com o post-mortem como insumo (a crise vira combustível também no meta-nível).

## Instrumentação (tudo é dado do experimento)

- toda ideia: autor (humano/agente/misto), operador, timestamp, embedding, score de fronteira
- toda seleção: votos, relatório de minoria
- todo kill-test: pré-registro, resultado, decisão (continua/pivota/mata)
- formato: arquivos versionados (`.cria/` — definição no M1 do [ROADMAP.md](ROADMAP.md)), sem UI — formulário + git

## Aberto (decidir no dry-run M1)

- modelo de embedding (congelar antes da coleta) e função exata do score de fronteira
- como punir "diversidade superficial" (parafrasear longe ≠ ideia nova) — rubrica humana no atrito
- peso relativo score-fronteira vs. sobrevivência na nota de contribuição
- anti-gaming: score visível ou oculto durante a fase 1?

## Twin — cross-duties

> Was `BRIDGE.md`, folded here 2026-07-30. Padrão dobra: código e paper são gêmeos, e o que cada
> lado deve ao outro é invariante — não um tipo `.md` separado (`core/SCHEMA.md` § The four
> disposal routes). Twin de pesquisa: `academy/papers/2027-CHI-cria`.

### Código deve ao paper

- Todo número reportável nasce aqui com proveniência: runs em `runs/` (quando existirem), métricas
  em CSV → copiados pra `academy/papers/2027-CHI-cria/outputs/` com script, nunca à mão
- Mudança nas fases/operadores/score acima → sincronizar `sections/03_cria.tex` na mesma sessão
- Modelo de embedding e função de score: congelados após o pré-registro OSF — mudança vira emenda
  documentada nos dois lados

### Paper deve ao código

- Decisões de desenho do experimento (métricas, exclusões) chegam como item no `ROADMAP.md` daqui
  antes de virar seção
- Achados de literatura com consequência de implementação (ex.: anti-gaming, personas) → item no
  Backlog daqui com link pro ref yaml

### Sessões

- Sessão de código: ler `CONTEXT.md` + `ROADMAP.md` Status daqui; não editar o paper além do sync
  do `03_cria.tex`
- Sessão de paper: protocolo no `CONTEXT.md` do twin; não editar código além de copiar outputs
