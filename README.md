# 🤖 Crypto Trading Signal Bots

Boturi de semnale crypto cu 7 indicatori tehnici, P&L live și notificări push.

**🔗 Link rapid:** https://investcryptowhite.github.io/trading-bot/

---

## 📊 Boturi disponibile

| Pereche | Exchange | Tip | Link |
|---------|----------|-----|------|
| ETH/USDC | Binance Spot | Live | [eth_usdc_bot.html](https://investcryptowhite.github.io/trading-bot/eth_usdc_bot.html) |
| BEAT/USDT | Binance Futures | Perpetual | [beat_usdt_bot.html](https://investcryptowhite.github.io/trading-bot/beat_usdt_bot.html) |

---

## 📈 Indicatori tehnici (7/7)

| # | Indicator | Semnale generate |
|---|-----------|-----------------|
| 1 | **MACD** | Crossover linie + histogramă |
| 2 | **Stochastic RSI** | Zone supracumpărate / supravândute |
| 3 | **Volume** | Confirmare față de media 20 lumânări |
| 4 | **RSI (14)** | Sub 30 = BUY · Peste 70 = SELL |
| 5 | **Bollinger Bands (20, 2σ)** | Preț față de benzi |
| 6 | **Momentum / ROC (10)** | Viteza și accelerarea prețului |
| 7 | **EMA 9** | Filtru trend pe termen scurt |

**Prag semnal:** implicit 5/7 indicatori (configurabil între 1–7)

---

## ⚙️ Funcționalități complete

### 📊 P&L Live — Tranzacție deschisă *(NOU)*
- Introduci manual: **data intrării**, **USD investiți**, **leverage**, **preț achiziție**, **tip poziție** (LONG/SHORT)
- Calculează automat **P&L în $ și %** la prețul curent din piață
- Suportă **multiple tranzacții simultane** cu sumar total
- Date salvate în **localStorage** — persistente chiar dacă închizi browserul
- Se actualizează la fiecare refresh al botului

### 🎯 Calculator tranzacție
- Preț intrare manual sau din semnal
- Leverage configurabil (1×–125×)
- Capital investit + profit dorit → preț de ieșire automat
- Preț de lichidare estimat

### 🔔 Notificări ntfy
- Trimite notificări push pe telefon la fiecare semnal BUY/SELL
- Fără cont, fără abonament — gratuit
- Metodă: form POST invizibil (ocolește blocajele din browser)

### ⚡ Auto-refresh
Dropdown configurabil: 30s · 1m · 2m · 5m · 10m · 15m · 30m · 1h · 4h

### 📉 Grafice
- **Mini chart** intern: prețuri + EMA9 (auriu) + Bollinger Bands (violet) + timestamps
- **TradingView** embed interactiv cu RSI, MACD, BB
- Buton "Deschide cu linii →" pentru graficul complet în tab nou

---

## 🔔 Configurare ntfy

1. Instalează **ntfy** pe telefon ([Android](https://play.google.com/store/apps/details?id=io.heckel.ntfy) / [iOS](https://apps.apple.com/app/ntfy/id1625396347))
2. Creează un topic secret (ex: `beatbot-misa-1305`) — **case-sensitive!**
3. Abonează-te la topic în aplicație
4. Introdu topicul în câmpul **ntfy Topic** din bot
5. Primești notificări la fiecare semnal BUY/SELL

---

## 🚀 Instalare locală (opțional)

```bash
git clone https://github.com/investcryptoWhite/trading-bot
cd trading-bot
python -m http.server 8080
# Deschide http://localhost:8080
```

> ⚠ Nu deschide fișierele direct cu `file://` — CORS blochează API-urile Binance. Folosește un server local.

---

## 🤖 GitHub Actions — Notificări 24/7

Scriptul `bot.py` + workflow-ul `.github/workflows/bot.yml` rulează automat la fiecare 15 minute și trimite notificări ntfy fără să fie nevoie ca browserul să fie deschis.

**Configurare secrets** (Settings → Secrets):
- `NTFY_TOPIC_ETH` — topicul pentru ETH
- `NTFY_TOPIC_BEAT` — topicul pentru BEAT

**Configurare variables** (Settings → Variables):
| Variabilă | Valoare implicită | Descriere |
|-----------|-------------------|-----------|
| `INTERVAL` | `1h` | Interval lumânări |
| `SIGNAL_THRESHOLD` | `4` | Prag semnale (din 7) |
| `SL_PCT` | `2.0` | Stop Loss % |
| `TP_PCT` | `4.0` | Take Profit % |
| `LEVERAGE` | `1` | Leverage |
| `CAPITAL` | `100` | Capital USDT |

---

## 📁 Fișiere repository

```
trading-bot/
├── index.html              # Pagina principală cu prețuri live
├── eth_usdc_bot.html       # Bot ETH/USDC (Binance Spot)
├── beat_usdt_bot.html      # Bot BEAT/USDT (Binance Futures Perpetual)
├── bot.py                  # Script Python pentru GitHub Actions
├── README.md               # Documentație
└── .github/
    └── workflows/
        └── bot.yml         # Workflow GitHub Actions (cron 15min)
```

---

## ⚠️ Disclaimer

Boturile generează **semnale informative** bazate pe indicatori tehnici.
**Nu execută tranzacții automat** și **nu constituie consiliere financiară.**
Tranzacționarea crypto implică riscuri semnificative. Folosești pe propria răspundere.

---

*Date preluate de pe Binance API (read-only, fără cheie API necesară)*
