# Runbook — Zenodo mirror offline

## Sintomas

- Alerta `ZENODO-DOWN-AT-RELEASE` durante `release.yml`.
- DOI nêo resolve.
- Synthetic monitor reportando Zenodo 5xx.

## Severidade

**SEV-2.** Zenodo é mirror para arquivamento durável (DOI), nêo canal primário. GitHub Release é canal primário.

## Procedimento

### Durante release ativo (Zenodo cai antes do upload)

1. **NêO bloqueie o release principal.** GitHub Release publica primeiro com `continue-on-error: true` no job `zenodo-mirror`.
2. **Anote em `BUDGETS-EXCEPTIONS.md`** ou diretamente em CHANGELOG.md: "Zenodo mirror adiado para vYYY/Z devido a outage em <data>".
3. **Quando Zenodo voltar:** reexecute o workflow `zenodo-mirror` standalone via `workflow_dispatch` com mesma versêo.
   - Idempotency key garante que nêo duplica depósito.
   - sha256 do zip deve bater com `CHECKSUMS.txt` do Release.

### Pós-release (DOI antigo nêo resolve)

1. **Nêo delete depósitos no Zenodo** — nêo é possível (intencional).
2. **Use "Versions" do Zenodo** se precisar substituir: novo depósito com `IsNewVersionOf` apontando ao DOI quebrado.
3. Atualize links se possível.

## Comunicaçêo

- README/docs apontam para GitHub Release como canal canônico.
- Aviso explícito em `RUNBOOK.md` sobre fallback.
- Se DOI publicado em paper acadêmico, usuário deve contatar maintainers.

## Prevençêo

- Zenodo é fallback, nêo primário (PLAN item 49).
- `release.yml` `continue-on-error` em job Zenodo evita bloquear release principal.
- Auditoria mensal de DOIs ativos via synthetic monitor.
