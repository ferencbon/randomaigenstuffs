# Background Jobs Template

## Cél

Itt dokumentáld a háttérfeldolgozás működését, különösen azt, ami requesten kívül történik.

## Ide ezt dokumentáld

- milyen típusú jobok léteznek
- mire használjátok a job infrastruktúrát
- hogyan működik az ütemezés, retry és locking
- hogyan kezelitek a hibákat és az idempotenciát
- milyen logok, metrikák és dashboardok fontosak

## Ne ide írd

- azt, hogy miért a választott job frameworköt használjátok
- az egyes workflow-k teljes üzleti leírását
- konkrét job handler kódot

## Javasolt kérdések

- Melyik munka miért kerül ki a request útvonalból?
- Mi véd az átfedő futások ellen?
- Mi történik sikertelen vagy többször retryolt job esetén?
- Hogyan lesz a háttérmunka tenant-aware?

## Kapcsolódó dokumentumok

- [Architecture Overview](overview.md)
- [Workflows](../domain/workflows.md)
- [ADR sablon](../adr/001-template.md)
