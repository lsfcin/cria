# cria — Roadmap
> Pending work only. Plano canônico do lado código; cronograma de pesquisa no twin: `academy/papers/2027-CHI-cria/ROADMAP.md`.

## Status

Fundação (2026-07-07, Fable): workflow v0 especificado, nenhum código. Ativo: M1.

## Backlog

- anti-gaming do score: paráfrase distante ≠ ideia nova — rubrica humana na fase de atrito; explorar detecção automática
- decisão: score de fronteira visível ou oculto durante fase 1 (afeta gaming e motivação)
- integração dobra: corpus entre coortes com context folding (memória de longo prazo)
- integração /loops: ideia sobrevivente vira feature request do craft flow
- integração motor do instituto (`branches/instituto/MOTOR.md` + `core/flows/mechanism-search.md`): cria = estágios 2-4 do motor em versão controlada/medida; compartilhar corpus de precedentes (estágio 0) e formato de candidato
- plataforma multi-user estilo Polis (contribuir+reagir, sem reply) — SÓ se evidência do piloto justificar (decisão C2 do paper)
- técnicas de foresight (Institute for the Future, Jane McGonigal) + design especulativo como motores/lentes de ideação
- **cluster de temas de pesquisa** (INBOX 2026-07-24) — teoria dos jogos, design de mecanismos, modelos de democracia, votação digital, tecnologias e incentivos, crowdsourcing e gamification. É o substrato conceitual do cria (ideação como mechanism design) e atravessa também a disciplina de inteligência híbrida, o [[lih-dd]], o ai4good e possíveis papers. Usar como lente de operadores/personas e como fonte de crises-piloto; cruzar com o motor do instituto.

---

## M1 — Dry-run harness 🔲 PENDING

### Problem
Validar formato, scores e prompts dos agentes ANTES da turma (ago/2026). Sem harness, o piloto vira debug ao vivo. Constraint: modelo de embedding precisa ser congelado no pré-registro OSF — escolha aqui trava o experimento.

### Solution
Tudo file-based (padrão craft, `core/flows/craft/craft.md`). Um ciclo = diretório `.cria/<ciclo>/` com uma ideia por arquivo md + frontmatter (`author: humano|agente/<operador>`, `phase`, `parent` pra cruzamentos, `ts`). Scorer CLI em Python: embeda ideia nova, calcula distância mínima ao corpus (score de fronteira), diversidade do corpus (mean pairwise cosine + Vendi), emite CSV. Corpus: `corpus.jsonl` + `embeddings.npy`. Agentes-motor: prompts md em `agents/` (1 por operador × persona), rodados via Claude Code/API — sem framework.

### Checklist
- [ ] escolher modelo de embedding multilíngue (candidatos: `paraphrase-multilingual-mpnet-base-v2`, `bge-m3`; critério: PT-BR + reprodutível local) — documentar em SPECS.md
- [ ] definir formato `.cria/` (template de ideia md + frontmatter) — exemplos no SPECS.md
- [ ] `tools/scorer.py`: frontier score + diversidade (pairwise, Vendi) + CSV
- [ ] prompts dos 5 agentes-motor + cartógrafo + cético em `agents/`
- [ ] rodar 1 ciclo solo (Lucas único humano) na crise feiras agroeco — dossiê pronto no paper outputs/CRISES.md
- [ ] post-mortem do dry-run → ajustar SPECS.md + sections/03_cria.tex (via SPECS § Twin)

### Key Files
- `SPECS.md` — spec das fases/papéis/operadores (fonte da verdade) + § Twin (deveres cruzados)
- `academy/papers/2027-CHI-cria/outputs/CRISES.md` — dossiê feiras (fase 0 pronta)
- `academy/papers/2027-CHI-cria/outputs/experiment-design.md` — métricas que o scorer deve produzir

## M2 — Operação turma 🔲 PENDING

### Problem
20-40 alunos sem git fluente precisam contribuir ideias/votos com telemetria íntegra.

### Solution
Ingestão via Google Forms → `core/tools/drive` → conversor pra `.cria/` (ou repo com template de PR, se a turma aguentar). Log de seleção/votos/kill-tests em CSVs por time. Export anonimizado pro paper (`outputs/` do twin).

### Checklist
- [ ] conversor forms→`.cria/`
- [ ] telemetria: votos, relatórios de minoria, pré-registros de kill-test
- [ ] export anonimizado (regras do CEP)

## M3 — Réplica eletiva + decisão plataforma 🔲 PENDING

Depende dos dados do piloto (C1/C2 do paper ROADMAP). Critério de build: fricção documentada do file-based > custo de manutenção de uma UI.
