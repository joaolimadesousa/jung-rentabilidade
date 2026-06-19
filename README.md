# JUNG · Mapa de Rentabilidade

Aplicação web que replica o ficheiro *"Tabela 2026 – análise de rentabilidade negócio"*.

Introduz referências JUNG e quantidades e a app calcula preços e margens para os vários compradores (Instalador, Distribuidor, Rappel) em 4 modos de cálculo.

## Funcionalidades

- **Entrada estilo Excel**: Artigo + Quantidade por linha. PG, PVP e custo vêm do catálogo (14.681 artigos).
- **4 modos de cálculo**:
  - **Normal** — `PVP × (1 − desconto)` direto.
  - **Normal c/ extra** — aplica desconto extra de instalador e distribuidor.
  - **GM** — parte do custo: `dist = custo / (1 − GM JUNG)`, `inst = dist / (1 − GM dist)`.
  - **GM esp** — como GM, mas artigos com preço especial usam PU especial com margem JUNG de 50%.
- **Margens** Instalador / Distribuidor / Rappel, com código de cores.
- **Resumo por PG** e **tabela de descontos editável** (recalcula ao vivo).
- **Exportação CSV**.
- Acesso protegido por password.

> Validado contra o Excel original: diferença máxima **0,00 €** nos 4 modos.

## Tecnologia

- HTML/CSS/JS estático (sem build).
- Dados: Supabase (projeto `gmowqbsmpsrercgxyjuy`), tabelas `rent_artigos`, `rent_descontos`, `rent_especiais`.
- Deploy: Vercel (site estático).

## Configuração

A password de acesso está em `index.html` na constante `PASSWORD` (predefinição: `jung2026`).

A chave Supabase usada é a *anon key* (apenas leitura do catálogo + escrita na tabela de descontos via RLS).
