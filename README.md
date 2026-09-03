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

A public-data observatory for Brazil's Northeast: population, GDP and GDP per
capita for all **1,794 municipalities**, ingested straight from the official
**IBGE APIs**. No hand-typed numbers anywhere in the project.

- **Pipeline:** Python ingestion → SQLite → static JSON snapshot → Next.js
  static export. No server to keep alive, no database in production.
- **Every figure carries its source and collection date.** A `conferir` command
  cross-checks the sum of all municipalities against IBGE's own regional
  aggregate before anything is published — and reports the difference instead of
  hiding it.
- **Weekly GitHub Actions job** re-ingests, verifies, and commits only when the
  data actually changed.
- **One page per municipality** — 1,794 of them, each with its own title,
  description and canonical, joining IBGE data to the fiscal figures by the
  shared IBGE code. A single indexable URL became 1,794.
- **55 automated tests**, including a cross-language contract test that fails if
  the Python export and the TypeScript types ever drift apart.

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

### Painel Fiscal do Nordeste

**[Source](https://github.com/peterwkdev-creator/painel-fiscal-ne)** · AGPL-3.0

Brazil's Fiscal Responsibility Law caps municipal personnel spending at **54%**
of net revenue, with a **51.3%** threshold that already forbids hiring. The data
is public, but it arrives one municipality per request, 200+ chart-of-accounts
lines at a time. In practice nobody looks.

The complete Northeast sweep: **1,793 municipalities, 1,414 filed, 379 did not.**

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

## Practice repos

Small single-purpose repos, built while learning a stack or testing an idea.
They are demos, not production systems — the featured project above is where the
real engineering is.

<details>
<summary><b>Backend &amp; automation</b></summary>

- **REST API from scratch (FastAPI)** — [sample-fastapi-inventory-api](https://github.com/peterwkdev-creator/sample-fastapi-inventory-api)
- **API-to-API integration/sync** — [sample-api-integration-sync](https://github.com/peterwkdev-creator/sample-api-integration-sync)
- **PDF invoice generation from CSV** — [sample-pdf-invoice-generator](https://github.com/peterwkdev-creator/sample-pdf-invoice-generator)
- **Receipt OCR → spreadsheet (script)** — [sample-ocr-receipt-to-spreadsheet](https://github.com/peterwkdev-creator/sample-ocr-receipt-to-spreadsheet)
- **Competitor price scraping (script)** — [sample-web-scraping-price-tracker](https://github.com/peterwkdev-creator/sample-web-scraping-price-tracker)
- **Customer feedback router (n8n + Claude)** — [sample-n8n-feedback-router](https://github.com/peterwkdev-creator/sample-n8n-feedback-router)

</details>

<details>
<summary><b>Web apps</b></summary>

- **Competitor price watch** — [sample-price-comparison-webapp](https://github.com/peterwkdev-creator/sample-price-comparison-webapp) · [live demo](https://sample-price-comparison-webapp.vercel.app)
- **Receipt OCR scanner** — [sample-ocr-receipt-webapp](https://github.com/peterwkdev-creator/sample-ocr-receipt-webapp) · [live demo](https://sample-ocr-receipt-webapp.vercel.app)
- **AI ticket triage** — [sample-ai-ticket-triage-webapp](https://github.com/peterwkdev-creator/sample-ai-ticket-triage-webapp) · [live demo](https://sample-ai-ticket-triage-webapp.vercel.app)

</details>

<details>
<summary><b>AI &amp; data</b></summary>

- **AI prompt pack (customer support)** — [sample-ai-prompt-pack-support](https://github.com/peterwkdev-creator/sample-ai-prompt-pack-support)
- **AI ticket triage (script)** — [sample-ai-support-triage](https://github.com/peterwkdev-creator/sample-ai-support-triage)
- **Text labeling / inter-annotator agreement** — [sample-data-annotation-text-labeling](https://github.com/peterwkdev-creator/sample-data-annotation-text-labeling)

</details>

<details>
<summary><b>Spreadsheets, documents and content</b></summary>

I also take on spreadsheet, document, translation and writing work.

- **Financial dashboard (Excel)** — [sample-financial-dashboard-spreadsheet](https://github.com/peterwkdev-creator/sample-financial-dashboard-spreadsheet)
- **Expense & invoice tracker (Excel)** — [sample-freelancer-expense-invoice-tracker](https://github.com/peterwkdev-creator/sample-freelancer-expense-invoice-tracker)
- **Content calendar (Google Sheets)** — [sample-google-sheets-content-calendar](https://github.com/peterwkdev-creator/sample-google-sheets-content-calendar)
- **Resume & LinkedIn rewrite** — [sample-resume-linkedin](https://github.com/peterwkdev-creator/sample-resume-linkedin)
- **Translation (PT ↔ EN)** — [sample-translation-pt-en](https://github.com/peterwkdev-creator/sample-translation-pt-en)
- **Proofreading & copy editing** — [sample-proofreading-editing](https://github.com/peterwkdev-creator/sample-proofreading-editing)
- **Content writing** — [sample-content-writing](https://github.com/peterwkdev-creator/sample-content-writing)
- **Static landing page** — [sample-landing-page-static](https://github.com/peterwkdev-creator/sample-landing-page-static)
- **Social media template kit** — [sample-social-media-template-kit](https://github.com/peterwkdev-creator/sample-social-media-template-kit)
- **Data cleaning automation** — [sample-automation-workflow](https://github.com/peterwkdev-creator/sample-automation-workflow)

</details>

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

Observatório de dados públicos do Nordeste: população, PIB e PIB per capita dos
**1.794 municípios** da região, ingeridos direto das **APIs oficiais do IBGE**.
Nenhum número digitado à mão em lugar nenhum do projeto.

- **Pipeline:** ingestão em Python → SQLite → snapshot JSON estático → export
  estático do Next.js. Nenhum servidor para manter de pé, nenhum banco em produção.
- **Todo número carrega a fonte e a data de coleta.** Um comando `conferir`
  cruza a soma dos municípios com o agregado regional do próprio IBGE antes de
  qualquer publicação — e **relata** a diferença em vez de escondê-la.
- **Rotina semanal no GitHub Actions** que reingere, confere e só commita quando
  o dado realmente mudou.
- **Uma página por município** — 1.794 delas, cada uma com título, descrição e
  canonical próprios, unindo o dado do IBGE ao fiscal pela chave do código
  IBGE. Uma única URL indexável virou 1.794.
- **55 testes automatizados**, incluindo um teste de contrato entre linguagens
  que falha se o export em Python e os tipos em TypeScript se afastarem.

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

### Painel Fiscal do Nordeste

**[Código](https://github.com/peterwkdev-creator/painel-fiscal-ne)** · AGPL-3.0

A Lei de Responsabilidade Fiscal limita a despesa municipal com pessoal a
**54%** da receita, com um limite prudencial de **51,3%** que já proíbe
contratar. O dado é público, mas sai **um município por requisição**, em 200+
linhas de plano de contas por consulta. Na prática, ninguém olha.

A varredura completa do Nordeste: **1.793 municípios, 1.414 entregaram, 379 não.**

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

## Repositórios de prática

Repositórios pequenos, de propósito único, feitos para aprender uma stack ou
testar uma ideia. São demonstrações, não sistemas de produção — a engenharia de
verdade está no projeto em destaque acima.

<details>
<summary><b>Backend e automação</b></summary>

- **API REST do zero (FastAPI)** — [sample-fastapi-inventory-api](https://github.com/peterwkdev-creator/sample-fastapi-inventory-api)
- **Integração/sincronização entre APIs** — [sample-api-integration-sync](https://github.com/peterwkdev-creator/sample-api-integration-sync)
- **Geração de fatura em PDF a partir de CSV** — [sample-pdf-invoice-generator](https://github.com/peterwkdev-creator/sample-pdf-invoice-generator)
- **OCR de recibos → planilha (script)** — [sample-ocr-receipt-to-spreadsheet](https://github.com/peterwkdev-creator/sample-ocr-receipt-to-spreadsheet)
- **Scraping de preço de concorrentes (script)** — [sample-web-scraping-price-tracker](https://github.com/peterwkdev-creator/sample-web-scraping-price-tracker)
- **Roteador de feedback de clientes (n8n + Claude)** — [sample-n8n-feedback-router](https://github.com/peterwkdev-creator/sample-n8n-feedback-router)

</details>

<details>
<summary><b>Web apps</b></summary>

- **Monitor de preço de concorrentes** — [sample-price-comparison-webapp](https://github.com/peterwkdev-creator/sample-price-comparison-webapp) · [demo ao vivo](https://sample-price-comparison-webapp.vercel.app)
- **Leitor de recibos com OCR** — [sample-ocr-receipt-webapp](https://github.com/peterwkdev-creator/sample-ocr-receipt-webapp) · [demo ao vivo](https://sample-ocr-receipt-webapp.vercel.app)
- **Triagem de tickets com IA** — [sample-ai-ticket-triage-webapp](https://github.com/peterwkdev-creator/sample-ai-ticket-triage-webapp) · [demo ao vivo](https://sample-ai-ticket-triage-webapp.vercel.app)

</details>

<details>
<summary><b>IA e dados</b></summary>

- **Pacote de prompts de IA (atendimento)** — [sample-ai-prompt-pack-support](https://github.com/peterwkdev-creator/sample-ai-prompt-pack-support)
- **Triagem de tickets com IA (script)** — [sample-ai-support-triage](https://github.com/peterwkdev-creator/sample-ai-support-triage)
- **Rotulagem de texto / concordância entre anotadores** — [sample-data-annotation-text-labeling](https://github.com/peterwkdev-creator/sample-data-annotation-text-labeling)

</details>

<details>
<summary><b>Planilhas, documentos e conteúdo</b></summary>

Também atendo trabalho de planilha, documento, tradução e redação.

- **Dashboard financeiro (Excel)** — [sample-financial-dashboard-spreadsheet](https://github.com/peterwkdev-creator/sample-financial-dashboard-spreadsheet)
- **Controle de despesas e faturas (Excel)** — [sample-freelancer-expense-invoice-tracker](https://github.com/peterwkdev-creator/sample-freelancer-expense-invoice-tracker)
- **Calendário de conteúdo (Google Sheets)** — [sample-google-sheets-content-calendar](https://github.com/peterwkdev-creator/sample-google-sheets-content-calendar)
- **Reescrita de currículo e LinkedIn** — [sample-resume-linkedin](https://github.com/peterwkdev-creator/sample-resume-linkedin)
- **Tradução (PT ↔ EN)** — [sample-translation-pt-en](https://github.com/peterwkdev-creator/sample-translation-pt-en)
- **Revisão e copidesque** — [sample-proofreading-editing](https://github.com/peterwkdev-creator/sample-proofreading-editing)
- **Redação de conteúdo** — [sample-content-writing](https://github.com/peterwkdev-creator/sample-content-writing)
- **Landing page estática** — [sample-landing-page-static](https://github.com/peterwkdev-creator/sample-landing-page-static)
- **Kit de templates para redes sociais** — [sample-social-media-template-kit](https://github.com/peterwkdev-creator/sample-social-media-template-kit)
- **Automação de limpeza de dados** — [sample-automation-workflow](https://github.com/peterwkdev-creator/sample-automation-workflow)

</details>

## Contato

- E-mail: **peterwk.dev@gmail.com**
