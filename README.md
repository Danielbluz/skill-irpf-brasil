# skill-irpf-brasil

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/status-projeto%20pessoal-orange.svg)](#-disclaimer-importante)
[![Ano-base](https://img.shields.io/badge/IRPF-2026%20%28ano--base%202025%29-blue.svg)](#-escopo)
[![Idioma](https://img.shields.io/badge/idioma-pt--BR-green.svg)](#)
[![GitHub Pages](https://img.shields.io/badge/docs-online-blue.svg)](https://danielbluz.github.io/skill-irpf-brasil/)
[![Release](https://img.shields.io/github/v/release/Danielbluz/skill-irpf-brasil?label=version)](https://github.com/Danielbluz/skill-irpf-brasil/releases/latest)

> 🌐 **Documentação online**: https://danielbluz.github.io/skill-irpf-brasil/

> **Agent Skill** (formato Anthropic) que orienta o contribuinte brasileiro sobre o **Imposto de Renda Pessoa Física (IRPF) 2026** — ciclo do ano-base 2025. Foco em **auditoria, leitura de DBK, e prevenção de malha fina** — não substitui o programa oficial da Receita Federal nem orientação contábil profissional.

---

## ⚠️ Disclaimer Importante

**LEIA ANTES DE USAR.**

- 🧑‍💻 **Projeto pessoal e amador** desenvolvido como exercício de organização de conhecimento tributário em formato Agent Skill.
- ❌ **Não foi revisado por contador habilitado.** O conteúdo reflete leitura própria da legislação e de fontes públicas, podendo conter erros de interpretação.
- 💸 **Sem fins lucrativos.** Distribuído gratuitamente sob licença MIT.
- 🚫 **Nenhuma garantia ou responsabilidade.** O autor (@Danielbluz) **não se responsabiliza** por:
  - Decisões fiscais tomadas com base no conteúdo desta skill.
  - Eventual incidência em malha fina, autuações, multas ou outros prejuízos do contribuinte.
  - Desatualizações regulatórias após a publicação.
  - Erros de cálculo, interpretação ou orientação.
- 👨‍⚖️ **Para casos concretos** — especialmente alta renda, sócios de PJ, holding patrimonial, espólio, ativos no exterior, IRPFM — **CONSULTE UM CONTADOR HABILITADO** registrado no CRC.
- 📅 **Janela de validade limitada.** A skill cobre IRPF **ciclo 2026 / ano-base 2025**. Após maio/2026 ou mudanças regulatórias significativas, o conteúdo pode ficar desatualizado.

Ver detalhes completos em [DISCLAIMER.md](DISCLAIMER.md).

---

## 📖 Sobre o Projeto

Esta é uma **Agent Skill** no padrão Anthropic — um conjunto de arquivos markdown com **progressive disclosure**: o LLM (Claude) carrega arquivos de referência sob demanda conforme o tema da conversa do usuário.

**Não é**:
- Um programa de cálculo de imposto.
- Um substituto do programa oficial da RFB.
- Um sistema de transmissão de declaração.

**É**:
- Um conjunto estruturado de conhecimento tributário em pt-BR.
- Um parser de leitura (`scripts/parse_dbk.py`) para arquivos `.DBK` rascunho do programa IRPF.
- Um auditor heurístico que sinaliza pontos de atenção comuns (malha fina, omissões frequentes).

---

## 🎯 Escopo

| Item | Cobertura |
|---|---|
| **Ciclo** | IRPF 2026 (ano-base 2025) |
| **Base regulatória** | IN RFB nº 2.312/2026, Lei 14.754/2023, Lei 14.790/2023, Lei 14.973/2024, Lei 15.270/2025 |
| **Idioma** | Português brasileiro |
| **Formato** | Agent Skill (Anthropic) — markdown + Python stdlib |
| **Privacidade** | Parser DBK mascara CPF/CNPJ por padrão |

### Tópicos cobertos

- Obrigatoriedade de declaração (limites)
- Modelo completo vs simplificado (deduções)
- Declaração pré-preenchida e Núcleo Familiar
- Renda variável e REVAR (B3)
- Renda fixa (tabela regressiva)
- **Bets** (Lei 14.790/2023 — apuração por evento)
- Ganho de capital — alienação de imóveis (GCAP)
- **Investimentos no exterior** (Lei 14.754/2023, antidiferimento, trusts)
- Malha fina e e-Social/EFD-Reinf
- Restituição (4 lotes) e Cashback IRPF
- Casos especiais (espólio, MEI, saída definitiva, PCD, atividade rural)
- Mudanças 2026-2027 (IRPFM, dividendos 10%, isenção R$ 5k)
- Parsing de arquivos DBK/DEC do programa oficial

---

## 🚀 Como Usar

### 1. Claude Code (CLI)

```bash
# Clonar repositório
git clone https://github.com/Danielbluz/skill-irpf-brasil.git

# Copiar para diretório de skills do Claude Code
cp -r skill-irpf-brasil ~/.claude/skills/irpf-brasil

# Iniciar Claude Code e mencionar IRPF na conversa
claude
> "Tenho dúvidas sobre o IRPF 2026"
```

A skill será automaticamente carregada quando o usuário mencionar trigger words (IRPF, malha fina, DARF, REVAR, etc).

### 2. Claude.ai (web/desktop)

1. Comprimir a pasta como `skill-irpf-brasil.zip` (paths POSIX, UTF-8).
2. Acessar **claude.ai → Settings → Capabilities → Skills**.
3. **Upload skill** e selecionar o ZIP.
4. A skill ficará disponível em todas as conversas.

```bash
# No Linux/Mac
cd .. && zip -r skill-irpf-brasil.zip skill-irpf-brasil/

# No Windows (Git Bash com Python)
python -c "import zipfile, os; src='skill-irpf-brasil'; dst='skill-irpf-brasil.zip';
import os; parent=os.path.dirname(os.path.abspath(src)) or '.';
zf=zipfile.ZipFile(dst,'w',zipfile.ZIP_DEFLATED);
[zf.write(os.path.join(r,f), os.path.relpath(os.path.join(r,f), parent).replace(os.sep,'/'))
 for r,_,fs in os.walk(src) for f in fs];
zf.close()"
```

### 3. Parser de DBK (uso isolado)

```bash
python scripts/parse_dbk.py "caminho/para/sua-declaracao.DBK"
```

Gera um relatório de auditoria heurística em markdown ao lado do DBK. Por padrão, **mascara CPF/CNPJ** e **omite valores monetários** (use `--include-values` para incluir totais agregados).

Ver [scripts/README.md](scripts/README.md) para detalhes.

---

## 📁 Estrutura

```
skill-irpf-brasil/
├── SKILL.md                          # Entry point + workflow + 4 exemplos + triggers
├── REFERENCE.md                      # Índice de carregamento sob demanda
├── reference/                        # Arquivos de referência temáticos
│   ├── obrigatoriedade.md            # Limites obrigatoriedade IRPF 2026
│   ├── deducoes-modelos.md           # Completo vs simplificado, tabela progressiva
│   ├── pre-preenchida-nucleo.md      # Pré-preenchida e Núcleo Familiar
│   ├── renda-variavel-revar.md       # Bolsa, REVAR, day trade
│   ├── renda-fixa.md                 # Tabela regressiva CDB/Tesouro
│   ├── bets-apostas.md               # Lei 14.790/2023, apuração por evento
│   ├── ganho-capital-imoveis.md      # GCAP, isenção 180 dias
│   ├── investimentos-exterior.md     # Lei 14.754, antidiferimento, trusts
│   ├── malha-fina-esocial.md         # Defesa contra malha, e-Social
│   ├── restituicao-cashback.md       # 4 lotes, prioridades, Cashback IRPF
│   ├── casos-especiais.md            # Espólio, MEI, saída, PCD, rural
│   ├── mudancas-2026-2027.md         # IRPFM, dividendos 10%, planejamento
│   ├── dbk-parsing.md                # Formato DBK/DEC, leiaute
│   └── integracoes-externas.md       # irpf-investidor, ferramentas BR
└── scripts/
    ├── parse_dbk.py                  # Parser stdlib only
    └── README.md                     # Documentação do parser
```

---

## ✅ Validação

A skill passou por **3 rodadas de auditoria** durante o desenvolvimento:

1. **Perplexity Deep Research** (Sonar Deep Research): 47 itens regulatórios verificados — corrigidos 4 erros, adicionadas 6 lacunas.
2. **Gemini Deep Research**: identificou 3 lacunas válidas em meio a vários falsos positivos por confusão temporal — incorporadas (apuração por evento em bets, regime antidiferimento, trusts).
3. **Reverse engineering do leiaute DBK 2025**: parser usa offsets do `LayoutDadosDIRPF2025.md` (RafaelEstevamReis/IRPF) para registros validados.

Ainda assim, **nenhuma auditoria por LLM substitui revisão humana qualificada**. Use por sua conta e risco.

---

## 🛠️ Stack & Dependências

- **Markdown puro** para conhecimento (sem dependências).
- **Python ≥ 3.9** (stdlib only) para o parser DBK — `argparse`, `pathlib`, `zipfile`, `collections`.
- **Encoding UTF-8** com acentos nativos PT-BR.
- **Sem dependências externas** (pip, npm, etc).

---

## 🤝 Contribuindo

Sugestões, correções e adições são bem-vindas via Issues e Pull Requests.

Ver [CONTRIBUTING.md](CONTRIBUTING.md).

**Especialmente bem-vindas**:
- Correções regulatórias com fonte oficial (IN RFB, Lei, comunicados RFB).
- Cobertura de casos não tratados (ex: GCAP de criptoativos).
- Melhorias no parser DBK (offsets validados em outras versões).
- Tradução para outros idiomas (en-US para residentes fiscais bilíngues).

**Não aceitas**:
- Conteúdo gerado por LLM sem verificação humana.
- Orientações que não tenham respaldo em legislação oficial.
- Material com fins promocionais comerciais.

---

## 🔗 Recursos Relacionados

### Oficiais (Receita Federal)

- [Meu Imposto de Renda](https://www.gov.br/receitafederal/pt-br/assuntos/meu-imposto-de-renda)
- [Perguntas e Respostas IRPF 2026](https://www.gov.br/receitafederal/pt-br/centrais-de-conteudo/publicacoes/perguntas-e-respostas/dirpf/)
- [Tabelas IRPF 2026](https://www.gov.br/receitafederal/pt-br/assuntos/meu-imposto-de-renda/tabelas/2026)
- [Programa GCAP](https://www.gov.br/receitafederal/pt-br/assuntos/meu-imposto-de-renda/programa-ganho-capital)
- [REVAR (B3)](https://www.investidor.b3.com.br)

### Open Source brasileiros

- [staticdev/irpf-investidor](https://github.com/staticdev/irpf-investidor) — calcula custos B3
- [RafaelEstevamReis/IRPF](https://github.com/RafaelEstevamReis/IRPF) — documentação leiaute DBK
- [renanleonellocastro/darf_generator](https://github.com/renanleonellocastro/darf_generator) — gera DARF de bolsa

### Comunidade Claude

- [Anthropic Skills (oficial)](https://github.com/anthropics/skills)
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)
- [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills)

---

## 📜 Licença

MIT License — ver [LICENSE](LICENSE).

**Importante**: a licença MIT inclui cláusula explícita de **ausência de garantia** (`AS IS`, `WITHOUT WARRANTY`). Combinada com o [DISCLAIMER.md](DISCLAIMER.md), reforça que o uso é por **sua conta e risco**.

---

## 👤 Autor

**Daniel Luz** ([@Danielbluz](https://github.com/Danielbluz))

Engenheiro Eletricista, especialista em **Mercados de Energia Elétrica** e **Geração Distribuída**. Entusiasta de **Transformação Digital** e **Inteligência Artificial**. **Não-contador** — este projeto é exercício de organização de conhecimento, não consultoria fiscal.

> Se este projeto te ajudou, considere dar uma ⭐ — é o meu único feedback.

---

## 📅 Histórico

- **v1.0** (25/04/2026) — Lançamento público inicial. Cobre IRPF 2026 ano-base 2025 com 14 arquivos de referência + parser DBK. Validado contra Perplexity + Gemini.

---

*Desenvolvido com auxílio de Claude (Anthropic) — todo conteúdo revisado pelo autor humano antes da publicação.*
