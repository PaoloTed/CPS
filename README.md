# Calcolo delle Probabilità e Statistica (CPS)

Repository didattico completo per il corso di **Calcolo delle Probabilità e Statistica (CPS)** presso l'**Università degli Studi di Napoli Federico II** (Corso di Laurea in Ingegneria Informatica / Ingegneria dell'Informazione).

---

## 📌 Indice dei Contenuti

1. [I Docenti e il Contesto Accademico](#-i-docenti-e-il-contesto-accademico)
2. [Guida alla Prova d'Esame](#-guida-alla-prova-desame)
   - [Struttura Standard della Prova Scritta](#struttura-standard-della-prova-scritta)
   - [Requisiti Minimi di Sufficienza](#requisiti-minimi-di-sufficienza)
   - [Analisi Dettagliata: Esercizio 1 (Discreto)](#esercizio-1-variabili-discrete-e-tabelle-congiunte)
   - [Analisi Dettagliata: Esercizio 2 (Continuo e Decisione)](#esercizio-2-variabili-continue-trasformazioni-e-decisione-statistica)
3. [Mappa e Struttura del Progetto](#-mappa-e-struttura-del-progetto)
4. [Compendio Formule e Appunti LaTeX](#-compendio-formule-e-appunti-latex)
5. [Errori Comuni da Evitare](#-errori-comuni-da-evitare)

---

## 👨‍🏫 I Docenti e il Contesto Accademico

Il materiale raccolto riflette le diverse anime e la transizione didattica del corso di Calcolo delle Probabilità e Statistica alla Federico II:

* **Prof. Davide Mattera**:
  * Docente storico di riferimento per l'impostazione degli scritti e degli appelli d'esame.
  * I suoi compiti seguono una struttura metodologica molto rigorosa e standardizzata, focalizzata su tabelle congiunte discrete, trasformazioni continue e problemi di decisione binaria (MAP/ML/Neyman-Pearson).
  * Materiale dedicato: cartella [Esercizi Mattera (svolti)](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/Esercizi/Esercizi%20Mattera%20(svolti)), file [Esami.txt](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/Esercizi/Esami.txt) e la Parte V di [riassunto_cps_formule_fino_a_5.1.9.md](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/Formulari/riassunto_cps_formule_fino_a_5.1.9.md).

* **Prof. Marco Lops**:
  * Professore ordinario ed eminente accademico, autore del materiale teorico di riferimento su teoria delle probabilità, misura dell'informazione, teoria di Markov e statistica inferenziale.
  * Materiale dedicato: cartella [SlideLops](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/SlideLops) con le storiche *Slide Verdi-Nere* e le sintesi tematiche.

* **Nuovo Docente (Ciclo Primavera 2026)**:
  * Docente titolare delle lezioni erogate da marzo/aprile a maggio 2026.
  * Materiale dedicato: archivio ordinato delle lezioni alla lavagna digitale in [Nuovo professore](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/Nuovo%20professore) e [Lavagne Professore](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/Lavagne%20Professore).

* **Angelo Marcone**:
  * Autore del progetto open-source modulare in LaTeX [SlideFatteBene](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/SlideFatteBene), che rielabora organicamente l'intero programma didattico del corso.

---

## 📝 Guida alla Prova d'Esame

### Struttura Standard della Prova Scritta

La prova scritta (stile Mattera) è tradizionalmente articolata in **due macro-esercizi**, ciascuno strutturato in 4 sotto-quesiti (a, b, c, d):

```
┌────────────────────────────────────────────────────────────────────────┐
│                        COMPITO D'ESAME CPS                             │
├────────────────────────────────────┬───────────────────────────────────┤
│   ESERCIZIO 1 (Variabili Discrete)  │ ESERCIZIO 2 (Continue & Decisione)│
├────────────────────────────────────┼───────────────────────────────────┤
│ a. PMF Marginali da tabella cong.  │ a. Costante di Normalizzazione A  │
│ b. PMF Variabile Somma T = X + Y   │ b. PDF della trasformata Y = g(X) │
│ c. PMF Condizionata ad un evento   │ c. Parametri (Moda e Mediana)     │
│ d. Indipendenza / Entropia H(X)    │ d. Test di Decisione (MAP / ML)   │
└────────────────────────────────────┴───────────────────────────────────┘
```

### Requisiti Minimi di Sufficienza

> [!IMPORTANT]
> **Vincolo di Sufficienza Docente**:
> Per conseguire la sufficienza (voto $\ge 18/30$), è **strettamente necessario** svolgere in modo corretto (anche con lievi imperfezioni di calcolo non concettuali):
> 1. **L'intero Esercizio 1** (tutti i punti a, b, c, d);
> 2. **Il punto "a" dell'Esercizio 2** (determinazione della costante di normalizzazione $A$).
>
> Senza questi requisiti minimi, la prova è considerata insufficiente a prescindere dal resto dello svolgimento.

---

### Esercizio 1: Variabili Discrete e Tabelle Congiunte

* **Dati assegnati**: Alfabeti discreti (es. $X \in \{0, 1\}$, $Y \in \{0, 2\}$ oppure $X \in \{0, 2\}$, $Y \in \{1, 3\}$) e le relative probabilità congiunte non nulle $P(X=x, Y=y)$.
* **Punto a - PMF Marginali**:
  * Si costruisce la tabella a doppia entrata.
  * $p_X(x) = \sum_y p_{X,Y}(x, y)$ (somma per righe).
  * $p_Y(y) = \sum_x p_{X,Y}(x, y)$ (somma per colonne).
  * *Verifica immediata*: accertarsi che $\sum_x p_X(x) = 1$ e $\sum_y p_Y(y) = 1$.
* **Punto b - Somma $T = X + Y$**:
  * Determinare l'alfabeto di $T$ valutando tutti i possibili valori $t = x + y$.
  * Sommare le probabilità congiunte delle coppie $(x, y)$ che danno la stessa somma $t$:
    $$p_T(t) = \sum_{(x,y): x+y=t} p_{X,Y}(x, y)$$
* **Punto c - PMF Condizionata**:
  * Sia $C$ l'evento condizionante (es. $X \cdot Y = 0$, $X \cdot Y < 3$ oppure $|V - \mu| < \delta$).
  * Calcolare prima $\mathbb{P}(C)$ sommando le probabilità delle celle favorevoli.
  * Per ogni $t$:
    $$p_{T \mid C}(t) = \frac{\mathbb{P}(\{T=t\} \cap C)}{\mathbb{P}(C)}$$
* **Punto d - Indipendenza stocastica o Entropia**:
  * **Indipendenza**: Due variabili sono indipendenti se e solo se $p_{X,Y}(x, y) = p_X(x) p_Y(y)$ per ogni coppia $(x,y)$. Se anche per una sola cella l'uguaglianza fallisce, le variabili **non** sono stocasticamente indipendenti.
  * **Entropia di Shannon**: $H(X) = - \sum_{x} p_X(x) \log_2 p_X(x)$ (espressa in bit). L'entropia è massima quando la distribuzione è uniforme.

---

### Esercizio 2: Variabili Continue, Trasformazioni e Decisione Statistica

* **Dati assegnati**: PDF continua semidefinita positiva, tipicamente esponenziale/Rayleigh con gradino unitario $u(x)$, ad es. $f_X(x) = A x e^{-x^2} u(x)$ o $f_X(x) = A e^{-\lambda x} u(x)$.
* **Punto a - Calcolo della Costante $A$**:
  * Imporre la condizione di normalizzazione:
    $$\int_{-\infty}^{+\infty} f_X(x)\,dx = 1 \implies A \int_{0}^{+\infty} x e^{-x^2}\,dx = 1 \implies A \cdot \left[ -\frac{1}{2}e^{-x^2} \right]_0^\infty = 1 \implies A = 2$$
* **Punto b - Trasformazione di Variabile $Y = g(X)$**:
  * Data $Y = \sqrt{X}$ o $Y = \ln(X)$ con $g(x)$ monotona strettamente crescente:
    $$x = g^{-1}(y), \quad f_Y(y) = f_X(g^{-1}(y)) \left| \frac{d}{dy} g^{-1}(y) \right|$$
  * Ricordare sempre di specificare il nuovo intervallo di definizione (supporto) per la variabile $Y$.
* **Punto c - Parametri di Sintesi (Moda e Mediana)**:
  * **Moda ($m_o$)**: punto di massimo relativo/assoluto della PDF, calcolato risolvendo $f'_Y(y) = 0$ con verifica di derivata seconda negativa ($f''_Y(m_o) < 0$).
  * **Mediana ($m_e$)**: valore tale che l'area cumulata fino a $m_e$ è pari a metà dell'area totale:
    $$F_Y(m_e) = \int_{-\infty}^{m_e} f_Y(y)\,dy = \frac{1}{2}$$
* **Punto d - Teoria delle Decisioni Binarie ($H_1$ vs $H_2$)**:
  * Osservazione $Z$: sotto $H_1$, $Z \sim f_1(z)$; sotto $H_2$, $Z \sim f_2(z)$.
  * Criterio MAP (Maximum A Posteriori):
    $$\Lambda(z) = \frac{f_1(z)}{f_2(z)} \gtrless_{H_2}^{H_1} \frac{P(H_2)}{P(H_1)}$$
  * Se le ipotesi sono equiprobabili ($P(H_1)=P(H_2)=1/2$), il test MAP coincide con il criterio di Massima Verosimiglianza (ML) con soglia unitaria ($\Lambda(z) \gtrless 1$).
  * Valutazione puntuale: sostituire il valore numerico dell'osservazione $z$ per determinare l'ipotesi scelta.

---

## 🗂 Mappa e Struttura del Progetto

```
CPS/
├── Esercizi/                                    # Prove d'esame ed esercitazioni
│   ├── Esami.txt                                # Trascrizione testuali prove d'esame recenti e note
│   ├── esami_calcolo_probabilita.pdf            # Raccolta storica prove d'esame
│   ├── Traccia_CPS.pdf                          # Tracce d'esame aggregate
│   ├── Esercizi Mattera (svolti)/               # Prove con svolgimenti (maggio 2026, prove prec.)
│   ├── Tracce-Esami/                            # Tracce ufficiali con date (2025 - 2026)
│   ├── Tracce-Esercizi/                         # Fogli di esercitazione del corso (marzo - giugno)
│   └── variabili_aleatorie_discrete/            # Schemi fotografici su VA discrete
├── Formulari/                                   # Strumenti di consultazione rapida
│   ├── riassunto_cps_formule_fino_a_5.1.9.md   # Compendio esaustivo con teoria e prontuario esame
│   └── Formulario CPS.pdf                       # Formulario pronto per la stampa
├── Lavagne Professore/                          # Lavagne digitali lezioni primaverili 2026
├── Nuovo professore/                            # Materiale del docente primavera 2026
│   └── Lavagne_delle_lezioni_primavera_2026/    # Lezioni complete dal 9 aprile al 28 maggio 2026
├── SlideFatteBene/                              # Dispensa completa in LaTeX (Autore: Angelo Marcone)
│   ├── main.tex                                 # Sorgente principale compilabile
│   ├── main.pdf                                 # PDF completo generato
│   ├── README.md                                # Istruzioni di compilazione LaTeX
│   └── chapters/                                # Capitoli modulari suddivisi per argomento
│       ├── 01_fondamenti_probabilita/
│       ├── 02_calcolo_combinatorio/
│       ├── 03_variabili_aleatorie/
│       ├── 04_varianza/
│       ├── 05_continuo/
│       └── 06_teoria_informazione/
├── SlideLops/                                   # Materiale teorico del Prof. Marco Lops
│   ├── SlideRiassunte/                          # Fondamenti e statistica inferenziale
│   └── SlidesVerdiNere/                         # Slide storiche (Probabilità, Informazione, Inferenza)
├── altro/                                       # Risorse ausiliarie
│   └── soluzione_renderizzata.html              # Risoluzioni con MathJax in alta definizione
└── README.md                                    # Questa guida
```

---

## 📖 Compendio Formule e Appunti LaTeX

### Formulario Markdown

Il file [riassunto_cps_formule_fino_a_5.1.9.md](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/Formulari/riassunto_cps_formule_fino_a_5.1.9.md) è uno strumento ad alta densità informativa che include:
* Assiomi di Kolmogorov e probabilità condizionata;
* Teorema di Bayes e Legge della Probabilità Totale;
* Variabili notevoli discrete (Bernoulli, Binomiale, Geometrica, Poisson);
* Variabili notevoli continue (Uniforme, Esponenziale, Gaussiana con tavola della funzione $Q(x)$);
* Teoria dell'informazione (Entropia congiunta, condizionale, codifica di sorgente di Huffman);
* Prontuario operativo e checklist anti-errore per il compito scritto.

### Compilazione Dispensa LaTeX (`SlideFatteBene`)

Per ricompilare il documento LaTeX in locale qualora si apportassero modifiche:

```bash
cd SlideFatteBene
pdflatex main.tex
pdflatex main.tex
```

> **Nota**: La doppia compilazione garantisce la corretta indicizzazione delle sezioni e dei riferimenti ipertestuali nel documento finale [main.pdf](file:///c:/Users/Paolo/Desktop/Universita/Terzo%20Anno/CPS/SlideFatteBene/main.pdf).

---

## ⚠️ Errori Comuni da Evitare

1. **Probabilità puntuale di una variabile aleatoria continua**:
   * Per qualunque variabile continua $X$ e qualsiasi valore fissato $x_0 \in \mathbb{R}$, vale **sempre**:
     $$\mathbb{P}(X = x_0) = 0$$
   * Non tentare mai di sostituire $x_0$ nella PDF per calcolare una probabilità puntuale.
2. **Modulo dello jacobiano nelle trasformazioni**:
   * Nel calcolo della PDF trasformata $f_Y(y) = f_X(g^{-1}(y)) \left| \frac{d}{dy} g^{-1}(y) \right|$, non dimenticare il **valore assoluto** sulla derivata dell'inversa.
3. **Controllo di normalizzazione**:
   * Al termine del calcolo delle PMF marginali o della variabile somma, verificare sempre che la somma dei coefficienti sia tassativamente pari a $1$.
4. **Dominio e funzione gradino $u(x)$**:
   * Negli integrali con gradino unitario $u(x)$, ricordarsi che gli estremi di integrazione si contraggono da $(-\infty, +\infty)$ a $[0, +\infty)$. Dimenticarlo altera la costante $A$.
