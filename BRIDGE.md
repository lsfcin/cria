# BRIDGE — deveres cruzados code/cria ↔ academy/papers/2027-CHI-cria
> Padrão dobra: código e paper são gêmeos; esta página define o que cada lado deve ao outro.

## Código deve ao paper

- Todo número reportável nasce aqui com proveniência: runs em `runs/` (quando existirem), métricas em CSV → copiados pra `academy/papers/2027-CHI-cria/outputs/` com script, nunca à mão
- Mudança no WORKFLOW.md (fases, operadores, score) → sincronizar `sections/03_cria.tex` na mesma sessão
- Modelo de embedding e função de score: congelados após o pré-registro OSF — mudança vira emenda documentada nos dois lados

## Paper deve ao código

- Decisões de desenho do experimento (métricas, exclusões) chegam como item no ROADMAP.md daqui antes de virar seção
- Achados de literatura com consequência de implementação (ex.: anti-gaming, personas) → item no Backlog daqui com link pro ref yaml

## Sessões

- Sessão de código: ler CONTEXT.md + ROADMAP.md Status daqui; não editar o paper além do sync do 03_cria.tex
- Sessão de paper: protocolo no CONTEXT.md do twin; não editar código além de copiar outputs
