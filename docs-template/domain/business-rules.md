# Business Rules Template

## Cél

Itt írd le azokat a nem triviális üzleti szabályokat, amelyeket a csapatnak és az új belépőknek gyorsan meg kell érteniük.

## Ide ezt dokumentáld

- fontos validációs szabályokat
- lifecycle vagy állapotátmeneti szabályokat
- jogosultsági vagy szerepkör alapú üzleti korlátozásokat
- tenant-scope-ban értelmezett üzleti megkötéseket
- olyan szabályokat, amelyeket drága lenne csak kódból újrafelfedezni

## Ne ide írd

- technikai implementációt
- minden apró mezőszintű ellenőrzést
- architektúrális döntések indoklását
- üzemeltetési runbook lépéseket

## Javasolt kérdések

- Mely szabályok okoznának hibás fejlesztést, ha valaki nem ismerné őket?
- Mely állapotátmenetek tiltottak?
- Mely szabályok tenantonként eltérhetnek?
- Mely szabályokat kell tesztekkel külön lefedni?

## Kapcsolódó dokumentumok

- [Workflows](workflows.md)
- [Glossary](glossary.md)
- [Tenancy](../architecture/tenancy.md)
