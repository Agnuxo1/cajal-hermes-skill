# CAJAL Skill for Hermes Agent

> Generate publication-ready scientific papers directly from your Hermes Agent. Local, free, open-source.

## What This Skill Does

Adds a `paper` command to Hermes that generates complete scientific papers with:
- **7 sections**: Abstract → Introduction → Methods → Results → Discussion → Conclusion → References
- **Real citations**: arXiv/CrossRef integration — no hallucinated references
- **Tribunal scoring**: 8-10 LLM judges evaluate paper quality
- **100% local**: Runs on your Ollama instance, zero cloud dependency

## Why CAJAL + Hermes?

Hermes is a **learning agent** that creates skills from experience. Researchers using Hermes can now:
1. Generate paper drafts from research conversations
2. Save successful prompts as reusable skills
3. Build a personal paper-generation library over time
4. Never pay API fees for academic writing

## Installation

```bash
# 1. Clone into Hermes skills directory
git clone https://github.com/Agnuxo1/cajal-hermes-skill.git ~/.hermes/skills/cajal-papers

# 2. Install CAJAL
pip install cajal-p2pclaw

# 3. Create Ollama model
ollama create cajal -f https://raw.githubusercontent.com/Agnuxo1/CAJAL/main/integrations/ollama/Modelfile

# 4. Restart Hermes gateway
hermes gateway
```

## Usage

In any Hermes channel:

```
/paper generate "Quantum error correction with surface codes"
```

Returns a full paper in markdown.

Other commands:
- `/paper abstract "Neural architecture search"` — 150-250 word abstract
- `/paper methods "Federated learning privacy"` — Reproducible methodology
- `/paper references "Byzantine consensus" 12` — Find 12 relevant papers
- `/paper review draft.md` — Peer review with scores

## How It Works

```
User request ──▶ Hermes parses /paper command
                  │
                  ▼
            CAJAL engine (local Ollama)
                  │
                  ├── Structured generation (7 sections)
                  ├── arXiv citation lookup
                  └── Tribunal scoring
                  │
                  ▼
            Hermes saves as skill
                  │
                  ▼
            User gets paper + scores
```

## Configuration

Add to `~/.hermes/config.yaml`:

```yaml
skills:
  cajal-papers:
    ollama_host: "http://localhost:11434"
    model: "cajal"
    temperature: 0.3
    min_references: 8
    default_format: "markdown"
```

## Requirements

- Hermes Agent ≥ 1.0
- Ollama running locally
- `cajal-p2pclaw` PyPI package
- Any Ollama-compatible model (llama3.1, qwen3.5, etc.)

## License

MIT — Same as Hermes Agent. A genuine gift, not a product.

---

**Created by:** [P2PCLAW Research Network](https://p2pclaw.com)  
**GitHub:** [Agnuxo1/CAJAL](https://github.com/Agnuxo1/CAJAL)  
**PyPI:** `pip install cajal-p2pclaw`
