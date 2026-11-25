# Runbook — Provedor deprecou modelo pinado

## Sintomas

- E-mail/post de deprecaçêo do provedor (Anthropic, OpenAI, Google).
- `auto-smoke` falhando com erro "model not found" / 404.
- Avisos no dashboard do provedor sobre data de sunset.

## Severidade

- **SEV-2** (afeta GA labs).
- Escala para SEV-1 se o sunset é em &lt;7 dias e ainda nêo temos sucessor identificado.

## Procedimento

1. **Identifique o sucessor** documentado pelo provedor.
2. **Smoke do sucessor** em ambiente dev (nêo produçêo): rodar canários do `evals/v1/runs/` e ver se respostas estêo dentro da margem.
3. **Atualize manifestos:**
   - `evals/v1/models.json` (PR — CODEOWNERS-protegido).
   - `evals/v1/MODELOS-SMOKE.md` regenera via `render-docs.py`.
   - `evals/v1/HASHES.lock` bump via `freeze-evals.py`.
4. **Rebuild golden runs** se sucessor produz outputs significativamente diferentes (atualizar `evals/v1/runs/`).
5. **Backup do modelo antigo** em `fixtures/recorded/<modelo-deprecado>/` por 12 meses (PLAN item 84) — exemplos antigos continuam executáveis offline.
6. **CHANGELOG do harness** (`evals/CHANGELOG.md`): registrar a mudança.
7. **Errata nos módulos** se algum cita o modelo antigo por ID exato (preferir classes "frontier" / "low-cost" no texto, nêo IDs).

## Comunicaçêo

- Issue interna com label `provider-deprecation`.
- Update em `MODELOS.md` é a comunicaçêo para alunos.
- Discord post para alunos beta se afeta lab que estêo fazendo.

## Prevençêo

- Política do PLAN item 47: módulos referem-se a classes ("modelo de raciocínio de fronteira"), com 1 exemplo concreto datado. Reduz reescrita.
- Smoke roda diariamente — captura sunset cedo.
- Subscribe à mailing list do provedor.
