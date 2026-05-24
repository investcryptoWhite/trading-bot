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

## Integrare Firebase

Botii au deja codul Firebase inclus. Trebuie doar inlocuita configuratia `FB_CONFIG` din fiecare fisier HTML.

1. Intra in Firebase Console: https://console.firebase.google.com/
2. Creeaza un proiect nou sau deschide proiectul tau existent.
3. Adauga o aplicatie Web din `Project settings` > `Your apps` > `Web app`.
4. Copiaza obiectul `firebaseConfig`.
5. Inlocuieste valorile din `FB_CONFIG` in:
   - `beat_usdt_bot.html`
   - `eth_usdc_bot.html`
6. Activeaza Authentication > Sign-in method > Google.
7. Activeaza Firestore Database.
8. Publica fisierele prin Firebase Hosting sau deschide-le local pentru test.

Colectiile folosite sunt:

- `trades_beat/{uid}/items` pentru BEAT/USDT.
- `trades_eth/{uid}/items` pentru ETH/USDC.

Reguli Firestore recomandate pentru inceput:

```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /trades_beat/{userId}/items/{tradeId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    match /trades_eth/{userId}/items/{tradeId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Stergerea fisierelor vechi

Pastreaza fisierele curente:

- `index.html`
- `README.md`
- `beat_usdt_bot.html`
- `eth_usdc_bot.html`

Sterge doar arhivele sau copiile mai vechi dupa ce verifici ca botii se deschid corect din `index.html`.
