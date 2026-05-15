# Data Cloud Credit Calculator - User Manual (PT/EN/ES)

Main file:

- `reports/data-cloud-credit-calculator-recurring-pdf-url.html`

---

## Portuguese (PT-BR)

### Objetivo

Esta calculadora estima o consumo de creditos de Data Cloud para cargas recorrentes, comparando tres cenarios:

- `Worst case`
- `Atual`
- `Target`

Ela permite modelar:

- cargas `full` e `delta`
- volume por execucao
- execucoes por mes
- `usage type` de cada carga
- ambiente `Sandbox` ou `Production`

### Estrutura da tela

1. **Fonte de rate card via PDF**
   - Campo para URL do PDF da Salesforce.
   - Botao para carregar rates automaticamente.
   - Botao para restaurar rates padrao.
2. **Rate card**
   - Tabela com `Production` e `Sandbox` por usage type.
3. **Resumo comparativo**
   - Totais mensais e anuais por cenario.
   - Economia do target vs atual e vs worst.
4. **Cenarios de cargas recorrentes**
   - Abas separadas para `Worst case`, `Atual` e `Target`.
5. **Detalhe por usage type**
   - Custo consolidado por tipo em cada cenario.
6. **Diagnostico**
   - Nivel de risco e recomendacoes.
7. **Exportar / importar**
   - Salva e restaura premissas via JSON.

### Como carregar usage types/rates pelo PDF (URL Salesforce)

1. Abra a secao **Fonte de rate card via PDF**.
2. Cole a URL publica do PDF de pricing da Salesforce no campo **URL do PDF**.
3. Clique em **Carregar rates da URL**.
4. Aguarde a mensagem de status:
   - sucesso: rates atualizados e quantidade de usage types encontrados
   - erro: falha HTTP, parsing ou bloqueio CORS
5. Confira a tabela **Rate card** para validar os valores carregados.

#### Observacao sobre CORS

Se a URL bloquear CORS, o navegador pode impedir a leitura do PDF. Nesse caso:

- abra o HTML por um servidor local (nao `file://`)
- use uma URL publica que permita leitura cruzada

### Como configurar idioma

No campo **Idioma**, selecione:

- `Portugues`
- `English`
- `Espanol`

A interface e as mensagens dinamicas serao atualizadas automaticamente. O idioma tambem e exportado no JSON (`language`) e volta ao importar.

### Fluxo recomendado de uso

1. Defina idioma e ambiente.
2. Carregue rates pelo PDF URL (ou mantenha rates padrao).
3. Preencha primeiro o cenario **Atual**.
4. Modele **Target** com reducoes de custo.
5. Use **Worst case** como teto de risco.
6. Compare indicadores no resumo e no detalhe por usage type.
7. Exporte JSON para versionar as hipoteses.

### Boas praticas

- nomeie cargas com padrao claro
- separe cargas `full` e `delta`
- valide unidade de volume (`1M rows processed`)
- trate `Worst case` como risco, nao baseline
- revise periodicamente quando mudar frequencia, volume ou estrategia

### Limitacoes

- o parser de PDF depende da estrutura textual do arquivo
- a calculadora nao substitui validacao contratual/comercial
- nao aplica descontos contratuais automaticamente
- nao le consumo real da org em tempo real

---

## English (EN)

### Purpose

This calculator estimates Data Cloud credit consumption for recurring loads across three scenarios:

- `Worst case`
- `Current`
- `Target`

You can model:

- `full` and `delta` loads
- volume per run
- runs per month
- load `usage type`
- `Sandbox` or `Production` environment

### Screen structure

1. **Rate card source via PDF**
   - Salesforce PDF URL input.
   - Button to load rates automatically.
   - Button to restore default rates.
2. **Rate card**
   - Table with `Production` and `Sandbox` values by usage type.
3. **Comparative summary**
   - Monthly and yearly totals by scenario.
   - Savings: target vs current, and target vs worst.
4. **Recurring load scenarios**
   - Separate tabs for `Worst case`, `Current`, and `Target`.
5. **Breakdown by usage type**
   - Consolidated cost by usage type per scenario.
6. **Diagnostics**
   - Risk level and automated recommendations.
7. **Export / import**
   - Save and restore assumptions in JSON format.

### How to load usage types/rates from Salesforce PDF URL

1. Open **Rate card source via PDF**.
2. Paste the public Salesforce pricing PDF URL into **PDF URL**.
3. Click **Load rates from URL**.
4. Check the status message:
   - success: rates updated and number of matched usage types
   - error: HTTP failure, parsing issue, or CORS block
5. Validate the loaded values in the **Rate card** table.

#### CORS note

If the PDF host blocks CORS, browser-side reading may fail. In that case:

- open the HTML through a local web server (not `file://`)
- use a public URL that allows cross-origin reads

### How to configure language

In the **Language** selector, choose:

- `Portuguese`
- `English`
- `Spanish`

UI labels and dynamic messages update immediately. Language is also saved in exported JSON (`language`) and restored on import.

### Recommended workflow

1. Set language and environment.
2. Load rates from PDF URL (or keep defaults).
3. Fill in **Current** first.
4. Build **Target** with optimization assumptions.
5. Use **Worst case** as an upper risk bound.
6. Compare summary KPIs and usage-type breakdown.
7. Export JSON to keep versioned assumptions.

### Best practices

- use clear, standardized load names
- model `full` and `delta` separately
- validate volume unit (`1M rows processed`)
- use worst case as a ceiling, not a baseline
- update assumptions whenever frequency, volume, or strategy changes

### Limitations

- PDF parsing depends on the document text structure
- calculator does not replace contractual/commercial validation
- contract discounts are not automatically applied
- no direct real-time org usage integration

---

## Espanol (ES)

### Objetivo

Esta calculadora estima el consumo de creditos de Data Cloud para cargas recurrentes en tres escenarios:

- `Worst case`
- `Actual`
- `Target`

Permite modelar:

- cargas `full` y `delta`
- volumen por ejecucion
- ejecuciones por mes
- `usage type` de cada carga
- entorno `Sandbox` o `Production`

### Estructura de la pantalla

1. **Fuente del rate card via PDF**
   - Campo para URL del PDF de Salesforce.
   - Boton para cargar rates automaticamente.
   - Boton para restaurar rates por defecto.
2. **Rate card**
   - Tabla con valores de `Production` y `Sandbox` por usage type.
3. **Resumen comparativo**
   - Totales mensuales y anuales por escenario.
   - Ahorro del target vs actual y vs worst.
4. **Escenarios de cargas recurrentes**
   - Pestanas para `Worst case`, `Actual` y `Target`.
5. **Detalle por usage type**
   - Costo consolidado por tipo en cada escenario.
6. **Diagnostico**
   - Nivel de riesgo y recomendaciones automaticas.
7. **Exportar / importar**
   - Guarda y recupera supuestos en JSON.

### Como cargar usage types/rates desde URL PDF de Salesforce

1. Abra **Fuente del rate card via PDF**.
2. Pegue la URL publica del PDF de pricing en **URL del PDF**.
3. Haga clic en **Cargar rates desde URL**.
4. Revise el mensaje de estado:
   - exito: rates actualizados y cantidad de usage types detectados
   - error: falla HTTP, parsing o bloqueo CORS
5. Valide los valores en la tabla **Rate card**.

#### Nota de CORS

Si el host del PDF bloquea CORS, la lectura desde el navegador puede fallar. En ese caso:

- abra el HTML con un servidor local (no `file://`)
- use una URL publica con permiso de lectura cruzada

### Como configurar idioma

En el selector **Idioma**, elija:

- `Portugues`
- `English`
- `Espanol`

La interfaz y los mensajes dinamicos se actualizan al instante. El idioma tambien se guarda en el JSON exportado (`language`) y se recupera al importar.

### Flujo recomendado

1. Defina idioma y entorno.
2. Cargue rates por URL del PDF (o mantenga los valores por defecto).
3. Complete primero el escenario **Actual**.
4. Modele **Target** con supuestos de optimizacion.
5. Use **Worst case** como techo de riesgo.
6. Compare KPIs en resumen y detalle por usage type.
7. Exporte JSON para versionar supuestos.

### Buenas practicas

- use nombres de carga claros y consistentes
- modele `full` y `delta` por separado
- valide la unidad de volumen (`1M rows processed`)
- use `Worst case` como techo, no como baseline
- actualice supuestos ante cambios de frecuencia, volumen o estrategia

### Limitaciones

- el parser de PDF depende de la estructura de texto del documento
- no reemplaza validacion contractual/comercial
- no aplica descuentos contractuales de forma automatica
- no integra consumo real de la org en tiempo real

# Manual de uso — calculadora de créditos de Data Cloud

Arquivo principal:

- `reports/data-cloud-credit-calculator-recurring.html`

## Objetivo

Esta calculadora foi feita para estimar consumo de créditos de Data Cloud em cenários de cargas recorrentes.

Ela permite modelar:

- cargas `full`
- cargas `delta`
- volume por execução
- número de execuções por mês
- `usage type` de cada carga
- comparação entre três cenários:
  - `worst case`
  - `actual`
  - `target`

## O que a calculadora considera

A calculadora usa como base a rate card do arquivo:

- `reports/New-Nov25-DataCloud-PlatformServices.pdf`

Com seletor de ambiente:

- `Sandbox`
- `Production`

Os cálculos usam os `usage types` da rate card, por exemplo:

- `External Data Pipeline - Batch`
- `External Data Pipeline - Streaming`
- `Data Transforms - Batch`
- `Calculated Insights - Batch`
- `Data Queries`
- `Segment Rows Processed`
- `Profile Unification`

## Estrutura da tela

### 1. Rate card

Na parte superior esquerda, você escolhe o ambiente:

- `Sandbox`
- `Production`

Isso troca automaticamente os multiplicadores de crédito.

### 2. Resumo comparativo

Na parte superior direita, aparecem os indicadores principais:

- custo mensal por cenário
- custo anual por cenário
- economia do `target` versus `actual`
- economia do `target` versus `worst case`
- razão `target / actual`

### 3. Escenarios de cargas recorrentes

Cada cenário tem sua própria aba:

- `Worst case`
- `Actual`
- `Target`

Dentro de cada aba, você pode cadastrar múltiplas cargas.

Cada linha tem:

- `Carga`: nome descritivo
- `Usage type`: tipo de uso da rate card
- `Modo`: `full` ou `delta`
- `Volumen por ejecución`
- `Ejecuciones / mes`

A tabela calcula automaticamente:

- `Volumen mensual`
- `Créditos / mes`

### 4. Detalle por usage type

Mostra o custo consolidado por tipo de uso em:

- `Worst`
- `Actual`
- `Target`
- delta do `target` vs `actual`

### 5. Diagnóstico

Mostra:

- risco do `worst`
- risco do `actual`
- risco do `target`
- recomendações automáticas com base no mix full/delta e nos drivers de custo

### 6. Exportar / importar

Você pode:

- exportar o cenário atual como JSON
- importar um JSON previamente salvo

Isso permite guardar hipóteses de planejamento sem usar banco de dados.

## Como usar

### Passo 1. Escolha o ambiente

Selecione:

- `Sandbox` para estimativas de sandbox
- `Production` para estimativas produtivas

### Passo 2. Escolha a aba do cenário

Preencha primeiro:

- `Actual`

Depois:

- `Target`

E opcionalmente:

- `Worst case`

O `worst case` serve para modelar teto de risco ou pico operacional.

### Passo 3. Cadastre as cargas

Para cada carga recorrente:

1. clique em `Agregar carga`
2. dê um nome para a carga
3. escolha o `usage type`
4. defina se é `full` ou `delta`
5. informe o volume por execução
6. informe quantas vezes roda no mês

### Passo 4. Compare os resultados

Observe principalmente:

- `Ahorro mensual vs actual`
- `Ahorro mensual vs worst`
- `Ratio target / actual`

Interpretação rápida:

- se `target` < `actual`, há economia
- se o `ratio target / actual` for menor que `1.00x`, o cenário alvo custa menos que o atual
- quanto menor esse ratio, maior a redução relativa

## Regras práticas de modelagem

### Quando usar `full`

Use `full` quando a carga:

- reprocessa tudo
- substitui integralmente o conjunto
- representa um refresh completo

Exemplos:

- carga mensal de cadastro completo
- rebuild integral de snapshot
- recálculo completo de dataset servido

### Quando usar `delta`

Use `delta` quando a carga:

- traz apenas novos ou alterados
- usa watermark
- carrega incrementalmente

Exemplos:

- delta diário de clientes
- delta por `updated_at`
- ingestion de eventos novos

## Exemplos de comparação

## Exemplo 1 — full mensal vs delta diário

### Cenário atual

- `Clientes full externo`
  - `External Data Pipeline - Batch`
  - `full`
  - volume: `25`
  - execuções/mês: `12`

- `Transform principal`
  - `Data Transforms - Batch`
  - `delta`
  - volume: `42`
  - execuções/mês: `30`

### Cenário target

- `Full refresh controlado`
  - `External Data Pipeline - Batch`
  - `full`
  - volume: `5`
  - execuções/mês: `4`

- `Delta diario optimizado`
  - `External Data Pipeline - Batch`
  - `delta`
  - volume: `1.4`
  - execuções/mês: `30`

- `Transform reducido`
  - `Data Transforms - Batch`
  - `delta`
  - volume: `18`
  - execuções/mês: `20`

### O que observar

- queda do volume `full`
- eventual aumento do volume `delta`
- redução do custo total de `External Data Pipeline - Batch`
- redução do custo de `Data Transforms - Batch`

### Interpretação esperada

Se o `target` for bem modelado, ele deve:

- reduzir o custo mensal
- reduzir a exposição a refresh completo
- melhorar o `ratio target / actual`

## Exemplo 2 — Query API serving otimizado

### Cenário atual

- `Query API serving`
  - `Data Queries`
  - `delta`
  - volume: `320`
  - execuções/mês: `1`

### Cenário target

- `Query API optimizada`
  - `Data Queries`
  - `delta`
  - volume: `140`
  - execuções/mês: `1`

### O que observar

- redução da linha `Data Queries`
- impacto direto no resumo mensal

### Interpretação esperada

Se o serving estiver mais materializado e com menos scan, o `target` deve cair mesmo sem mexer em ingestão ou identity.

## Exemplo 3 — pior caso operacional

### Cenário worst case

- `Clientes full externo`
  - `External Data Pipeline - Batch`
  - `full`
  - volume: `40`
  - execuções/mês: `20`

- `Calculated Insights batch`
  - `Calculated Insights - Batch`
  - `delta`
  - volume: `110`
  - execuções/mês: `8`

- `Segmentación intensiva`
  - `Segment Rows Processed`
  - `delta`
  - volume: `300`
  - execuções/mês: `1`

### O que observar

- teto de consumo
- sensibilidade do ambiente a campanhas ou janelas de pico
- distância entre `target` e `worst`

### Interpretação esperada

Esse cenário não é para meta de operação normal. Ele serve para:

- prever risco
- estimar budget máximo
- justificar otimizações preventivas

## Como interpretar o diagnóstico

A seção `Diagnóstico` dá pistas rápidas:

- se o full domina, a maior alavanca costuma ser migrar para delta
- se `Data Transforms` domina, revise cardinalidade, filtros e materializações
- se `Data Queries` domina, reduza scans e prefira DMO serving

## Salvando cenários

Sem usar banco de dados, há duas formas simples:

### 1. Exportar JSON

Clique em:

- `Exportar JSON`

Depois copie o conteúdo e guarde em:

- arquivo `.json`
- documento interno
- ticket

### 2. Importar JSON

Cole um JSON salvo anteriormente na caixa `JSON` e clique em:

- `Importar JSON`

## Boas práticas

- mantenha nomes de carga claros e padronizados
- modele `full` e `delta` separadamente
- use o `worst case` como teto, não como baseline
- compare sempre `target` vs `actual`
- atualize o cenário quando mudar:
  - frequência
  - volume por execução
  - estratégia de refresh
  - padrão de serving/query

## Limitações

- a calculadora depende da interpretação correta do volume na unidade da rate card
- não substitui validação contratual/comercial
- não conhece automaticamente o consumo real da org
- não aplica descontos comerciais nem créditos incluídos no contrato

## Uso recomendado com os relatórios deste projeto

Você pode usar esta calculadora junto com:

- `reports/data-stream-refresh-action-checklist.md`
- `reports/data-stream-refresh-cost-review.csv`
- `reports/dlo_full_qualified_keys_audit.md`
- `reports/DT_Clientes_Reglas.json`

Assim, o cenário pode refletir:

- otimização de refresh dos Data Streams
- redução de custo em transforms
- redução de leitura por Query API
- mudanças em serving materializado
