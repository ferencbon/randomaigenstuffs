# Architecture Overview Template

## Cél

Itt írd le a rendszer működésének nagy képét, hogy egy új fejlesztő értse a fő komponenseket és azok kapcsolatát.

## Ide ezt dokumentáld

- a rendszer fő részei és felelősségeik
- milyen rétegek vagy fő komponensek vannak
- egy tipikus request vagy folyamat magas szintű útja
- hol él az üzleti logika, hol történik az integráció, hol fut a háttérmunka
- milyen technikai határok fontosak a rendszerben

## Ne ide írd

- az egyes üzleti szabályok részletes listáját
- döntési naplót arról, hogy miért ezt az architektúrát választottátok
- lokális indítási lépéseket
- teljes kódrészleteket

## Javasolt kérdések

- Melyek a rendszer fő építőelemei?
- Mi történik egy tipikus bejövő kérés során?
- Hol vannak a szinkron és aszinkron feldolgozási pontok?
- Melyik témáról kell külön architektúra dokumentumot nyitni?

## Kapcsolódó dokumentumok

- [Tenancy](tenancy.md)
- [Background Jobs](background-jobs.md)
- [Business Rules](../domain/business-rules.md)
- [ADR sablon](../adr/001-template.md)
