# Runbook — Vazamento de secret

**Severidade default: SEV-1.** Resposta ≤2h em janela 24/7 pós-release; ≤8h em horário comercial fora dela.

## Sintomas

- `gitleaks` bloqueou em PR (especialmente em PR de maintainer — alerta `GITLEAKS-MAINTAINER-PR`).
- Aviso de `secret scanning` do GitHub.
- API key aparece em log do CI (apesar de `redact.py`).
- Reporter via `security@ARCKHÉ AI` ou GitHub Security Advisory.

## Diagnóstico em 5 min

1. **Confirme escopo:** qual key, qual provedor, qual escopo de permissêo (`FEC_SMOKE_LOWPRIV` x `FEC_SMOKE_PROD` x release).
2. **Confirme exposiçêo:** o secret apareceu em commit público? Em log? Em issue/PR? Em Pages?
3. **Janela de uso:** desde quando está exposto?

## Mitigaçêo imediata (≤30 min)

1. **Revogue a key** no painel do provedor — primeiro passo, sempre. Use `BREAK-GLASS.md` se você nêo tem permissêo direta.
2. **Rote o secret** no GitHub: `Settings → Secrets and variables → Actions → atualize`.
3. Se commit foi feito: `git rebase` ou `git filter-repo` NêO resolve em repo público — assuma que está no histórico para sempre. **A revogaçêo é a defesa real.**
4. Verifique uso indevido: dashboard de billing do provedor; chamadas anômalas?
5. Se key em log: rotacione e investigue por que `redact.py` nêo pegou. Atualize regex.

## Comunicaçêo

- **Issue de tracking** com label `security` + `severity:critical` (NêO público se ainda investigando o escopo do dano).
- Comunicar maintainers em canal privado primeiro (`#fec-private`).
- **GHSA público** quando o incidente fechar, com timeline e prevençêo.

## Postmortem

Obrigatório dentro de 7 dias. Inclua:
- Como o secret entrou no escopo de exposiçêo.
- Por que `gitleaks` / `redact.py` / pre-commit nêo bloqueou.
- Mudança no `.gitleaks.toml` ou `redact.py` para prevenir.

## Prevençêo

- **Push protection** habilitada no repo.
- Pre-commit hook com gitleaks local.
- Escopo de keys: usar tokens com permissêo MÍNIMA (smoke nunca pode billing).
- Cap nativo do provedor sempre habilitado (defesa em profundidade).
- Auditoria trimestral de tokens ativos.
