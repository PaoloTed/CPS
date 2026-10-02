# Appunti di Probabilità e Statistica

Questi appunti coprono i concetti fondamentali trattati nel corso di Probabilità e Statistica presso l'**Università degli Studi di Napoli Federico II** (Inizio corso Marzo 2026). Sono stati scritti interamente in \LaTeX\ e resi open-source per favorire la condivisione e lo studio collaborativo.

> [!WARNING]
> Questi appunti sono stati redatti a scopo di studio personale e non mi assumo alcuna responsabilità riguardo all'assoluta correttezza o completezza dei contenuti.

## Come Contribuire
Tutto il codice sorgente utilizzato per generare questo documento è aperto e modificabile. Se trovi degli errori tipografici, concetti da chiarire, o vuoi semplicemente migliorare e arricchire questo PDF, sei liberissimo di farlo e ogni contributo è il benvenuto!

1. Fai un **Fork** della repository
2. Apporta le modifiche ai file `.tex` nella cartella `chapters/` o al `main.tex`
3. Assicurati che il codice compili correttamente
4. Apri una **Pull Request**

### Aggiungere o modificare un capitolo
Il progetto ha una struttura modulare per mantenere il codice ordinato:
- Per aggiungere un capitolo semplice, basta creare un nuovo file `.tex` all'interno della cartella `chapters/` e includerlo in `chapters/index.tex` (es. `\input{chapters/nuovo_capitolo.tex}`).
- Se un capitolo è corposo e contiene molti **sottocapitoli**, è consigliabile creare una cartella dedicata (es. `chapters/07_nuovo_argomento/`), inserire al suo interno un file aggregatore `chapter.tex` che includerà i vari sotto-paragrafi, e infine richiamare questo file in `chapters/index.tex`.

## 🛠 Come compilare il codice
Se desideri generare o aggiornare il file PDF in locale dopo una modifica, è sufficiente utilizzare un compilatore LaTeX (ad esempio `pdflatex`):

```bash
pdflatex main.tex
pdflatex main.tex
```
*(Nota: la doppia esecuzione è necessaria per generare e aggiornare correttamente l'Indice del documento).*

Il file `main.pdf` è comunque costantemente aggiornato e incluso in questa repository per permettere a chiunque di scaricarlo senza necessità di compilare il codice sorgente.

---
*Autore: Angelo Marcone*
