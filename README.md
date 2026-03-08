# MoonBoard BLE Test (POC)

Minimal test-side til at validere:
- Kan telefonen forbinde til en BLE-enhed?
- Kan appen sende LED-kommandoer?

## Hvad du får

- `index.html` med knapper til:
  - `Connect BLE`
  - `Send LED ON`
  - `Send LED OFF`
  - `Send PULSE`
  - `Send Custom`
  - `Load Problems` + problemvælger + `Top Problem (LED show)`
- UUID-felter så du kan skifte service/characteristic uden at kode om.
- Auto-discovery af writable BLE characteristic, hvis de indtastede UUID'er er forkerte.
- `problems.sample.json` med 20 lokale testproblemer.

## Kør lokalt

Web Bluetooth kræver en sikker kontekst:
- `https://` eller
- `http://localhost`

Start en lokal server:

```bash
python3 -m http.server 8080
```

Åbn derefter:
- På samme maskine: `http://localhost:8080`
- På telefon: brug HTTPS-tunnel (fx ngrok) eller test direkte i en Android-browser der tillader dit setup.

## Vigtigt om mobil-support

- Android + Chrome: virker typisk.
- iPhone Safari/PWA: Web Bluetooth er normalt ikke understøttet.

Hvis iPhone er et krav, er næste skridt typisk en native app (React Native/Swift) eller en lokal gateway/controller.

## Kommandoformat

Eksempelknapper sender ASCII:
- `LED:ON`
- `LED:OFF`
- `LED:PULSE`

Juster formatet til det din BLE-modtager forventer.

## Hurtig test-flow

1. Start med `Scan all BLE devices` slået til.
2. Indtast korrekt `Service UUID` og `Write Characteristic UUID`.
3. Tryk `Connect BLE`.
4. Tryk `Load Problems` og vælg et problem.
5. Tryk `Show Problem LEDs` eller `Top Problem (LED show)`.
6. Tjek at LED reagerer.
7. Prøv disconnect/reconnect 10+ gange og noter fejl.

Hvis enheden stadig ikke dukker op, er den ofte enten ikke BLE, eller også mangler browseren tilladelser til `Nearby devices` og `Location`.
Hvis du får en "no services found"-fejl, er enheden typisk ikke eksponeret som BLE GATT til Web Bluetooth, eller også er de nødvendige services ikke tilladt.
# Moonboard-BLE-test
