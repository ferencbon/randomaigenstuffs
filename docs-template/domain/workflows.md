# Workflows Template

## Cél

Itt írd le az üzleti folyamatokat lépésről lépésre, emberi nyelven, hogy a rendszer viselkedése követhető legyen kódolvasás nélkül is.

## Ide ezt dokumentáld

- a legfontosabb üzleti folyamatokat
- a folyamat fő lépéseit és döntési pontjait
- hol lép be háttérmunka vagy manuális jóváhagyás
- milyen kimenetelek vannak siker, hiba vagy review esetén

## Ne ide írd

- alacsony szintű metódushívási sorrendet
- teljes üzleti szabálylistát ismételten
- technikai locking vagy infra részleteket

## Javasolt kérdések

- Mi a legfontosabb end-to-end folyamat a rendszerben?
- Hol akad meg a folyamat manuális review-ra?
- Mely lépések aszinkronok?
- Melyik ponton történik állapotváltás?

## Kapcsolódó dokumentumok

- [Business Rules](business-rules.md)
- [Background Jobs](../architecture/background-jobs.md)
- [Local Development](../runbook/local-development.md)
