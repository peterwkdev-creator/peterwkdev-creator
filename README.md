# Hi, I'm Peter

I build **public websites on top of official Brazilian data** — the number, its
source and its date, on one page a person can actually use. Senior software
engineer since 2017; everything below is my own work, running in production.

## Live products

### [Números Públicos](https://www.numerospublicos.com.br) · [source](https://github.com/peterwkdev-creator/numeros-publicos)

One page for each of Brazil's **5,571 municipalities**: population, GDP, where
the budget comes from, what it is spent on, personnel spending against the
legal limit, health spending and school results — IBGE, National Treasury and
INEP data that no single source publishes together.

**37.6k Google search impressions** in its first month online · every figure
carries its source and collection date · 137k published values re-checked
against the database before each release.

### [Chegou na hora?](https://chegounahora.com.br)

Does this flight usually arrive on time? **Real arrival punctuality** for
domestic flights in Brazil — by flight number, route, airport and airline —
from ANAC's official flight records, with the promised time next to what
actually happened. 777 pages, launched September 2026.

### [NumeraSheets](https://numerasheets.com) · [shop on Etsy](https://numerasheets.etsy.com) · [source](https://github.com/peterwkdev-creator/numerasheets-site)

Formula-driven spreadsheet templates — invoices and expenses, rental
property, marketplace fees, social media content — each with a filled-in
example and a setup guide, sold as instant downloads.

## The engines behind them (open source, AGPL-3.0)

| | What it does |
|---|---|
| [painel-fiscal-ne](https://github.com/peterwkdev-creator/painel-fiscal-ne) | Sweeps the fiscal reports of all 5,570 municipalities from the National Treasury, resumably, and flags implausible filings instead of ranking them |
| [educacao-inep](https://github.com/peterwkdev-creator/educacao-inep) | Reads the IDEB school index per municipality out of INEP's spreadsheet, past six silent traps |
| [radar-licitacoes](https://github.com/peterwkdev-creator/radar-licitacoes) | Sweeps Brazil's public procurement API for the IT contracts a small supplier can bid on, and keeps an audit trail of what it discarded |

**How they're built:** Python (standard library) → SQLite → static site.
No server to keep alive, a cross-check against the official aggregate before
anything is published, and absence is never turned into a number.

## Contact

**[peterwk.dev@gmail.com](mailto:peterwk.dev@gmail.com)**

<details>
<summary><b>Em português</b></summary>

<br>

Construo **sites públicos sobre dados oficiais do Brasil** — o número, a fonte
e a data, numa página que uma pessoa consegue usar. Engenheiro de software
sênior desde 2017; tudo abaixo é trabalho meu, no ar.

- **[Números Públicos](https://www.numerospublicos.com.br)** — uma página para
  cada um dos 5.571 municípios: população, PIB, de onde vem e para onde vai o
  orçamento, gasto com pessoal contra o limite legal, saúde e educação. 37,6
  mil impressões no Google no primeiro mês.
- **[Chegou na hora?](https://chegounahora.com.br)** — a pontualidade real de
  cada voo doméstico, pela chegada, com o dado oficial da ANAC.
- **[NumeraSheets](https://numerasheets.com)** — planilhas prontas com
  fórmulas, exemplo preenchido e guia de uso, à venda na
  [loja da Etsy](https://numerasheets.etsy.com).

Os motores de dados são abertos (AGPL-3.0): painel fiscal, IDEB e radar de
licitações.

**Contato:** [peterwk.dev@gmail.com](mailto:peterwk.dev@gmail.com)

</details>
