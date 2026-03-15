# MoonBoard BLE Debug

Minimal Web Bluetooth-side til at:
- forbinde til MoonBoard eller MoonBoard-lignende BLE-enheder
- logge services og characteristics
- lytte efter notify-data
- sende forskellige payload-varianter for at finde boardets rigtige kommandoformat

## Funktioner

- `Connect BLE` / `Disconnect`
- valg af `Service UUID` og `Write Characteristic UUID`
- automatisk forsøg på notify-listening, typisk på `6e400003-...`
- quick payload-knapper til hurtige tests
- multiline payload-felt, så flere kommandoer kan prøves i rækkefølge
- valg mellem rå payload, `\n` og `\r\n`
- copy/download af logs

## Kør lokalt

Web Bluetooth kræver en sikker kontekst:
- `http://localhost`
- eller `https://`

Start en lokal server:

```bash
python3 -m http.server 8080
```

Åbn derefter:

- `http://localhost:8080`

## Anbefalet testflow

1. Tryk `Connect BLE`
2. Bekræft i loggen hvilken write-characteristic der blev valgt
3. Bekræft om notify-listening blev startet
4. Send fx `l#E128#`
5. Prøv igen med `Append \n`
6. Prøv igen med `Append \r\n`
7. Gem loggen, hvis boardet svarer tilbage eller reagerer forskelligt

## Bemærk

Projektet er nu bevidst skåret ned til BLE-debug. Problem-builder, lokale problems og øvrig MoonBoard-app-logik er fjernet fra UI og kode.
