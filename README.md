# Tennis Resultattavle – Vue

Dette projekt implementerer en tennisagtig resultattavle bygget i Vue 3.

Applikationen håndterer pointgivning, vinderegler og uafgjort baseret på de angivne krav.

---

## Funktioner

- To spillere med hver sin +1-knap
- Nulstil-knap der sætter begge scores til 0
- En spiller vinder hvis:
  - Spilleren har mindst 6 point
  - OG mindst 2 point mere end modstanderen
- Hvis stillingen bliver 11–11, erklæres spillet for uafgjort
- Når spillet er afsluttet (sejr eller uafgjort), deaktiveres +1-knapperne

---

## Teknologi

Projektet er lavet i:

- Vue 3
- Vite

Applikationen benytter:

- Reaktiv state (`data`)
- Methods til håndtering af brugerinteraktion
- Computed properties til beregning af spillets tilstand (vinder, uafgjort og status)

---

## Installation

1. Installer dependencies:

npm install

npm run dev

---

## Brug

Åbn i browser:

http://localhost:5173/