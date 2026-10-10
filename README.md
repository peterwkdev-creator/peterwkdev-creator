# Oi, eu sou o Peter

Construo **ferramentas sobre dados e regras oficiais do Brasil**: sites que
mostram o número com a fonte e a data, e bibliotecas abertas que conferem a
regra contra o texto oficial. Engenheiro de software sênior desde 2017; tudo
abaixo é trabalho meu, no ar.

## Produtos no ar

### [Números Públicos](https://www.numerospublicos.com.br) · [código](https://github.com/peterwkdev-creator/numeros-publicos)

Uma página para cada um dos **5.571 municípios** do Brasil: população, PIB, de
onde vem o orçamento, em que ele é gasto, gasto com pessoal contra o limite
legal, saúde e resultados escolares. Dados do IBGE, do Tesouro Nacional e do
INEP que nenhuma fonte publica juntos. Cada número traz a fonte e a data da
coleta, e os valores publicados são reconferidos contra o banco antes de cada
versão.

### [Chegou na hora?](https://chegounahora.com.br)

Esse voo costuma chegar no horário? **A pontualidade real na chegada** dos
voos domésticos no Brasil, por número do voo, rota, aeroporto e companhia, com
os registros oficiais da ANAC: o horário prometido ao lado do que aconteceu.
2.646 páginas (2.021 voos, 540 rotas, 74 aeroportos), no ar desde setembro de
2026.

### [NumeraSheets](https://numerasheets.com) · [loja na Etsy](https://numerasheets.etsy.com) · [código](https://github.com/peterwkdev-creator/numerasheets-site)

Planilhas prontas com fórmulas (notas e despesas, imóvel de aluguel, taxas de
marketplace, conteúdo para redes sociais), cada uma com exemplo preenchido e
guia de uso, vendidas para baixar na hora.

## Bibliotecas abertas (MIT)

Python sem dependência, com testes contra a fonte oficial e uma página para
experimentar no navegador, sem instalar nada.

| | O que faz | |
|---|---|---|
| [simples-nacional-br](https://github.com/peterwkdev-creator/simples-nacional-br) | Simples Nacional: alíquota efetiva, valor do mês, Fator R e a repartição do DAS por tributo, conferidos faixa a faixa contra as tabelas da LC 123/2006 e da LC 214/2025; também como servidor MCP, para o Claude e outros assistentes chamarem as mesmas contas | [experimentar](https://peterwkdev-creator.github.io/simples-nacional-br/) |
| [linguagem-simples-br](https://github.com/peterwkdev-creator/linguagem-simples-br) | Confere um texto contra os 18 incisos da Lei 15.263/2025 (Linguagem Simples) e diz, inciso por inciso, o que achou e o que não tem como conferir; precisão medida no README | [experimentar](https://peterwkdev-creator.github.io/linguagem-simples-br/) |

## Para quem usa o Claude Code (MIT)

| | O que faz |
|---|---|
| [claude-context-cost](https://github.com/peterwkdev-creator/claude-context-cost) | Quanto cada fonte (`CLAUDE.md`, regras, skills, memória, resultado de ferramenta) custa no contexto de uma sessão, contado pelo `usage` da API gravado na transcrição, não estimado pelos caracteres; lê só os arquivos locais |

## Os motores por trás dos sites (AGPL-3.0)

| | O que faz |
|---|---|
| [painel-fiscal](https://github.com/peterwkdev-creator/painel-fiscal) | Varre os relatórios fiscais dos 5.570 municípios no Tesouro Nacional, retomando de onde parou, e marca o envio implausível em vez de ranqueá-lo |
| [educacao-inep](https://github.com/peterwkdev-creator/educacao-inep) | Lê o IDEB de cada município na planilha do INEP, passando por seis armadilhas silenciosas |

**Como são feitos:** Python → SQLite → site estático, sem servidor para manter
de pé. Conferência contra o total oficial antes de publicar qualquer coisa,
ausência de dado nunca vira número, e nenhuma alegação sem o número medido.

## Contato

**[peterwk.dev@gmail.com](mailto:peterwk.dev@gmail.com)**

<details>
<summary><b>In English</b></summary>

<br>

I build **tools on top of official Brazilian data and rules**: websites that
show the number with its source and date, and open libraries that check a rule
against the official text. Senior software engineer since 2017; everything
here is my own work, running in production.

- **[Números Públicos](https://www.numerospublicos.com.br)**: one page for
  each of Brazil's 5,571 municipalities (population, GDP, budget, personnel
  spending against the legal limit, health and schools), each number with its
  source and collection date.
- **[Chegou na hora?](https://chegounahora.com.br)**: real arrival
  punctuality for every domestic flight in Brazil, from ANAC's official
  records (2,646 pages).
- **[NumeraSheets](https://numerasheets.com)**: formula-driven spreadsheet
  templates with a filled-in example and a setup guide, sold on
  [Etsy](https://numerasheets.etsy.com).

Open libraries (MIT, pure Python, each with an in-browser demo):
[simples-nacional-br](https://github.com/peterwkdev-creator/simples-nacional-br)
computes Brazil's Simples Nacional tax and its split by tax, checked bracket
by bracket against the official tables, also as an MCP server for Claude
and other assistants;
[linguagem-simples-br](https://github.com/peterwkdev-creator/linguagem-simples-br)
checks a text against Brazil's Plain Language Law (Lei 15.263/2025).
For Claude Code users, [claude-context-cost](https://github.com/peterwkdev-creator/claude-context-cost) (MIT) measures how much
each source (`CLAUDE.md`, rules, skills, memory, tool results) costs in a
session's context, from the API `usage` recorded in its transcript. The data
engines behind the sites are open source too (AGPL-3.0): fiscal reports and
IDEB.

**Contact:** [peterwk.dev@gmail.com](mailto:peterwk.dev@gmail.com)

</details>
