# Boti automati crypto

Acest folder contine doua dashboard-uri HTML locale pentru monitorizare si tranzactii manuale:

- `index.html` - pagina de pornire cu link catre ambii boti.
- `beat_usdt_bot.html` - bot BEAT/USDT Perpetual Futures.
- `eth_usdc_bot.html` - bot ETH/USDC Binance Spot.

## Cum se foloseste

1. Deschide `index.html` in browser.
2. Alege botul dorit: BEAT/USDT sau ETH/USDC.
3. Apasa `ANALIZEAZA ACUM` pentru a incarca datele live.
4. Completeaza zona de tranzactie manuala daca vrei sa urmaresti o pozitie.
5. Apasa `Inchide` pe tranzactie cand vrei sa marchezi iesirea.
6. Introdu pretul de inchidere, iar pagina calculeaza automat profitul obtinut.

## Functii incluse

- Semnale BUY/SELL pe baza indicatorilor tehnici.
- Pret live si modificare 24h.
- Calcul pentru stop loss, take profit si pret de iesire pentru profit dorit.
- Lista de tranzactii manuale.
- P&L live pentru tranzactii deschise.
- Buton `Inchide` pentru marcarea tranzactiilor inchise.
- Total `Profit obtinut` in sumar.
- Pentru ETH/USDC, tranzactiile pot fi salvate local sau sincronizate cu Firebase, daca datele Firebase sunt configurate.

## Observatii

Fisierele ruleaza local in browser si nu sunt consultanta financiara. Preturile live depind de accesul la internet si de disponibilitatea API-urilor Binance si TradingView.
