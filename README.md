# FEC ê¢â¬â FormaêÂ§êÂ£o de Engenharia de Contexto

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


> **Tese editorial:** Engenharia de Contexto êÂ© a disciplina de projetar, montar, comprimir, persistir e avaliar a janela de contexto que um modelo recebe ê¢â¬â nêÂ£o "prompt engineering" enfeitado.

[![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)](./CHANGELOG.md)
[![Release alvo](https://img.shields.io/badge/release-v1.0.0%20%E2%80%94%20maio%2F2026-blue)](./CHANGELOG.md)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/conteêÂºdo-CC%20BY--SA%204.0-lightgrey)](./LICENSE)
[![License: MIT](https://img.shields.io/badge/cêÂ³digo-MIT-green)](./LICENSE-CODE)

Curso master avanêÂ§ado em PT-BR sobre Engenharia de Contexto para LLMs. PadrêÂµes agnêÂ³sticos de provedor (Claude, GPT, Gemini, open-source). Formato ARCKHê AI com mêÂ¡ximo de ilustraêÂ§êÂµes, exercêÂ­cios testêÂ¡veis e projetos cumulativos.

---

## Mapa do curso

```mermaid
flowchart LR
    T1["T1<br>Fundamentos<br>de Contexto"]:::emerald
    T2["T2<br>Engenharia da<br>Mensagem"]:::blue
    T3["T3<br>RAG e<br>RecuperaêÂ§êÂ£o"]:::purple
    T4["T4<br>Tools, Agentes<br>e Multi-Agente"]:::amber
    T5["T5<br>MemêÂ³ria e<br>CompressêÂ£o"]:::teal
    T6["T6<br>AvaliaêÂ§êÂ£o e<br>ProduêÂ§êÂ£o"]:::rose

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

| Trilha | Cor | MêÂ³dulos GA (v1.0) | Beta (post-launch) |
|--------|-----|-------------------|--------------------|
| **T1 ê¢â¬â Fundamentos de Contexto** | ê°Å¸Å¸Â¢ emerald | 1.1, 1.2 | ê¢â¬â |
| **T2 ê¢â¬â Engenharia da Mensagem** | ê°Å¸âÂµ blue | 2.1, 2.2 | ê¢â¬â |
| **T3 ê¢â¬â RAG e RecuperaêÂ§êÂ£o** | ê°Å¸Å¸Â£ purple | 3.1, 3.2 | 3.3 |
| **T4 ê¢â¬â Tools, Agentes e Multi-Agente** | ê°Å¸Å¸Â  amber | 4.1, 4.2 | 4.3 |
| **T5 ê¢â¬â MemêÂ³ria e CompressêÂ£o** | ê°Å¸âÂ· teal | 5.1 | 5.2 |
| **T6 ê¢â¬â AvaliaêÂ§êÂ£o e ProduêÂ§êÂ£o** | ê°Å¸âÂ´ rose | 6.1 | 6.2 |

**Total v1.0:** 10 mêÂ³dulos GA + 4 beta + 3 projetos GA (P1, P2, P5) + 2 opcionais (P3, P4).

---

## Comece aqui

1. **Verifique prêÂ©-requisitos:** [PRE-REQUISITOS.md](./PRE-REQUISITOS.md).
2. **Leia o escopo** (o que estêÂ¡ dentro / fora): [ESCOPO.md](./ESCOPO.md).
3. **Instale o cliente do curso:**
   ```bash
   pip install fec-sdk==<versêÂ£o da release> --require-hashes -r releases/v1.0.0/lockfile.toml
   ```
4. **Abra a landing local:** `open index.html` (ou acesse a versêÂ£o hospedada quando publicada).
5. **Siga a trilha 1** em `curso/trilha1/index.html`.

ê¢Å¡Â ê¯Â¸Â **Canal canêÂ´nico de download:** sempre o asset nomeado `fec-vX.Y.Z.zip` da [GitHub Release](https://github.com/linnoff88-dev/FEC/releases). Os "Source code (zip/tar.gz)" auto-gerados pelo GitHub **nêÂ£o sêÂ£o auditados**.

---

## Status do projeto

Em desenvolvimento ativo seguindo o [PLAN.md](./PLAN.md) (95 itens, endurecido por 5 rodadas adversariais ê¢â¬â ver [RELATORIO-CLAUDEX.md](./RELATORIO-CLAUDEX.md)).

- ê°Å¸âÂ´ **NêÂ£o publicado.** v1.0.0 prevista para maio/2026.
- ê°Å¸Å¸Â¡ **Apenas scaffolding.** ConteêÂºdo dos mêÂ³dulos serêÂ¡ adicionado em ondas (T1 piloto ê¢â â T2-T3 ê¢â â T4-T6).
- ê¢Åâ¦ **Plano completo** com gates objetivos, harness de avaliaêÂ§êÂ£o congelado, runbooks de incidente, e protocolo de release atêÂ´mico.

Acompanhe o progresso em [`docs/status.html`](./docs/status.html) (publicado em GitHub Pages apêÂ³s primeiro release).

---

## Diferencial editorial

- **Provider-neutral primeiro.** Cada padrêÂ£o êÂ© ensinado em forma agnêÂ³stica e depois materializado em provedor canêÂ´nico do mêÂ³dulo, com adaptadores para os outros e mocks para casos nêÂ£o-portêÂ¡veis.
- **Toda alegaêÂ§êÂ£o de ganho roda no harness** [`evals/v1/`](./evals/v1/) ê¢â¬â datasets, judges e modelos pinados; sem cherry-pick.
- **SeêÂ§êÂ£o "Quando NêÆO usar"** obrigatêÂ³ria em todo padrêÂ£o ê¢â¬â RAG, agente, multi-agente, memêÂ³ria, caching.
- **ExercêÂ­cios com teste automatizado.** Aluno roda `pytest` e sabe se passou ê¢â¬â nêÂ£o "achismo".
- **Sandbox obrigatêÂ³rio** para todo lab que toca filesystem/processo/rede. Bateria de testes de traversal antes de virar GA.

---

## Estrutura do repositêÂ³rio

```
FEC/
ê¢âÅê¢ââ¬ê¢ââ¬ PLAN.md, RELATORIO-CLAUDEX.md     # plano endurecido + relatêÂ³rio do loop
ê¢âÅê¢ââ¬ê¢ââ¬ ESCOPO.md, PRE-REQUISITOS.md, GLOSSARIO.md, CHANGELOG.md
ê¢âÅê¢ââ¬ê¢ââ¬ SECURITY.md, RUNBOOK.md, ALERTS.md, RELEASE-INCIDENT.md
ê¢âÅê¢ââ¬ê¢ââ¬ COMPAT.md, MODELOS.md, CAPACIDADES.md  # gerados de evals/v1/*.json
ê¢âÅê¢ââ¬ê¢ââ¬ index.html                         # landing ARCKHê
ê¢âÅê¢ââ¬ê¢ââ¬ curso/trilha[1-6]/{index,modulo-X-Y}.html
ê¢âÅê¢ââ¬ê¢ââ¬ fec_sdk/                           # cliente abstrato + adaptadores + sandbox
ê¢âÅê¢ââ¬ê¢ââ¬ exemplos/, exercicios/, solucoes/
ê¢âÅê¢ââ¬ê¢ââ¬ projetos/{P1,P2,P5}/ + projetos/post-launch/{P3,P4}/
ê¢âÅê¢ââ¬ê¢ââ¬ quizzes/*.json
ê¢âÅê¢ââ¬ê¢ââ¬ evals/v1/{compat,revoked_versions,budgets,models,capabilities,...}.json
ê¢âÅê¢ââ¬ê¢ââ¬ schemas/*.schema.json              # JSON Schema 2020-12 ê¢â¬â source of truth
ê¢âÅê¢ââ¬ê¢ââ¬ assets/{css/, diagrams/, csp/, banners/}
ê¢âÅê¢ââ¬ê¢ââ¬ runbooks/                          # playbooks por classe de falha
ê¢âÅê¢ââ¬ê¢ââ¬ postmortems/                       # incidentes pêÂºblicos
ê¢âÅê¢ââ¬ê¢ââ¬ releases/v<X.Y.Z>/lockfile.toml
ê¢ââê¢ââ¬ê¢ââ¬ scripts/                           # automaêÂ§êÂµes de validaêÂ§êÂ£o, build, release
```

---

## Contribuindo

Veja [CONTRIBUTING.md](./CONTRIBUTING.md). Fluxos:

- **Errata** ê¢â â issue com label `errata` (templates em `.github/ISSUE_TEMPLATE/`).
- **DêÂºvida** ê¢â â issue com label `duvida`.
- **SugestêÂ£o de têÂ³pico/mêÂ³dulo** ê¢â â RFC em PR.
- **ConteêÂºdo novo** ê¢â â segue o contrato fixo de mêÂ³dulo (item 18 do PLAN).

CODEOWNERS bloqueia mudanêÂ§as em `.github/workflows/**`, `evals/**`, `MODELOS.md`, `BUDGETS.md` ê¢â¬â exigem aprovaêÂ§êÂ£o de maintainer.

---

## LicenêÂ§as

- **ConteêÂºdo (texto, ilustraêÂ§êÂµes, slides):** [CC BY-SA 4.0](./LICENSE)
- **CêÂ³digo (exemplos, exercêÂ­cios, fec_sdk, scripts):** [MIT](./LICENSE-CODE)
- **Terceiros:** ver [LICENSES-THIRD-PARTY.md](./LICENSES-THIRD-PARTY.md) (datasets, screenshots, papers citados).

---

## SeguranêÂ§a

Encontrou vulnerabilidade? Veja [SECURITY.md](./SECURITY.md) ê¢â¬â nêÂ£o abra issue pêÂºblico; use o canal privado descrito lêÂ¡.

---

**Mantido pelo ARCKHê ê¢â¬â [ARCKHê AI](https://ARCKHê AI).**

<!-- ARCKHê-backlink:v1 -->
## Mais no ARCKHê AI

- [Ficha completa deste curso](https://www.ARCKHê AI/cursos/87-fec-formacao-de-engenharia-de-contexto/)
- [Guia: como aprender inteligêÂªncia artificial](https://www.ARCKHê AI/aprender-inteligencia-artificial/)
- [Todos os cursos](https://www.ARCKHê AI/cursos/)
<!-- /ARCKHê-backlink:v1 -->

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>