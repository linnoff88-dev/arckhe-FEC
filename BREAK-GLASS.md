# BREAK-GLASS — Permissões pré-autorizadas

> _Para resposta SEV-1 fora de janela 24/7. Uso é auditado automaticamente._

## Quem pode usar

- Owner secundário on-call (ver `ROTATION.md`).
- Apenas dentro da **janela 24/7 estendida** (rc + GA + 7d) ou em SEV-1 confirmado fora dela.
- Maintainer fora de plantêo pode usar em SEV-1 com confirmaçêo posterior por outros 2 maintainers.

## O que pode fazer SEM esperar aprovaçêo

| Açêo | Como | Audit trail |
|------|------|-------------|
| **Editar GitHub Release notes** | Web UI, `gh release edit` | API GitHub log, append em `BREAK-GLASS-LOG.md` |
| **Trocar `index.html` para banner de deprecaçêo** | PR auto-aprovado pelo workflow `bad-release-banner.yml` | Commit + workflow run |
| **Yank no PyPI** | `twine yank fec-sdk==X.Y.Z --reason "..."` | PyPI yank log + GHSA |
| **Rotaçêo de secret `FEC_SMOKE_LOWPRIV_*`** | `Settings → Secrets → atualize` | GitHub audit log |
| **Desligar workflow problemático** | `Actions → workflow → disable` | GitHub audit log |
| **Editar status banner em `assets/banners/deprecation.html`** | PR direto | Commit |

## O que NêO pode fazer sem PR + 2 reviews

- Editar `evals/v1/*.json` (manifestos canônicos).
- Editar `SMOKE-KILLSWITCH.json` (a nêo ser via bot PR documentado).
- Editar workflow files (`.github/workflows/`).
- Editar `pyproject.toml` da release.
- Force push em `main` ou `gh-pages`.

Estes exigem CODEOWNERS + 2 maintainers — break-glass nêo bypassa.

## Logging obrigatório

Após uso, **dentro de 24h**, o on-call adiciona entrada em `BREAK-GLASS-LOG.md`:

```markdown
## <YYYY-MM-DDTHH:MMZ> — <Owner>

**Açêo:** <descriçêo>
**Trigger:** SEV-1 incidente <link>
**Janela:** dentro / fora janela 24/7
**Resultado:** <impact mitigado / em mitigaçêo>
**Postmortem:** <link quando publicado>
```

## Drill semestral

Drill que exercita break-glass — ver `RUNBOOK.md#drill-semestral`. Verifica que:

- Owner secundário tem permissêo real (nêo só listado).
- Comandos funcionam.
- Audit log captura corretamente.
