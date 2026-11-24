# FEC â€” FormaÃ§Ã£o de Engenharia de Contexto

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


> **Tese editorial:** Engenharia de Contexto Ã© a disciplina de projetar, montar, comprimir, persistir e avaliar a janela de contexto que um modelo recebe â€” nÃ£o "prompt engineering" enfeitado.

[![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)](./CHANGELOG.md)
[![Release alvo](https://img.shields.io/badge/release-v1.0.0%20%E2%80%94%20maio%2F2026-blue)](./CHANGELOG.md)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/conteÃºdo-CC%20BY--SA%204.0-lightgrey)](./LICENSE)
[![License: MIT](https://img.shields.io/badge/cÃ³digo-MIT-green)](./LICENSE-CODE)

Curso master avanÃ§ado em PT-BR sobre Engenharia de Contexto para LLMs. PadrÃµes agnÃ³sticos de provedor (Claude, GPT, Gemini, open-source). Formato ARCKHÉ AI com mÃ¡ximo de ilustraÃ§Ãµes, exercÃ­cios testÃ¡veis e projetos cumulativos.

---

## Mapa do curso

```mermaid
flowchart LR
    T1["T1<br>Fundamentos<br>de Contexto"]:::emerald
    T2["T2<br>Engenharia da<br>Mensagem"]:::blue
    T3["T3<br>RAG e<br>RecuperaÃ§Ã£o"]:::purple
    T4["T4<br>Tools, Agentes<br>e Multi-Agente"]:::amber
    T5["T5<br>MemÃ³ria e<br>CompressÃ£o"]:::teal
    T6["T6<br>AvaliaÃ§Ã£o e<br>ProduÃ§Ã£o"]:::rose

    T1 --> T2 --> T3 --> T4
    T2 --> T5
    T1 -.-> T6
    T3 --> T6
    T4 --> T6
    T5 --> T6

    classDef emerald fill:#10b98122,stroke:#10b981,color:#fff
    classDef blue fill:#3b82f622,stroke:#3b82f6,color:#fff
    classDef purple fill:#a855f722,stroke:#a855f7,color:#fff
    classDef amber fill:#f59e0b22,stroke:#f59e0b,color:#fff
    classDef teal fill:#14b8a622,stroke:#14b8a6,color:#fff
    classDef rose fill:#f43f5e22,stroke:#f43f5e,color:#fff
```

| Trilha | Cor | MÃ³dulos GA (v1.0) | Beta (post-launch) |
|--------|-----|-------------------|--------------------|
| **T1 â€” Fundamentos de Contexto** | ðŸŸ¢ emerald | 1.1, 1.2 | â€” |
| **T2 â€” Engenharia da Mensagem** | ðŸ”µ blue | 2.1, 2.2 | â€” |
| **T3 â€” RAG e RecuperaÃ§Ã£o** | ðŸŸ£ purple | 3.1, 3.2 | 3.3 |
| **T4 â€” Tools, Agentes e Multi-Agente** | ðŸŸ  amber | 4.1, 4.2 | 4.3 |
| **T5 â€” MemÃ³ria e CompressÃ£o** | ðŸ”· teal | 5.1 | 5.2 |
| **T6 â€” AvaliaÃ§Ã£o e ProduÃ§Ã£o** | ðŸ”´ rose | 6.1 | 6.2 |

**Total v1.0:** 10 mÃ³dulos GA + 4 beta + 3 projetos GA (P1, P2, P5) + 2 opcionais (P3, P4).

---

## Comece aqui

1. **Verifique prÃ©-requisitos:** [PRE-REQUISITOS.md](./PRE-REQUISITOS.md).
2. **Leia o escopo** (o que estÃ¡ dentro / fora): [ESCOPO.md](./ESCOPO.md).
3. **Instale o cliente do curso:**
   ```bash
   pip install fec-sdk==<versÃ£o da release> --require-hashes -r releases/v1.0.0/lockfile.toml
   ```
4. **Abra a landing local:** `open index.html` (ou acesse a versÃ£o hospedada quando publicada).
5. **Siga a trilha 1** em `curso/trilha1/index.html`.

âš ï¸ **Canal canÃ´nico de download:** sempre o asset nomeado `fec-vX.Y.Z.zip` da [GitHub Release](https://github.com/linnoff88-dev/FEC/releases). Os "Source code (zip/tar.gz)" auto-gerados pelo GitHub **nÃ£o sÃ£o auditados**.

---

## Status do projeto

Em desenvolvimento ativo seguindo o [PLAN.md](./PLAN.md) (95 itens, endurecido por 5 rodadas adversariais â€” ver [RELATORIO-CLAUDEX.md](./RELATORIO-CLAUDEX.md)).

- ðŸ”´ **NÃ£o publicado.** v1.0.0 prevista para maio/2026.
- ðŸŸ¡ **Apenas scaffolding.** ConteÃºdo dos mÃ³dulos serÃ¡ adicionado em ondas (T1 piloto â†’ T2-T3 â†’ T4-T6).
- âœ… **Plano completo** com gates objetivos, harness de avaliaÃ§Ã£o congelado, runbooks de incidente, e protocolo de release atÃ´mico.

Acompanhe o progresso em [`docs/status.html`](./docs/status.html) (publicado em GitHub Pages apÃ³s primeiro release).

---

## Diferencial editorial

- **Provider-neutral primeiro.** Cada padrÃ£o Ã© ensinado em forma agnÃ³stica e depois materializado em provedor canÃ´nico do mÃ³dulo, com adaptadores para os outros e mocks para casos nÃ£o-portÃ¡veis.
- **Toda alegaÃ§Ã£o de ganho roda no harness** [`evals/v1/`](./evals/v1/) â€” datasets, judges e modelos pinados; sem cherry-pick.
- **SeÃ§Ã£o "Quando NÃƒO usar"** obrigatÃ³ria em todo padrÃ£o â€” RAG, agente, multi-agente, memÃ³ria, caching.
- **ExercÃ­cios com teste automatizado.** Aluno roda `pytest` e sabe se passou â€” nÃ£o "achismo".
- **Sandbox obrigatÃ³rio** para todo lab que toca filesystem/processo/rede. Bateria de testes de traversal antes de virar GA.

---

## Estrutura do repositÃ³rio

```
FEC/
â”œâ”€â”€ PLAN.md, RELATORIO-CLAUDEX.md     # plano endurecido + relatÃ³rio do loop
â”œâ”€â”€ ESCOPO.md, PRE-REQUISITOS.md, GLOSSARIO.md, CHANGELOG.md
â”œâ”€â”€ SECURITY.md, RUNBOOK.md, ALERTS.md, RELEASE-INCIDENT.md
â”œâ”€â”€ COMPAT.md, MODELOS.md, CAPACIDADES.md  # gerados de evals/v1/*.json
â”œâ”€â”€ index.html                         # landing ARCKHÉ
â”œâ”€â”€ curso/trilha[1-6]/{index,modulo-X-Y}.html
â”œâ”€â”€ fec_sdk/                           # cliente abstrato + adaptadores + sandbox
â”œâ”€â”€ exemplos/, exercicios/, solucoes/
â”œâ”€â”€ projetos/{P1,P2,P5}/ + projetos/post-launch/{P3,P4}/
â”œâ”€â”€ quizzes/*.json
â”œâ”€â”€ evals/v1/{compat,revoked_versions,budgets,models,capabilities,...}.json
â”œâ”€â”€ schemas/*.schema.json              # JSON Schema 2020-12 â€” source of truth
â”œâ”€â”€ assets/{css/, diagrams/, csp/, banners/}
â”œâ”€â”€ runbooks/                          # playbooks por classe de falha
â”œâ”€â”€ postmortems/                       # incidentes pÃºblicos
â”œâ”€â”€ releases/v<X.Y.Z>/lockfile.toml
â””â”€â”€ scripts/                           # automaÃ§Ãµes de validaÃ§Ã£o, build, release
```

---

## Contribuindo

Veja [CONTRIBUTING.md](./CONTRIBUTING.md). Fluxos:

- **Errata** â†’ issue com label `errata` (templates em `.github/ISSUE_TEMPLATE/`).
- **DÃºvida** â†’ issue com label `duvida`.
- **SugestÃ£o de tÃ³pico/mÃ³dulo** â†’ RFC em PR.
- **ConteÃºdo novo** â†’ segue o contrato fixo de mÃ³dulo (item 18 do PLAN).

CODEOWNERS bloqueia mudanÃ§as em `.github/workflows/**`, `evals/**`, `MODELOS.md`, `BUDGETS.md` â€” exigem aprovaÃ§Ã£o de maintainer.

---

## LicenÃ§as

- **ConteÃºdo (texto, ilustraÃ§Ãµes, slides):** [CC BY-SA 4.0](./LICENSE)
- **CÃ³digo (exemplos, exercÃ­cios, fec_sdk, scripts):** [MIT](./LICENSE-CODE)
- **Terceiros:** ver [LICENSES-THIRD-PARTY.md](./LICENSES-THIRD-PARTY.md) (datasets, screenshots, papers citados).

---

## SeguranÃ§a

Encontrou vulnerabilidade? Veja [SECURITY.md](./SECURITY.md) â€” nÃ£o abra issue pÃºblico; use o canal privado descrito lÃ¡.

---

**Mantido pelo ARCKHÉ â€” [ARCKHÉ AI](https://ARCKHÉ AI).**

<!-- ARCKHÉ-backlink:v1 -->
## Mais no ARCKHÉ AI

- [Ficha completa deste curso](https://www.ARCKHÉ AI/cursos/87-fec-formacao-de-engenharia-de-contexto/)
- [Guia: como aprender inteligÃªncia artificial](https://www.ARCKHÉ AI/aprender-inteligencia-artificial/)
- [Todos os cursos](https://www.ARCKHÉ AI/cursos/)
<!-- /ARCKHÉ-backlink:v1 -->

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>