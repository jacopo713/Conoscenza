---

# === METADATA CORE ===

type: trading-news date: <% tp.date.now("YYYY-MM-DD") %> created: <% tp.date.now("YYYY-MM-DDTHH:mm:ss") %> modified: <% tp.date.now("YYYY-MM-DDTHH:mm:ss") %>

# === CURRENCY CONTEXT ===

currency_primary: <% await tp.system.suggester(["USD", "EUR", "GBP", "JPY", "CHF", "AUD", "CAD", "NZD", "XAU", "XAG"], ["USD", "EUR", "GBP", "JPY", "CHF", "AUD", "CAD", "NZD", "XAU", "XAG"], false, "Valuta principale") %> currency_secondary: <% await tp.system.suggester(["USD", "EUR", "GBP", "JPY", "CHF", "AUD", "CAD", "NZD", "XAU", "XAG", "none"], ["USD", "EUR", "GBP", "JPY", "CHF", "AUD", "CAD", "NZD", "XAU", "XAG", "none"], false, "Valuta secondaria (opzionale)") %> pair: <% await tp.system.prompt("Pair specifico (es. XAUUSD, EURUSD) - lascia vuoto se non applicabile", "") %>

# === MARKET SESSION ===

session: <% await tp.system.suggester(["asian", "london", "new-york", "overlap-london-ny", "all-day"], ["asian", "london", "new-york", "overlap-london-ny", "all-day"], false, "Sessione di mercato") %>

# === NEWS CLASSIFICATION ===

news_impact: <% await tp.system.suggester(["high", "medium", "low"], ["high", "medium", "low"], false, "Impatto previsto") %> news_type: <% await tp.system.suggester(["economic-data", "central-bank", "geopolitical", "earnings", "sentiment", "technical", "other"], ["economic-data", "central-bank", "geopolitical", "earnings", "sentiment", "technical", "other"], false, "Tipo di notizia") %> news_source: <% await tp.system.prompt("Fonte (es. Fed, ECB, BLS, Reuters)", "") %>

# === MARKET REACTION (compilare dopo) ===

actual_reaction: direction: # bullish | bearish | neutral magnitude: # strong | moderate | weak duration: # immediate | sustained | reversed price_move_pips:

# === SEMANTIC TAGS ===

tags:

- trading/news
- currency/<% await tp.system.suggester(["USD", "EUR", "GBP", "JPY", "CHF", "AUD", "CAD", "NZD", "XAU", "XAG"], ["USD", "EUR", "GBP", "JPY", "CHF", "AUD", "CAD", "NZD", "XAU", "XAG"], false, "Tag valuta") %>
- impact/<% await tp.system.suggester(["high", "medium", "low"], ["high", "medium", "low"], false, "Tag impatto") %>
- type/<% await tp.system.suggester(["economic-data", "central-bank", "geopolitical", "earnings", "sentiment"], ["economic-data", "central-bank", "geopolitical", "earnings", "sentiment"], false, "Tag tipo") %>

# === LLM ANALYSIS HINTS ===

## llm_context: analyzable: true confidence_level: # high | medium | low - da compilare pattern_category: # per clustering futuro related_events: [] # link ad altre note correlate

# 📰 News: <% await tp.system.prompt("Titolo breve della notizia", "") %>

## 📋 Sommario Evento

|Campo|Valore|
|---|---|
|**Data/Ora UTC**|<% tp.date.now("YYYY-MM-DD HH:mm") %> UTC|
|**Valuta**|{{currency_primary}}|
|**Tipo**|{{news_type}}|
|**Impatto Atteso**|{{news_impact}}|
|**Fonte**|{{news_source}}|

## 📊 Dati Economici

> [!info] Compilare se applicabile (release di dati)

|Metrica|Previous|Forecast|Actual|
|---|---|---|---|
|<% await tp.system.prompt("Nome metrica (es. NFP, CPI, GDP)", "Metrica") %>||||

## 📝 Descrizione Evento

<% await tp.system.prompt("Descrizione dettagliata della notizia/evento", "Descrivi l'evento...") %>

## 🎯 Aspettative Pre-News

### Sentiment di Mercato

- **Consensus:**
- **Posizionamento:**
- **Volatilità implicita:**

### Scenari Previsti

1. **Bullish scenario:**
2. **Bearish scenario:**
3. **Neutral scenario:**

## 📈 Reazione di Mercato (Post-Event)

> [!warning] Compilare DOPO l'evento

### Price Action

- **Direzione iniziale:**
- **Range immediato (15min):**
- **Range esteso (1h):**
- **Livelli chiave testati:**

### Volume Analysis

- **Volume spike:**
- **Delta (buy vs sell):**

## 🧠 Analisi e Takeaways

### Pattern Riconosciuto

<!-- Utile per training pattern recognition -->

### Lezioni Apprese

<!-- Per future reference -->

### Correlazioni Osservate

<!-- Link con altre asset class o valute -->

## 🔗 Collegamenti

### Note Correlate

### Fonti Esterne

---

## 📊 LLM Analysis Block

```yaml
# Blocco strutturato per parsing LLM
event_summary:
  headline: ""
  currency_affected: []
  market_impact_score: # 1-10
  predictability_score: # 1-10
  
price_action_summary:
  pre_event_bias: # bullish | bearish | neutral
  post_event_direction: # bullish | bearish | neutral  
  expectation_vs_reality: # as-expected | surprise-bullish | surprise-bearish
  
trading_implications:
  short_term: ""
  medium_term: ""
  key_levels: []
  
metadata:
  analyst: "Jacopo"
  review_date: 
  confidence: # 1-5
```

---

_Template v1.0 - Trading News Archive_