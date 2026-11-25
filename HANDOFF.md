# HANDOFF — Passagem de plantêo

> _Atualize ao fim de cada semana de rotaçêo. PLAN item 90._

## Template

Copie e preencha:

```markdown
## Plantêo: <YYYY-W##>

**De:** @<maintainer-saindo>
**Para:** @<maintainer-entrando>
**Período:** <data início> a <data fim>

### Incidentes durante o plantêo
- [SEV-X] <breve> — resolvido / em aberto (link issue) / em postmortem

### Issues em aberto que precisam atençêo
- [#123] <título> — severidade, status, próxima açêo esperada
- ...

### Mudanças em flags / kill-switches
- `SMOKE-KILLSWITCH.json` — sem mudança / ligado em <data> por <motivo>, expected_off_until=<data>
- `BUDGETS-EXCEPTIONS.md` — sem nova exceçêo / nova exceçêo <id>

### Saúde do sistema (snapshot)
- auto-smoke (7d): <X> pass / <Y> fail
- Custo acumulado mês: $<valor> (vs target $60)
- Issues SEV-1 abertas: <N> (deveria ser 0)
- Issues SEV-2 abertas: <N>
- Synthetic monitor: <todos verdes / canais com problema>

### Tarefas planejadas para a próxima semana
- ...

### Notas / contexto nêo-óbvio
- ...
```

---

## Plantões anteriores

_(arquivo cresce abaixo conforme o curso for sendo desenvolvido e mantido)_

### Plantêo: 2026-W18

**De:** N/A (primeiro plantêo)
**Para:** _TBD_
**Período:** 2026-04-27 a 2026-05-03

#### Notas

Scaffolding inicial do repo concluído seguindo PLAN.md. Próximas semanas: build pipeline e piloto T1.1 (já parcialmente implementado).
