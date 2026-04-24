# Dokumentációs Template

## Cél

Ez a mappa egy új projektbe átemelhető dokumentációs sablon. Nem kész mintarendszert ír le, hanem megmutatja, hogy melyik fájlba milyen típusú információ kerüljön.

## Ide ezt dokumentáld

- röviden, mi a rendszer célja
- milyen fő technológiákat használ a projekt
- hogyan induljon el egy új kolléga az olvasásban
- hogyan van felosztva a dokumentáció
- mi a csapat dokumentációs alapelve

## Ne ide írd

- részletes üzleti szabályokat
- konkrét architektúrális döntések teljes indoklását
- lokális troubleshooting lépéseket
- kódszintű implementációs részleteket

## Javasolt kérdések

- Mi ez a rendszer egy új kolléga számára egy percben elmagyarázva?
- Melyik 4-6 dokumentumot kell először elolvasni?
- Mi a különbség az `ADR`, az `architecture`, a `domain` és a `runbook` között?
- Milyen elv alapján döntjük el, hogy valamit egyáltalán dokumentálunk-e?

## Kapcsolódó dokumentumok

- [Architecture Overview](architecture/overview.md)
- [Business Rules](domain/business-rules.md)
- [Local Development](runbook/local-development.md)

## Javasolt struktúra

```text
/docs-template
  /architecture
  /domain
  /adr
  /runbook
```

## Rövid emlékeztető

- `ADR = miért`
- `Architecture = hogyan`
- `Domain = üzleti jelentés és szabály`
- `Code + tests = pontos működés`
