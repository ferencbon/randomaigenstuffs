# Tenancy Template

## Cél

Itt dokumentáld, hogyan működik a tenant-kezelés technikai és rendszer-szintű nézőpontból.

## Ide ezt dokumentáld

- hogyan azonosítjátok a tenantot
- hogyan terjed tovább a tenant context a rendszeren belül
- hogyan történik az adatizoláció
- mely komponensek tenant-aware működésűek
- milyen operációs és support szempontok vannak tenant nézőpontból

## Ne ide írd

- azt, hogy miért ezt a tenant modellt választottátok
- üzleti szabályokat arról, hogy mely folyamatok tenant-scope-osak
- kódszintű repository vagy middleware implementációt

## Javasolt kérdések

- Mi a tenant forrása: header, subdomain, claim vagy más?
- Hol válik kötelezővé a tenant context?
- Vannak-e kivételek a tenant izoláció alól?
- Hogyan futnak a háttérjobok tenant contexttel?

## Kapcsolódó dokumentumok

- [Architecture Overview](overview.md)
- [Business Rules](../domain/business-rules.md)
- [Glossary](../domain/glossary.md)
- [ADR sablon](../adr/002-template.md)
