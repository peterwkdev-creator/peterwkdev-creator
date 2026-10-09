# Oi, eu sou o Peter

Construo **sites públicos sobre dados oficiais do Brasil**: o número, a fonte
e a data, numa página que uma pessoa consegue usar. Engenheiro de software
sênior desde 2017; tudo abaixo é trabalho meu, no ar.

## Produtos no ar

### [Números Públicos](https://www.numerospublicos.com.br) · [código](https://github.com/peterwkdev-creator/numeros-publicos)

Uma página para cada um dos **5.571 municípios** do Brasil: população, PIB, de
onde vem o orçamento, em que ele é gasto, gasto com pessoal contra o limite
legal, saúde e resultados escolares. Dados do IBGE, do Tesouro Nacional e do
INEP que nenhuma fonte publica juntos.

**37,6 mil impressões no Google** no primeiro mês no ar · cada número traz a
fonte e a data da coleta · 137 mil valores publicados reconferidos contra o
banco antes de cada versão.

### [Chegou na hora?](https://chegounahora.com.br)

Esse voo costuma chegar no horário? **A pontualidade real na chegada** dos
voos domésticos no Brasil, por número do voo, rota, aeroporto e companhia, com
os registros oficiais da ANAC: o horário prometido ao lado do que aconteceu.
777 páginas, no ar desde setembro de 2026.

### [NumeraSheets](https://numerasheets.com) · [loja na Etsy](https://numerasheets.etsy.com) · [código](https://github.com/peterwkdev-creator/numerasheets-site)

Planilhas prontas com fórmulas (notas e despesas, imóvel de aluguel, taxas de
marketplace, conteúdo para redes sociais), cada uma com exemplo preenchido e
guia de uso, vendidas para baixar na hora.

## Os motores por trás (código aberto, AGPL-3.0)

| | O que faz |
|---|---|
| [painel-fiscal-ne](https://github.com/peterwkdev-creator/painel-fiscal-ne) | Varre os relatórios fiscais dos 5.570 municípios no Tesouro Nacional, retomando de onde parou, e marca o envio implausível em vez de ranqueá-lo |
| [educacao-inep](https://github.com/peterwkdev-creator/educacao-inep) | Lê o IDEB de cada município na planilha do INEP, passando por seis armadilhas silenciosas |
| [radar-licitacoes](https://github.com/peterwkdev-creator/radar-licitacoes) | Varre a API de compras públicas (PNCP) atrás dos contratos de TI que um fornecedor pequeno pode disputar, e guarda o registro do que descartou |

**Biblioteca aberta (MIT):** [simples-nacional-br](https://github.com/peterwkdev-creator/simples-nacional-br),
alíquota efetiva, valor do mês e Fator R do Simples Nacional, conferidos
faixa a faixa contra as tabelas oficiais da LC 123/2006.

**Como são feitos:** Python (biblioteca padrão) → SQLite → site estático. Sem
servidor para manter de pé, conferência contra o total oficial antes de
publicar qualquer coisa, e ausência de dado nunca vira número.

## Contato

**[peterwk.dev@gmail.com](mailto:peterwk.dev@gmail.com)**

<details>
<summary><b>In English</b></summary>

<br>

I build **public websites on top of official Brazilian data**: the number, its
source and its date, on one page a person can actually use. Senior software
engineer since 2017; everything here is my own work, running in production.

- **[Números Públicos](https://www.numerospublicos.com.br)**: one page for
  each of Brazil's 5,571 municipalities (population, GDP, budget, personnel
  spending against the legal limit, health and schools). 37.6k Google search
  impressions in its first month.
- **[Chegou na hora?](https://chegounahora.com.br)**: real arrival
  punctuality for every domestic flight in Brazil, from ANAC's official
  records.
- **[NumeraSheets](https://numerasheets.com)**: formula-driven spreadsheet
  templates with a filled-in example and a setup guide, sold on
  [Etsy](https://numerasheets.etsy.com).

The data engines are open source (AGPL-3.0): fiscal reports, IDEB and public
procurement. [simples-nacional-br](https://github.com/peterwkdev-creator/simples-nacional-br)
(MIT) computes Brazil's Simples Nacional tax, checked bracket by bracket
against the official tables.

**Contact:** [peterwk.dev@gmail.com](mailto:peterwk.dev@gmail.com)

</details>
