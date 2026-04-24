# ADR Template

## Cél

Ezt a második sablont ugyanúgy használhatjátok további döntésekhez, amikor már több ADR él a repóban és kell egy új számozott kiindulópont.

## Ide ezt dokumentáld

- új architektúrális vagy platform döntéseket
- üzemeltetést, skálázást vagy tenancyt érintő fontos trade-offokat
- olyan választásokat, amelyek hatással vannak a fejlesztési irányra vagy a rendszer korlátaira

## Ne ide írd

- apró refaktor döntéseket
- egyszer használatos ticket-jegyzeteket
- tisztán domain szabálymagyarázatot

## Javasolt kérdések

- A döntés után mi lesz egyszerűbb, és mi lesz nehezebb?
- Mely csapatok vagy komponensek érintettek?
- Mikor kellhet ezt a döntést felülvizsgálni?

## Kapcsolódó dokumentumok

- [Tenancy](../architecture/tenancy.md)
- [Background Jobs](../architecture/background-jobs.md)
- [Local Development](../runbook/local-development.md)

## Ajánlott belső szerkezet

- Kontextus
- Döntés
- Indoklás
- Következmények
- Mérlegelt alternatívák

## Rövid emlékeztető

- `ADR = miért`
- A működés részlete maradjon az architecture dokumentumokban
