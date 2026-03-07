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
- UUID-felter så du kan skifte service/characteristic uden at kode om.

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

1. Indtast korrekt `Service UUID` og `Write Characteristic UUID`.
2. Tryk `Connect BLE`.
3. Send `LED:ON`.
4. Tjek at LED reagerer.
5. Prøv disconnect/reconnect 10+ gange og noter fejl.
# Moonboard-BLE-test
# Moonboard-BLE-test
