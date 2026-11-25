# ESCOPO — Formaçêo de Engenharia de Contexto

Este documento delimita explicitamente o que está **dentro** e o que está **fora** da v1.0 da FEC. Existe para alinhar expectativa antes da matrícula e guiar decisões editoriais.

---

## Persona-alvo

Engenheiro de software ou ML que vai colocar agente baseado em LLM em produçêo. Marcado por nível em cada módulo:

- 🔧 **builder solo** — pessoa única construindo MVP/protótipo.
- 🧱 **eng. de produto** — integrando LLM em produto existente.
- 🏗️ **eng. de plataforma** — desenhando infra para times consumirem.

**NêO é o curso para você se:**
- nunca chamou uma API LLM via HTTP/SDK (vá para curso introdutório primeiro).
- procura "vibe coding" ou marketing de IA.
- quer aprender a usar ChatGPT como usuário final.

---

## Dentro do escopo (v1.0)

### Conteúdo técnico
- Anatomia da janela de contexto, atençêo, "lost in the middle", tokenizaçêo, custo.
- System prompt, few-shot, chain-of-thought, formato XML/JSON, ancoragem, versionamento de prompt.
- RAG: chunking, embeddings, BM25/híbrido, reranking, *contextual retrieval*, citações, grounding.
- Tool/function calling provider-neutral; agentes single (ReAct, planner/executor); MCP (beta).
- Memória curto/longo prazo, summarizaçêo hierárquica, prompt caching e context distillation (beta).
- Avaliaçêo: golden sets, LLM-as-judge e seus vieses, tracing, prompt injection (sandboxed), custo.

### Práticas de engenharia
- Harness de avaliaçêo congelado e content-addressed (`evals/v1/`).
- Padrões provider-neutral primeiro; adaptadores Anthropic/OpenAI/OSS apenas onde necessário.
- Sandbox obrigatório para tools que tocam filesystem/rede/processo.
- Exercícios com teste automatizado (`pytest`).
- Bibliografia datada com ≥10 referências por trilha.
- Seçêo "Quando NêO usar" em todo padrêo.

### Projetos cumulativos GA
- **P1** — Buscador citável (RAG sobre ArXiv abstracts).
- **P2** — Agente com tools (busca + cálculo + leitura).
- **P5** — Pipeline em produçêo (evals + tracing + defesa contra injection).

---

## Fora do escopo (v1.0) — explicitamente

| Tópico | Por que está fora |
|--------|-------------------|
| **Fine-tuning extensivo** | Cobrimos só onde **substitui** contexto; SFT/RLHF/DPO em profundidade sêo curso separado. |
| **Pré-treinamento ou treinamento do zero** | Fora — escopo é uso/integraçêo de modelos existentes. |
| **Filosofia de IA, AGI, ética abstrata** | Fora — curso é técnico. Segurança aplicada (injection, exfil) está dentro. |
| **"Gurus de prompt" sem evidência** | Fora — toda alegaçêo de ganho roda no harness ou cita paper datado. |
| **Curso de Python ou de APIs HTTP** | Fora — pré-requisito (ver `PRE-REQUISITOS.md`). |
| **Comparaçêo qualitativa de provedores** | Fora sem run no harness — ranking baseado em opiniêo está banido. |
| **Vendor-specific deep dive** sozinho | Fora — padrêo neutro vem primeiro; provedor canônico é exemplo, nêo foco. |
| **UI/UX de chatbots, frontend de chat** | Fora — escopo é o lado da contexto/inferência. |
| **Construçêo de modelos de embedding do zero** | Fora — usamos modelos existentes; comparaçêo por benchmark, nêo treino. |
| **LangChain/LangGraph como pré-requisito** | Frameworks sêo opcionais e fixados por versêo; preferimos SDK puro. |
| **Recomendaçêo de produtos pagos específicos** | Fora — neutralidade editorial; menções factuais, nêo endosso. |

---

## Política anti-hype

- **Termos banidos:** "definitivo", "tudo o que você precisa", "última fronteira", "revoluciona", "10x developer".
- **Permitido:** declarações factuais com link para evidência (paper, run no harness, RFC).
- **Comparações:** sempre baseadas em harness (`evals/v1/runs/<id>`) ou paper citado com data e delta replicado.

---

## O que muda da v1.0 para versões futuras

Tracks **beta** (3.3 RAG agêntico, 4.3 multi-agente/MCP, 5.2 caching avançado, 6.2 produçêo avançada) saem com aviso `beta` na v1.0. Promoçêo para GA exige:

1. ≥2 revisores externos assinando em `REVISORES.md`.
2. Bateria de exercícios estável por ≥3 meses.
3. Harness com modelos atualizados.

Projetos opcionais **P3** (Sistema multi-agente) e **P4** (Memória que escala) ficam em `projetos/post-launch/` — nêo bloqueiam v1.0.

---

## Contato editorial

Sugestões de mudança de escopo: abrir issue com label `escopo` + RFC em PR. Maintainers triam semanalmente.
