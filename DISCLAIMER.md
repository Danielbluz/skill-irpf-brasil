# DISCLAIMER — Isenção de Responsabilidade

**Data:** 25/04/2026
**Projeto:** skill-irpf-brasil (Agent Skill IRPF Brasil)
**Autor:** Daniel Luz ([@Danielbluz](https://github.com/Danielbluz))

---

## 1. Natureza do projeto

Este é um **projeto pessoal, amador e sem fins lucrativos**, desenvolvido como exercício de:

- Organização estruturada de conhecimento tributário brasileiro.
- Aprendizado sobre o formato Agent Skill (Anthropic).
- Compartilhamento livre com a comunidade.

**Não é** um produto comercial, software certificado, sistema contábil profissional, nem ferramenta validada por órgão regulador.

---

## 2. Ausência de revisão profissional

O conteúdo desta skill **NÃO foi revisado por contador habilitado** (registrado no Conselho Regional de Contabilidade — CRC), advogado tributarista, ou qualquer profissional credenciado pela Receita Federal do Brasil.

O conteúdo reflete:

- Leitura própria do autor de legislação pública (Leis, Instruções Normativas, etc).
- Síntese de fontes secundárias (artigos jornalísticos, blogs especializados, comunicados oficiais).
- Auditoria automatizada por modelos de linguagem (Perplexity, Gemini) — que **podem ter produzido falsos positivos ou negativos** durante a validação.

**O autor é Engenheiro Eletricista**, especialista em Mercados de Energia Elétrica e Geração Distribuída, entusiasta de Transformação Digital e Inteligência Artificial — **não é contador habilitado** nem profissional da área tributária.

---

## 3. Ausência de garantias

A skill é distribuída **"COMO ESTÁ" (AS IS)**, sem qualquer garantia expressa ou implícita, incluindo mas não limitado a:

- Precisão das informações tributárias.
- Adequação a casos específicos.
- Atualidade frente a mudanças regulatórias.
- Ausência de erros, omissões ou interpretações equivocadas.

A licença MIT (ver [LICENSE](LICENSE)) reforça essa ausência de garantia em termos legais.

---

## 4. Ausência de responsabilidade

O autor **NÃO se responsabiliza** por:

### 4.1 Decisões fiscais

Decisões tomadas pelo usuário ou terceiros com base no conteúdo desta skill, incluindo (mas não limitado a):

- Inclusão ou omissão de dependentes.
- Escolha entre modelo completo e simplificado.
- Lançamento de despesas dedutíveis.
- Apuração de ganhos de capital.
- Tributação de rendimentos no exterior.
- Qualquer decisão que afete o cálculo do imposto a pagar ou a restituir.

### 4.2 Consequências fiscais

Quaisquer consequências fiscais ou financeiras, incluindo (mas não limitado a):

- Incidência em malha fina.
- Lançamentos de ofício pela Receita Federal.
- Multas, juros, mora.
- Autuações por sonegação.
- Perda de benefícios fiscais.
- Repercussões patrimoniais ou criminais.

### 4.3 Erros técnicos

- Erros no parser Python (`scripts/parse_dbk.py`).
- Falhas de leitura ou interpretação de arquivos DBK.
- Falsos positivos ou negativos em auditoria heurística.
- Vulnerabilidades de segurança (apesar de não haver coleta de dados ou comunicação externa).

### 4.4 Desatualização

- A skill cobre IRPF **ciclo 2026 / ano-base 2025**.
- Mudanças regulatórias após **abril/2026** podem invalidar partes do conteúdo.
- O autor não se compromete a manter a skill atualizada.
- Forks e versões derivadas são responsabilidade dos respectivos mantenedores.

---

## 5. Recomendação categórica

Para qualquer decisão fiscal com **valor financeiro relevante** ou **risco patrimonial**, especialmente:

- 💰 Alta renda anual (acima de R$ 600.000).
- 🏢 Sócio de pessoa jurídica com distribuição de lucros.
- 🌎 Investimentos no exterior (offshore, trust, ações estrangeiras).
- 🏠 Alienação de imóvel com ganho de capital significativo.
- ⚱️ Espólio com bens diversos.
- 🌾 Atividade rural com receita relevante.
- 🎯 Casos de IRPFM (Imposto Mínimo Pessoa Física).

→ **CONSULTE UM CONTADOR HABILITADO** registrado no CRC ou advogado tributarista.

A consulta profissional **não é opcional** nesses casos — é o meio adequado para garantir conformidade fiscal e proteção patrimonial.

---

## 6. Uso oficial — apenas pelo programa da RFB

A **única forma autoritativa** de transmitir uma declaração de IRPF é através do **programa oficial** disponibilizado pela Receita Federal:

- **Download**: https://www.gov.br/receitafederal/pt-br/assuntos/meu-imposto-de-renda
- **Web (Meu IR)**: https://www.gov.br/receitafederal/pt-br/assuntos/meu-imposto-de-renda

Esta skill **NÃO transmite declarações**, **NÃO calcula imposto oficialmente**, e **NÃO substitui** o programa da RFB.

---

## 7. Privacidade e segurança

- O parser `parse_dbk.py` opera **localmente** no computador do usuário — sem comunicação com servidores externos.
- CPF e CNPJ são **mascarados por padrão** no relatório de auditoria.
- Valores monetários são **omitidos por padrão** (ativados apenas com `--include-values`).
- Arquivos DBK contêm dados pessoais sensíveis (CPF, valores, despesas médicas, dados familiares). **Nunca compartilhe seu DBK** em chats públicos, redes sociais, ou serviços de IA online sem mascarar dados sensíveis.
- O autor recomenda manter DBK criptografado (BitLocker, VeraCrypt) ou em pasta de acesso restrito.

---

## 8. Aceite de uso

**Ao utilizar esta skill, você reconhece e aceita:**

1. Ter lido e compreendido este DISCLAIMER e o [LICENSE](LICENSE).
2. Que o uso é **por sua conta e risco**.
3. Que **não há relação contratual, profissional ou consultiva** com o autor.
4. Que **não há expectativa de suporte técnico** ou atualizações.
5. Que **consultará profissional habilitado** para casos relevantes.

Se você não concorda com qualquer item acima, **não utilize esta skill**.

---

## 9. Contato

Para reportar erros regulatórios, sugerir melhorias ou tirar dúvidas técnicas:

- **Issues no GitHub**: https://github.com/Danielbluz/skill-irpf-brasil/issues
- **Pull Requests**: contribuições com fontes oficiais são bem-vindas.

**Não responderei**:
- Consultas fiscais individualizadas (procure um contador).
- Pedidos de orientação para casos específicos.
- Solicitações de atualização urgente.

---

*Última atualização: 25/04/2026.*
