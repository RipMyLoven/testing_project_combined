# Testiplaan – Kvaliteedijälg

**Projekti nimi:** Kvaliteedijälg  
**Autor:** Martin Sild  
**Kuupäev:** 24.11.2025  
**Versioon:** 0.1  

---

## 1. Sissejuhatus
**Eesmärk:**  
Testiplaani eesmärk on hinnata projekti Kvaliteedijälg kvaliteeti läbi erinevate testide, sh API, frontend, backend, CI ning koormustestimise.  

**Kontekst:**  
Projekt sisaldab veebirakendust koos API-dega, A/B-testimisega ja kasutajate tegevuse jälgimisega GA4 kaudu. Testimine aitab tuvastada vigu, jõudlusprobleeme ja tagada süsteemi stabiilsus enne tootmisse viimist.  

**Osapooled ja rollid:**  
- Martin Sild – testiplaani autor, testide täitmine  
- Arendustiim – bugide parandamine  
- Projektijuht – testide prioriseerimine  

---

## 2. Ulatus
**Kaasatud moodulid:**  
- Backend API-d (CRUD lõpp-punktid)  
- Frontend (UI funktsionaalsus, A/B testid)  
- CI/CD torujuhtmed (GitHub Actions)  
- Koormustestimine (Locust)  
- GA4 andmete jälgimine  

**Mittekäsitletavad osad:**  
- Tootmise andmed (ainult test-andmed)  
- Kolmanda osapoole teenuste sisemine logika  

---

## 3. Nõuded ja aktsepteerimiskriteeriumid

**Funktsionaalsed nõuded:**  
- API tagastab korrektsed HTTP vastused (200, 201, 400, 404, 500)  
- Frontend kuvab õige sisu vastavalt kasutaja rollile  
- A/B testid toimivad ja koguvad GA4-s korrektseid sündmusi  

**Mittenõuded:**  
- Jõudlus: API reageerimisaeg < 500ms  
- Koormus: maksimaalne veamäär Locust testides < 2%  
- Turvalisus: testimise käigus ei simuleerita rünnakuid  

**Aktsepteeritavuse kontroll-leht:**  
| Nõue | Kontroll | Staatus |
|------|---------|--------|
| API CRUD toimib | Postman testid |  |
| UI funktsionaalsus | Manuaalne ja Cypress |  |
| GA4 sündmused | GA4 debug view |  |
| A/B test | Split.io raport |  |
| CI pipeline | GitHub Actions |  |
| Koormustest | Locust raport |  |

---

## 4. Riskid ja maandus

| ID | Risk | Mõju | Tõenäosus | Maandus |
|----|------|------|-----------|---------|
| R1 | API vastused ebaõiged | Kõrge | Keskmine | Automaattestide ja CI abil kontroll |
| R2 | Locust testid näitavad ülekoormust | Keskmine | Kõrge | Limiidid, skaleerimine |
| R3 | GA4 ei logi kõiki sündmusi | Keskmine | Madal | Tunneli testid, debug view |
| R4 | CI torujuhtmed ebaõnnestuvad | Kõrge | Keskmine | Monitooring, automaatsed alertid |
| R5 | A/B testide valed andmed | Keskmine | Madal | Kontrollitud testandmed |

---

## 5. Meetodid ja tööriistad

**Testimise liigid:**  
- Ühikutestid (pytest, Jest)  
- Integratsioonitestid (API ja DB)  
- A/B testid (Split.io, GA4)  
- Koormustestid (Locust)  
- CI testimine (GitHub Actions)  

**Automaatika vahendid:**  
- Python + pytest (backend)  
- Jest (frontend)  
- Locust (koormus)  
- GA4 debug view (analüütika)  
- GitHub Actions (CI)  

---

## 6. Testkeskkonnad ja andmed

**Konfiguratsioonid:**  
- OS: Ubuntu 22.04 / Windows 10  
- Python 3.11  
- Node.js 20  
- Browsers: Chrome, Firefox  

**Testandmete allikad:**  
- Mock andmebaas (SQLite/PostgreSQL sandbox)  
- API sandbox keskkond  
- A/B testide kontrollitud kasutajagrupid  

---

## 7. Ajajoon ja vastutajad

| Tund | Tegevus | Vastutaja |
|------|---------|-----------|
| 1 | Testkeskkonna seadistamine | Martin Sild |
| 2 | API testid Postman/Hoppscotch | Martin Sild |
| 3 | Backend ühikutestid pytest | Martin Sild |
| 4 | Frontend ühikutestid Jest | Martin Sild |
| 5 | Locust koormustestid | Martin Sild |
| 6 | GA4 sündmuste kontroll | Martin Sild |
| 7 | A/B testide seadistamine | Martin Sild |
| 8 | CI pipeline testimine | Martin Sild |
| 9 | Tulemuste kogumine | Martin Sild |
| 10 | Raportite koostamine ja dokumenteerimine | Martin Sild |

---

## 8. Raporteerimine

- **Aruannete formaadid:** Markdown ja CSV (koormus, API logid, A/B tulemused)  
- **Asukoht:** `docs/results/`  
  - `api_results.md`  
  - `locust_report.md`  
  - `ab_test_report.md`  
- **Edukriteeriumid:**  
  - Kõik kriitilised testid roheline ( )  
  - Maksimaalselt 2% veamäär koormustestides  
  - GA4 andmed korrektsed
