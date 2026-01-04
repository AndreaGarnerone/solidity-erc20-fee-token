# TokenMagico ERC20

**TokenMagico** è un token ERC20 scritto in Solidity che estende l’implementazione di OpenZeppelin aggiungendo una tassa sulle transazioni, una tesoreria dedicata e la possibilità di mettere in pausa tutti i trasferimenti.

Il progetto nasce come esercizio pratico e dimostrativo per esplorare pattern comuni nello sviluppo di smart contract su Ethereum.

---

## Caratteristiche principali

- Standard **ERC20** basato su OpenZeppelin
- Tassa configurabile sulle transazioni (0–100%)
- Tesoreria che riceve automaticamente le fee
- Esenzione dalla fee per indirizzi selezionati
- Possibilità di **pausare** e **riattivare** tutti i trasferimenti
- Controllo completo tramite **Ownable**
- Eventi per tutte le operazioni amministrative rilevanti

---

## Logica della fee

Durante un trasferimento:

- Se `taxFee == 0`, il trasferimento avviene normalmente
- Se il mittente o il destinatario sono esenti, **nessuna fee viene applicata**
- Altrimenti:
  - una percentuale dell’importo viene inviata alla tesoreria
  - il resto arriva al destinatario

La fee è espressa come percentuale intera (`0–100`).

---

## Ruoli speciali

- **Owner**
  - Può modificare la fee
  - Può cambiare la tesoreria
  - Può impostare esenzioni
  - Può mettere in pausa il contratto

- **Treasury**
  - Riceve automaticamente le fee
  - È esente dalla tassa
