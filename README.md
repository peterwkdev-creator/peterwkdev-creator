<p align="right">
<a href="#english">English</a> · <a href="#português-brasil">Português</a>
</p>

<a id="english"></a>
# Hi, I'm Peter 👋

Senior software engineer since 2017 — C# and Delphi in production, Python and
TypeScript for everything I build on my own. I like systems that take messy
real-world data and turn it into something a person can actually use, with the
sources still attached.

## Featured projects

### Números Públicos

**[Live site](https://www.numerospublicos.com.br)** · **[Source](https://github.com/peterwkdev-creator/observatorio-ne)** · AGPL-3.0

Open data on **all 5,571 Brazilian municipalities**: population, GDP, personnel
spending against the legal limit, spending by budget function, and school
results — ingested straight from the official **IBGE**, **National Treasury**
and **INEP** sources. No hand-typed numbers anywhere in the project.

The value is in the join: **no single source publishes these together.** A
municipality's page shows the share of its budget that went to education
(Treasury) beside the result that spending met (INEP), keyed by the shared IBGE
code.

- **Pipeline:** Python ingestion → SQLite → static JSON snapshot → Next.js
  static export. No server to keep alive, no database in production.
- **Every figure carries its source and collection date.** A `conferir` command
  cross-checks the sum of all municipalities against IBGE's own national
  aggregate before anything is published — and reports the difference instead of
  hiding it. Population matches exactly; GDP differs by 31 in 9,012,142,000,
  which is rounding, and the check says which it is.
- **Absence is never turned into a number.** "Did not file", "not yet consulted"
  and "reports as a state, not a municipality" are three different things, and
  the site keeps them apart — including in the downloads.
- **One page per municipality** — 5,571 of them, each with its own title,
  description and canonical, plus search across the whole country, filters that
  stack, and downloads in CSV and XLSX.
- **56 Python tests and 37 in the panel**, including a cross-language contract
  test that fails if the Python export and the TypeScript types ever drift
  apart — plus an accessibility audit that runs against the **generated HTML**
  in three modes: light, dark and print.

**Stack:** Python 3.12 (standard library only) · SQLite · Next.js 16 (App
Router, static export) · TypeScript · GitHub Actions · Vercel

### Radar de Licitações

**[Source](https://github.com/peterwkdev-creator/radar-licitacoes)** · AGPL-3.0

Sweeps Brazil's public procurement API for the IT contracts a small supplier can
actually compete for. Electronic auction alone publishes **2,432 contracts in a
single day**, and the API cannot filter by keyword — without a program in the
middle, the open data is unusable.

- **It stores what it discarded.** A false positive shows up and someone sees it;
  a false negative shows up nowhere, and silence is indistinguishable from
  "there was nothing there". An audit of that silence found a city hall asking
  for a website **with source code delivery** that the filter had missed by a
  single letter.
- **The sweep assumes it will be interrupted.** The API spends a daily budget
  rather than enforcing a rate, so pages are written as they arrive and a rerun
  resumes instead of re-reading.
- **Network failure is a status code, never an exception** — a socket
  `TimeoutError` is an `OSError`, not a `URLError`, and once escaped the retry
  logic entirely, taking down a run that had already read 2,500 records.
- **104 tests**, no network and no waiting: transport and clock are injected, so
  the backoff policy is verifiable rather than merely described.

**Stack:** Python 3.10+ (standard library only, zero dependencies) · SQLite

### Painel Fiscal

**[Source](https://github.com/peterwkdev-creator/painel-fiscal-ne)** · AGPL-3.0

Brazil's Fiscal Responsibility Law caps municipal personnel spending at **54%**
of net revenue, with a **51.3%** threshold that already forbids hiring. The data
is public, but it arrives one municipality per request, 200+ chart-of-accounts
lines at a time. In practice nobody looks.

The complete national sweep: **5,570 municipalities consulted, 3,244 filed, 2,326 did not** — and zero divergences across all 3,244.

**The filing rate is the finding, not the spending.** It ranges from 100% to 14% across states and follows no regional line: Santa Catarina files 86% and neighbouring Rio Grande do Sul 15%; Bahia 99% and Maranhão 49%, both in the Northeast.

- **It never recalculates the percentage.** The figure arrives computed by the
  municipality over its *adjusted* revenue — a distinction the consistency check
  itself uncovered, having first diverged in every single municipality by using
  the gross figure. **Divergence in one direction only is never chance.**
- **Implausible filings are shown as filed and labelled, not ranked.**
  Guaratinga/BA declared 371% of revenue; Paripueira/AL declared *negative*
  spending, and that one is internally consistent, so the check could not catch
  it — consistency is not plausibility. Correcting would invent a number; hiding
  would decide which filings a reader may see.

**Stack:** Python 3.12 (standard library only) · SQLite · Next.js · TypeScript

### Educação (INEP)

**[Source](https://github.com/peterwkdev-creator/educacao-inep)** · AGPL-3.0

Reads Brazil's IDEB education index per municipality out of the INEP
spreadsheet — **5,433 municipalities in the early years, 3,906 in the later
ones**, ten editions from 2005 to 2023 — and feeds the observatory, so a
municipality's page can show the share of budget spent on education beside the
result that spending met.

- **Six silent traps**, and the last two only surfaced against the real file.
  The municipality code is not the key on its own — the network is the other
  half, and `Pública` is the *aggregate* of the others, not one more network.
  Caveat markers arrive glued to the number (`206,95**`) with the legend in the
  spreadsheet's **footer**, not its header.
- **The absence of a municipal network is not a gap in the collection.** 138
  municipalities have no municipal early-years network and 1,665 have none in
  the later years — in Paraná, 388 of 399. Verified by re-ingesting with
  `--rede Estadual`: 133 of the 138 appear there.
- **Fixture agreement is not verification.** The fixture I wrote agreed with me
  by construction; only the live file exposed the last two traps.

**Stack:** Python 3.12 (standard library only) · SQLite

## What I build

**Backend & data**
- REST APIs from scratch (FastAPI), with tests
- Integrations between two systems/APIs — resumable and idempotent, because
  real integrations get interrupted
- Ingestion pipelines over public/third-party APIs, with provenance and
  verification built in
- OCR and document data extraction, PDF and report generation
- Web scraping and price monitoring

**Web**
- Web apps in Next.js/React + TypeScript, deployed and ready to use
- Static landing pages, calculators, and working prototypes

**AI-assisted workflows**
- Prompts and workflows for support and content teams
- Ticket triage and classification

## How I work

- **The spec comes before the code** — and when reality disagrees with the spec,
  the spec gets corrected first, then the code.
- **Tests from the first commit**, not "once it stabilises": one happy path per
  feature, and one regression test per bug, written before the fix.
- **No secrets in version control.** Configuration comes from the environment.
- **One documented command** to run it from a clean checkout.

## Tools

Python · TypeScript/Next.js · C# · Delphi · SQLite/PostgreSQL · FastAPI ·
Git/GitHub Actions · Vercel · Excel/Google Sheets

## Also on sale

Some of my spreadsheets grew into finished products, sold as instant downloads:
**[NumeraSheets on Etsy](https://numerasheets.etsy.com)** — formula-driven
trackers for invoices and expenses, rental property, marketplace fees and social
media content, each with a filled-in example and a setup guide. There is a
**[catalogue site](https://numerasheets.com)** too, with a screenshot of every
workbook.

## Contact

- Email: **peterwk.dev@gmail.com**

<br>

---

<a id="português-brasil"></a>
# Olá, sou o Peter 👋

*[Read in English](#english)*

Engenheiro de software sênior desde 2017 — C# e Delphi em produção, Python e
TypeScript no que construo por conta própria. Gosto de sistemas que pegam dado
bruto do mundo real e devolvem algo que uma pessoa consegue usar, com as fontes
ainda coladas no número.

## Projetos em destaque

### Números Públicos

**[Site no ar](https://www.numerospublicos.com.br)** · **[Código](https://github.com/peterwkdev-creator/observatorio-ne)** · AGPL-3.0

Dados abertos dos **5.571 municípios brasileiros**: população, PIB, gasto com
pessoal contra o limite legal, despesa por função orçamentária e resultado
escolar — ingeridos direto das fontes oficiais do **IBGE**, do **Tesouro
Nacional** e do **INEP**. Nenhum número digitado à mão em lugar nenhum do
projeto.

O valor está na costura: **nenhuma fonte publica isso junto.** A página de um
município mostra a fatia do orçamento que foi para educação (Tesouro) ao lado do
resultado que esse gasto encontrou (INEP), unidos pela chave do código IBGE.

- **Pipeline:** ingestão em Python → SQLite → snapshot JSON estático → export
  estático do Next.js. Nenhum servidor para manter de pé, nenhum banco em produção.
- **Todo número carrega a fonte e a data de coleta.** Um comando `conferir`
  cruza a soma dos municípios com o agregado nacional do próprio IBGE antes de
  qualquer publicação — e **relata** a diferença em vez de escondê-la. A
  população bate exata; o PIB difere em 31 sobre 9.012.142.000, que é
  arredondamento, e o critério diz qual dos dois é.
- **Ausência nunca vira número.** "Não entregou", "ainda não consultado" e
  "presta contas como estado, não como município" são três coisas diferentes, e
  o site as mantém separadas — inclusive nos downloads.
- **Uma página por município** — 5.571 delas, cada uma com título, descrição e
  canonical próprios, mais busca em todo o país, filtros que se somam e
  downloads em CSV e XLSX.
- **56 testes em Python e 37 no painel**, incluindo um teste de contrato entre
  linguagens que falha se o export em Python e os tipos em TypeScript se
  afastarem — e uma auditoria de acessibilidade que roda contra o **HTML
  gerado**, em três modos: claro, escuro e impressão.

**Stack:** Python 3.12 (só biblioteca padrão) · SQLite · Next.js 16 (App Router,
export estático) · TypeScript · GitHub Actions · Vercel

### Radar de Licitações

**[Código](https://github.com/peterwkdev-creator/radar-licitacoes)** · AGPL-3.0

Varre a API de compras públicas do Brasil atrás das contratações de TI que um
fornecedor pequeno consegue de fato disputar. Só o Pregão Eletrônico publica
**2.432 contratações em um único dia**, e a API **não filtra por palavra-chave**
— sem um programa no meio, o dado aberto é inutilizável.

- **Ele guarda o que descartou.** Falso positivo aparece e alguém vê; falso
  negativo não aparece em lugar nenhum, e ficar quieto é indistinguível de "não
  havia nada". A auditoria desse silêncio achou uma prefeitura pedindo site
  **com entrega do código-fonte** que o filtro tinha perdido por uma letra.
- **A varredura assume que vai ser interrompida.** A API gasta um orçamento
  diário em vez de impor uma taxa, então cada página é gravada ao chegar e uma
  nova execução retoma em vez de reler.
- **Falha de rede é status, nunca exceção** — `TimeoutError` de socket é
  `OSError`, não `URLError`, e uma vez atravessou todo o mecanismo de repetição,
  derrubando uma execução com 2.500 registros já lidos.
- **104 testes**, sem rede e sem espera: transporte e relógio são injetados, o
  que torna a política de backoff verificável em vez de apenas descrita.

**Stack:** Python 3.10+ (só biblioteca padrão, zero dependências) · SQLite

### Painel Fiscal

**[Código](https://github.com/peterwkdev-creator/painel-fiscal-ne)** · AGPL-3.0

A Lei de Responsabilidade Fiscal limita a despesa municipal com pessoal a
**54%** da receita, com um limite prudencial de **51,3%** que já proíbe
contratar. O dado é público, mas sai **um município por requisição**, em 200+
linhas de plano de contas por consulta. Na prática, ninguém olha.

A varredura nacional completa: **5.570 municípios consultados, 3.244 entregaram, 2.326 não** — e zero divergências nos 3.244.

**A taxa de entrega é o achado, não o gasto.** Ela varia de 100% a 14% entre os estados e não segue linha regional: Santa Catarina entrega 86% e o vizinho Rio Grande do Sul 15%; a Bahia 99% e o Maranhão 49%, ambos no Nordeste.

- **Ele nunca recalcula o percentual.** O número vem calculado pelo próprio
  município sobre a receita *ajustada* — distinção que a própria conferência
  descobriu, ao divergir em **todos** os municípios por usar a receita bruta.
  **Divergência num sentido só nunca é acaso.**
- **Declaração implausível é exibida como declarada e marcada, nunca ranqueada.**
  Guaratinga/BA declarou 371% da receita; Paripueira/AL declarou despesa
  **negativa** — e essa a conferência não pegou, porque é internamente coerente.
  Coerência não é plausibilidade. Corrigir seria inventar número; esconder seria
  escolher quais declarações o leitor pode ver.

**Stack:** Python 3.12 (só biblioteca padrão) · SQLite · Next.js · TypeScript

### Educação (INEP)

**[Código](https://github.com/peterwkdev-creator/educacao-inep)** · AGPL-3.0

Lê o IDEB por município da planilha do INEP — **5.433 municípios nos anos
iniciais e 3.906 nos finais**, dez edições de 2005 a 2023 — e alimenta o
observatório, para que a página de um município possa mostrar a fatia do
orçamento gasta em educação ao lado do resultado que esse gasto encontrou.

- **Seis armadilhas silenciosas**, e as duas últimas só apareceram contra o
  arquivo real. O código do município não é chave sozinho — a rede é a outra
  metade, e `Pública` é o **agregado** das outras, não uma rede a mais. Marcas
  de ressalva vêm coladas ao número (`206,95**`), com a legenda no **rodapé**
  da planilha, não no cabeçalho.
- **A ausência de rede municipal não é lacuna da coleta.** 138 municípios não
  têm rede municipal nos anos iniciais e 1.665 não têm nos finais — no Paraná,
  388 de 399. Verificado reingerindo com `--rede Estadual`: 133 dos 138
  aparecem lá.
- **Fixture que concorda não é verificação.** A que escrevi concordava comigo
  por construção; só o arquivo vivo expôs as duas últimas armadilhas.

**Stack:** Python 3.12 (só biblioteca padrão)

## O que eu construo

**Backend e dados**
- APIs REST do zero (FastAPI), com testes
- Integrações entre dois sistemas/APIs — retomáveis e idempotentes, porque
  integração de verdade é interrompida no meio
- Pipelines de ingestão sobre APIs públicas/de terceiros, com proveniência e
  conferência embutidas
- OCR e extração de dados de documentos, geração de PDF e relatórios
- Web scraping e monitoramento de preço

**Web**
- Web apps em Next.js/React + TypeScript, publicados e prontos para uso
- Landing pages estáticas, calculadoras e protótipos funcionais

**Fluxos com IA**
- Prompts e fluxos para times de suporte e conteúdo
- Triagem e classificação de tickets

## Como eu trabalho

- **A especificação vem antes do código** — e quando a realidade discorda da
  especificação, corrige-se a especificação primeiro, o código depois.
- **Teste desde o primeiro commit**, não "depois que estabilizar": um caminho
  feliz por funcionalidade e um teste de regressão por bug, escrito antes da
  correção.
- **Nenhum segredo em arquivo versionado.** Configuração vem do ambiente.
- **Um comando documentado** para rodar a partir de um checkout limpo.

## Ferramentas

Python · TypeScript/Next.js · C# · Delphi · SQLite/PostgreSQL · FastAPI ·
Git/GitHub Actions · Vercel · Excel/Google Sheets

## Também à venda

Algumas das minhas planilhas viraram produtos acabados, vendidos como download
imediato: **[NumeraSheets na Etsy](https://numerasheets.etsy.com)** — controles
orientados a fórmula para faturas e despesas, imóveis de aluguel, taxas de
marketplace e conteúdo de redes sociais, cada um com exemplo preenchido e guia
de uso. Há também um **[site com o catálogo](https://numerasheets.com)**, com
screenshot de cada planilha.

## Contato

- E-mail: **peterwk.dev@gmail.com**
