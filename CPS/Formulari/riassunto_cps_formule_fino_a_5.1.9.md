# Compendio di Calcolo delle Probabilità e Statistica
### Dalle basi fino a Sezione 5.1.9 (Pagina 93 / 99 di `main.pdf`)
*Formulario ragionato, condizioni di applicabilità e prontuario operativo per le prove d'esame*

---

## Indice Generale

1. [Parte I: Fondamenti di Probabilità e Calcolo Combinatorio (Capitoli 1 e 2)](#parte-i-fondamenti-di-probabilità-e-calcolo-combinatorio)
2. [Parte II: Variabili Aleatorie Discrete e Distribuzioni Notevoli (Capitolo 3)](#parte-ii-variabili-aleatorie-discrete)
3. [Parte III: Momenti, Disuguaglianze e Variabili Multiple Discrete (Capitolo 4)](#parte-iii-momenti-disuguaglianze-e-variabili-multiple-discrete)
4. [Parte IV: Dal Discreto al Continuo (Capitolo 5, fino a 5.1.9)](#parte-iv-dal-discreto-al-continuo)
5. [Parte V: Prontuario Operativo d'Esame "Stile Mattera"](#parte-v-prontuario-operativo-desame-stile-mattera)

---

# Parte I: Fondamenti di Probabilità e Calcolo Combinatorio

### 1.1 Assiomi di Kolmogorov e Proprietà Fondamentali
Dato uno spazio campionario $\Omega$ e una $\sigma$-algebra degli eventi $\mathcal{F}$, una misura di probabilità $\mathbb{P}: \mathcal{F} \to [0, 1]$ soddisfa:

1. **Non-negatività:** $\mathbb{P}(A) \ge 0 \quad \forall A \in \mathcal{F}$
2. **Normalizzazione:** $\mathbb{P}(\Omega) = 1$
3. **Additività numerabile:** se $A_1, A_2, \dots$ sono disgiunti a due a due ($A_i \cap A_j = \emptyset$ per $i \neq j$), allora:
   $$\mathbb{P}\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} \mathbb{P}(A_i)$$

#### Formule derivate essenziali
* **Evento complementare:** $\mathbb{P}(A^c) = 1 - \mathbb{P}(A)$
* **Evento impossibile:** $\mathbb{P}(\emptyset) = 0$
* **Monotonia:** se $A \subseteq B \implies \mathbb{P}(A) \le \mathbb{P}(B)$
* **Differenza di eventi:** $\mathbb{P}(A \setminus B) = \mathbb{P}(A) - \mathbb{P}(A \cap B)$
* **Unione di due eventi (Inclusione-Esclusione):**
  $$\mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B) - \mathbb{P}(A \cap B)$$

> **Quando si usa all'esame:**
> * Quando viene richiesta la probabilità dell'evento "almeno uno si verifica" ($\mathbb{P}(A \cup B)$).
> * Per semplificare il calcolo di eventi complessi passando al complementare: $\mathbb{P}(\text{"almeno un successo"}) = 1 - \mathbb{P}(\text{"nessun successo"})$.

---

### 1.2 Calcolo Combinatorio: Mappa di Scelta
Dati $n$ elementi distinti e gruppi di cardinalità $k$:

| Tipo di raggruppamento | L'ordine conta? | Ripetizione ammessa? | Formula |
| :--- | :---: | :---: | :--- |
| **Disposizioni semplici** | **Sì** | **No** | $D_{n, k} = \frac{n!}{(n-k)!}$ |
| **Disposizioni con ripetizione** | **Sì** | **Sì** | $D'_{n, k} = n^k$ |
| **Permutazioni semplici** | **Sì** ($k = n$) | **No** | $P_n = n!$ |
| **Permutazioni con ripetizione** | **Sì** | **Sì** (gruppi $n_1, \dots, n_r$) | $P_n^{n_1, \dots, n_r} = \frac{n!}{n_1! n_2! \cdots n_r!}$ |
| **Combinazioni semplici** | **No** | **No** | $C_{n, k} = \binom{n}{k} = \frac{n!}{k!(n-k)!}$ |
| **Combinazioni con ripetizione** | **No** | **Sì** | $C'_{n, k} = \binom{n+k-1}{k}$ |

> **Quando si usa all'esame:**
> * Estrazioni in blocco o contemporanee (senza ordine, senza reimmissione) $\to$ **Combinazioni semplici** $\binom{n}{k}$.
> * Estrazioni ordinate con reimmissione (es. generazione di sequenze di bit, stringhe, codici PIN) $\to$ **Disposizioni con ripetizione** $n^k$.
> * Estrazioni ordinate senza reimmissione (es. podio, classifica) $\to$ **Disposizioni semplici**.
> * Anagrammi o parole con lettere ripetute $\to$ **Permutazioni con ripetizione**.

---

### 1.3 Probabilità Condizionata, Legge della Probabilità Totale e Teorema di Bayes

#### Probabilità Condizionata
$$\mathbb{P}(A \mid B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}, \quad \text{con } \mathbb{P}(B) > 0$$
* **Regola della catena (prodotto):** $\mathbb{P}(A \cap B) = \mathbb{P}(A \mid B)\mathbb{P}(B) = \mathbb{P}(B \mid A)\mathbb{P}(A)$.

#### Legge della Probabilità Totale
Sia $\{E_1, E_2, \dots, E_M\}$ una partizione dello spazio campionario $\Omega$ (disgiunti a due a due e $\bigcup_{m=1}^M E_m = \Omega$ con $\mathbb{P}(E_m) > 0$):
$$\mathbb{P}(A) = \sum_{m=1}^M \mathbb{P}(A \mid E_m)\mathbb{P}(E_m)$$

#### Teorema di Bayes
Permette di "invertire il condizionamento" (probabilità a posteriori delle cause):
$$\mathbb{P}(E_k \mid A) = \frac{\mathbb{P}(A \mid E_k)\mathbb{P}(E_k)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A \mid E_k)\mathbb{P}(E_k)}{\sum_{m=1}^M \mathbb{P}(A \mid E_m)\mathbb{P}(E_m)}$$

#### Indipendenza Stocastica tra Eventi
Due eventi $A$ e $B$ sono indipendenti ($A \perp B$) se e solo se:
$$\mathbb{P}(A \cap B) = \mathbb{P}(A)\mathbb{P}(B) \iff \mathbb{P}(A \mid B) = \mathbb{P}(A)$$

> **Quando si usa all'esame:**
> * Problemi di diagnosi medica (test positivo $\to$ calcolare la probabilità di essere realmente malato).
> * Trasmissione su canale rumoroso binario ($H_1, H_2$ ipotesi trasmesse, $Z$ simbolo ricevuto).
> * Calcolo della probabilità di falso allarme e mancata rivelazione.

---

# Parte II: Variabili Aleatorie Discrete

Una variabile aleatoria discreta $X: \Omega \to \mathcal{X}$ assume valori in un alfabeto finito o numerabile $\mathcal{X} = \{x_1, x_2, \dots\}$.

### 2.1 PMF, CDF e Momenti Discreti

* **Probability Mass Function (PMF):**
  $$p_X(x) = \mathbb{P}(X = x), \quad p_X(x) \ge 0, \quad \sum_{x \in \mathcal{X}} p_X(x) = 1$$
* **Cumulative Distribution Function (CDF):**
  $$F_X(x) = \mathbb{P}(X \le x) = \sum_{x_i \le x} p_X(x_i)$$
  È una funzione a gradini, monotona non decrescente e continua a destra.
* **Valore Atteso (Media Statistica):**
  $$\mathbb{E}[X] = \sum_{x \in \mathcal{X}} x \, p_X(x)$$
* **Teorema del Valore Atteso per Trasformazioni (LOTUS discreto):**
  Dato $Y = g(X)$:
  $$\mathbb{E}[g(X)] = \sum_{x \in \mathcal{X}} g(x) \, p_X(x)$$
  *(Non serve calcolare esplicitamente la PMF di $Y$ per trovarne la media!)*

---

### 2.2 Distribuzioni Notevoli Discrete: Guida all'Uso e Significato Fisico

Le distribuzioni notevoli non sono formule astratte, ma la formalizzazione matematica di precisi **meccanismi fisici di generazione dei dati**.

#### Mappa di Scelta Immediata: «Cosa sta misurando la variabile $X$?»

```text
                         COSA MISURA LA VARIABILE X?
                                     │
         ┌───────────────────────────┼───────────────────────────┐
         ▼                           ▼                           ▼
Un singolo evento            Una serie di prove           Eventi nel tempo/spazio
 (Sì / No)                   ripetute (successi)                 continuo
         │                           │                           │
   BERNOULLI                         │                        POISSON
                             ┌───────┴───────┐
                             ▼               ▼
                      Fisso le prove    Fisso il successo
                       e conto quanti    e conto quante prove
                          successi           devo fare
                             │               │
                         BINOMIALE       GEOMETRICA
```

---

#### 1. Distribuzione di Bernoulli: $\mathcal{B}(p)$
* **L'intuizione fisica**: È l'atomo elementare della probabilità: una singola prova con due soli esiti possibili, codificati convenzionalmente come **Successo ($1$)** con probabilità $p$, o **Insuccesso ($0$)** con probabilità $1-p$.
* **Perché esiste?** Perché rappresenta il "mattoncino base" per modellare qualsiasi fenomeno dicotomico e per costruire per somma le distribuzioni di conteggio.
* **PMF e Momenti**:
  $$p_X(1) = p, \quad p_X(0) = 1-p \implies p_X(k) = p^k (1-p)^{1-k} \quad (k \in \{0, 1\})$$
  $$\mathbb{E}[X] = p, \qquad \operatorname{Var}(X) = p(1-p)$$
* **Quando si usa all'esame?**
  * Singolo lancio di una moneta (anche non bilanciata).
  * Trasmissione di un singolo bit attraverso un canale binario simmetrico ($1$ se errato, $0$ se corretto).
  * **Variabile indicatrice**: data una partizione o un evento $A$, la variabile $I_A$ vale $1$ se $A$ accade e $0$ altrimenti ($\mathbb{E}[I_A] = \mathbb{P}(A)$).
* **Segnali nel testo**: *"Si consideri una prova con esito binario..."*, *"Sia $X \in \{0, 1\}$..."*.

---

#### 2. Distribuzione Binomiale: $\mathcal{B}(n, p)$
* **L'intuizione fisica**: Ripeti la prova di Bernoulli per un numero **fissato a priori** di $n$ volte, in modo indipendente e nelle stesse identiche condizioni. La variabile $X$ conta: **«Quanti successi ho totalizzato su questi $n$ tentativi?»**
* **Perché la formula è strutturata così?**
  $$p_X(k) = \underbrace{\binom{n}{k}}_{\text{in quanti modi diversi}} \cdot \underbrace{p^k}_{\text{i } k \text{ successi}} \cdot \underbrace{(1-p)^{n-k}}_{\text{gli } n-k \text{ insuccessi}}, \quad k \in \{0, 1, \dots, n\}$$
  Il coefficiente binomiale $\binom{n}{k}$ è indispensabile perché non importa in quali posizioni temporali si presentino i $k$ successi, ma solo che il loro conteggio finale sia $k$.
* **Le 3 condizioni per poterla applicare**:
  1. Il numero di prove $n$ è **costante e noto a priori**.
  2. Gli esiti di ogni singola prova sono mutualmente indipendenti.
  3. La probabilità di successo $p$ rimane rigorosamente costante ad ogni prova (estrazioni *con reimmissione*).
* **Momenti**:
  $$\mathbb{E}[X] = np, \qquad \operatorname{Var}(X) = np(1-p)$$
* **Quando si usa all'esame?**
  * Trasmissione di pacchetti di $n$ bit: calcolare la probabilità che si verifichino esattamente $k$ errori di trasmissione.
  * Controllo qualità: estrazione di un campione di $n$ prodotti con probabilità $p$ che ciascuno sia difettoso.
* **Segnali nel testo**: *"Su $n$ prove indipendenti..."*, *"Si eseguono $n$ lanci..."*, *"Un blocco di $n$ simboli..."*.

---

#### 3. Distribuzione Geometrica: $\mathcal{G}(p)$
* **L'intuizione fisica**: È la dinamica complementare alla Binomiale.
  * Nella Binomiale fissi le prove $n$ e conti i successi $k$.
  * Nella Geometrica **fissi l'obiettivo (il primo successo!)** e la variabile aleatoria $X$ è il **numero di tentativi necessari per ottenerlo**.
* **Perché la formula è strutturata così?**
  $$p_X(k) = (1-p)^{k-1} \cdot p, \quad k \in \{1, 2, 3, \dots\}$$
  Per fermarsi esattamente al tentativo $k$, devi aver necessariamente collezionato $k-1$ fallimenti consecutivi (ciascuno con probabilità $1-p$) e aver fatto centro al $k$-esimo tentativo (probabilità $p$). L'ordine qui è rigidamente prefissato, perciò **non c'è alcun coefficiente binomiale**.
* **Proprietà Cardine: Assenza di Memoria (*Memoryless* discreta)**:
  $$\mathbb{P}(X > n + k \mid X > n) = \mathbb{P}(X > k)$$
  Se hai già fallito $n$ volte, la probabilità di dover fare altri $k$ tentativi è identica a quella iniziale. Il sistema non accumula "stanchezza" o usura.
* **Momenti**:
  $$\mathbb{E}[X] = \frac{1}{p}, \qquad \operatorname{Var}(X) = \frac{1-p}{p^2}$$
* **Quando si usa all'esame?**
  * Protocolli di ritrasmissione dati (ARQ): quanti tentativi servono affinché un frame venga ricevuto correttamente.
  * Tentativi di accesso / login prima di inserire la credenziale esatta.
  * Affidabilità a tempo discreto: cicli di accensione prima del primo guasto.
* **Segnali nel testo**: *"Si ripete la prova fino al primo successo..."*, *"Numero di tentativi necessari affinché..."*.

---

#### 4. Distribuzione di Poisson: $\mathcal{P}(\lambda)$
* **L'intuizione fisica**: È la **legge degli eventi rari nel tempo o nello spazio continuo**.
  * Nasce come limite asintotico della Binomiale quando il numero potenziale di prove tende all'infinito ($n \to \infty$) e la probabilità del singolo evento diventa infinitesima ($p \to 0$), mentre il numero medio di eventi attesi $\lambda = n \cdot p$ resta finito e costante.
* **Perché è essenziale in informatica e ingegneria?**
  Perché nella realtà non si conosce quasi mai il numero totale potenziale di utenti $n$ (quante persone nel mondo potrebbero inviare una richiesta a un server?), ma si può misurare sperimentalmente la **frequenza media di arrivo $\lambda$** (es. $\lambda = 5$ richieste al secondo).
* **PMF e Momenti**:
  $$p_X(k) = \frac{\lambda^k}{k!} e^{-\lambda}, \quad k \in \mathbb{N}_0 = \{0, 1, 2, \dots\}$$
  $$\mathbb{E}[X] = \operatorname{Var}(X) = \lambda$$
  *(Media e varianza coincidono esattamente: questa è la "firma" inconfondibile della Poisson).*
* **Quando si usa all'esame?**
  * Arrivo di chiamate a un centralino, accessi HTTP a un server web, arrivo di pacchetti su un'interfaccia di rete.
  * Conteggio di difetti per unità di lunghezza (su fibra ottica) o per unità di superficie (su wafer di silicio).
  * **Esercizio tipico d'esame (stile Mattera)**: Viene assegnata una PMF del tipo:
    $$P(X = k) = A \frac{c^k}{k!}, \quad k \in \mathbb{N}_0$$
    Riconoscendo la serie esponenziale $\sum_{k=0}^{\infty} \frac{c^k}{k!} = e^c$, si impone la normalizzazione:
    $$A \sum_{k=0}^{\infty} \frac{c^k}{k!} = A e^c = 1 \implies A = e^{-c}$$
    e si deduce che $X \sim \mathcal{P}(c)$.
* **Segnali nel testo**: *"In media avvengono $\lambda$ eventi per unità di tempo..."*, *"Eventi indipendenti e rari..."*, *"Formula con $k!$ a denominatore e potenze a numeratore"*.

---

#### 5. Distribuzione Uniforme Discreta: $\mathcal{U}(\{x_1, \dots, x_M\})$
* **L'intuizione fisica**: Discende dal *principio di ragione insufficiente* di Laplace: quando uno spazio di possibilità finite $M$ non presenta alcun elemento fisico, simmetrico o logico che favorisca un esito rispetto a un altro, ciascun esito ha la stessa identica probabilità.
* **PMF e Momenti**:
  $$p_X(x_i) = \frac{1}{M}, \quad \forall i \in \{1, \dots, M\}$$
  $$\mathbb{E}[X] = \frac{1}{M} \sum_{i=1}^M x_i$$
  Se i valori sono gli interi consecutivi $\{0, 1, \dots, M-1\}$:
  $$\mathbb{E}[X] = \frac{M-1}{2}, \qquad \operatorname{Var}(X) = \frac{M^2 - 1}{12}$$
* **Quando si usa all'esame?**
  * Lancio di dadi a $M$ facce non truccati o estrazione di carte.
  * Scelta pseudo-casuale di un canale di trasmissione o di uno slot temporale (TDMA) tra $M$ disponibili.
  * Funzioni hash ideali con partizionamento equo tra $M$ bucket.
* **Segnali nel testo**: *"Equiprobabili"*, *"Scelta puramente casuale tra $M$ opzioni"*, *"Dado non truccato"*.

---

#### Tabella Riassuntiva Comparativa per le Prove d'Esame

| Distribuzione | Cosa conta la variabile $X$? | Parametri | Alfabeto $\mathcal{X}$ | PMF $p_X(k)$ | Firma distintiva |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Bernoulli** | Singola prova dicotomica (Sì/No) | $p$ | $\{0, 1\}$ | $p^k (1-p)^{1-k}$ | $\mathbb{E}[X] = p$ |
| **Binomiale** | Numero di successi su $n$ prove | $n, p$ | $\{0, 1, \dots, n\}$ | $\binom{n}{k} p^k (1-p)^{n-k}$ | $n$ fissato a priori, con reimmissione |
| **Geometrica** | Prove necessarie fino al 1° successo | $p$ | $\{1, 2, 3, \dots\}$ | $(1-p)^{k-1} p$ | Assenza di memoria a tempo discreto |
| **Poisson** | Eventi in tempo/spazio continuo | $\lambda$ | $\{0, 1, 2, \dots\}$ | $\frac{\lambda^k}{k!} e^{-\lambda}$ | $\mathbb{E}[X] = \operatorname{Var}(X) = \lambda$ |
| **Uniforme** | Scelta perfettamente equiprobabile | $M$ | $\{x_1, \dots, x_M\}$ | $\frac{1}{M}$ | Tutte le masse sono identiche |

### 2.3 PMF Condizionale e Funzioni di Variabili Discrete

#### PMF Condizionata da un evento $B$
$$p_{X \mid B}(x) = \mathbb{P}(X = x \mid B) = \frac{\mathbb{P}(\{X = x\} \cap B)}{\mathbb{P}(B)}$$
* Media condizionata: $\mathbb{E}[X \mid B] = \sum_{x} x \, p_{X \mid B}(x)$.

#### Legge della Probabilità Totale per PMF e Medie
Data una partizione $\{E_m\}$ di $\Omega$:
$$p_X(x) = \sum_{m=1}^M p_{X \mid E_m}(x)\mathbb{P}(E_m), \qquad \mathbb{E}[X] = \sum_{m=1}^M \mathbb{E}[X \mid E_m]\mathbb{P}(E_m)$$

#### Trasformazione di variabile discreta $Y = g(X)$
* Se $g$ è **biunivoca** (invertibile): $p_Y(y) = p_X(g^{-1}(y))$.
* Se $g$ **non è iniettiva**:
  $$p_Y(y) = \sum_{x \in \mathcal{X} \,:\, g(x) = y} p_X(x)$$

---

# Parte III: Momenti, Disuguaglianze e Variabili Multiple Discrete

### 3.1 Varianza e Proprietà di Varianza
$$\operatorname{Var}(X) = \sigma_X^2 = \mathbb{E}[(X - \mathbb{E}[X])^2] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$
* **Deviazione standard:** $\sigma_X = \sqrt{\operatorname{Var}(X)}$
* **Proprietà di scala e traslazione:**
  $$\operatorname{Var}(aX + b) = a^2 \operatorname{Var}(X)$$
  $$\sigma_{aX + b} = |a|\sigma_X$$

---

### 3.2 Disuguaglianze Notevoli (Caratterizzazione Parziale)

#### Disuguaglianza di Markov
Applicabile **solo a variabili aleatorie non negative** ($X \ge 0$) e per soglie $a > 0$:
$$\mathbb{P}(X \ge a) \le \frac{\mathbb{E}[X]}{a}$$

#### Disuguaglianza di Chebyshev
Applicabile a **qualsiasi variabile aleatoria** di cui si conoscano media $\mu = \mathbb{E}[X]$ e varianza $\sigma^2 = \operatorname{Var}(X)$, per ogni $\epsilon > 0$:
$$\mathbb{P}(|X - \mu| \ge \epsilon) \le \frac{\sigma^2}{\epsilon^2} \iff \mathbb{P}(|X - \mu| < \epsilon) \ge 1 - \frac{\sigma^2}{\epsilon^2}$$

> **Quando si usa all'esame:**
> * Quando il testo chiede di delimitare o maggiorare la probabilità di una coda (es. $\mathbb{P}(|X - \mu| \ge 2\sigma)$) **senza conoscere la distribuzione esatta** della variabile aleatoria.

---

### 3.3 Variabili Multiple Discrete $(X, Y)$

#### PMF Congiunta
$$p_{X, Y}(x, y) = \mathbb{P}(X = x, Y = y), \quad \sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p_{X, Y}(x, y) = 1$$

#### Marginalizzazione
$$p_X(x) = \sum_{y \in \mathcal{Y}} p_{X, Y}(x, y), \qquad p_Y(y) = \sum_{x \in \mathcal{X}} p_{X, Y}(x, y)$$
*(Nelle tabelle d'esame: basta sommare lungo le righe o le colonne!)*

#### Criterio di Indipendenza Stocastica
Due variabili discrete $X$ e $Y$ sono indipendenti ($X \perp Y$) se e solo se:
$$p_{X, Y}(x, y) = p_X(x) \cdot p_Y(y) \quad \forall (x, y) \in \mathcal{X} \times \mathcal{Y}$$
> **All'esame:** Per dimostrare che NON sono indipendenti, basta trovare **una sola coppia $(x_0, y_0)$** per cui $p_{X,Y}(x_0, y_0) \neq p_X(x_0) p_Y(y_0)$. Spesso salta all'occhio un valore congiunto nullo ($p_{X,Y} = 0$) dove le due marginali sono invece strettamente positive!

#### Covarianza e Correlazione
* **Covarianza:**
  $$\operatorname{Cov}(X, Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$$
  dove $\mathbb{E}[XY] = \sum_x \sum_y x \cdot y \cdot p_{X, Y}(x, y)$.
* **Proprietà:**
  * Se $X \perp Y \implies \operatorname{Cov}(X, Y) = 0$ (v.a. incorrelate). *(Attenzione: l'inverso non è sempre vero!)*
  * $\operatorname{Cov}(X, X) = \operatorname{Var}(X)$.
* **Varianza della somma:**
  $$\operatorname{Var}(aX + bY) = a^2 \operatorname{Var}(X) + b^2 \operatorname{Var}(Y) + 2ab\operatorname{Cov}(X, Y)$$
  Se $X$ e $Y$ sono indipendenti (o incorrelate, $\operatorname{Cov}(X, Y) = 0$):
  $$\operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y)$$
* **Coefficiente di correlazione di Pearson:**
  $$\rho_{XY} = \frac{\operatorname{Cov}(X, Y)}{\sigma_X \sigma_Y}, \quad -1 \le \rho_{XY} \le 1$$

---

# Parte IV: Dal Discreto al Continuo (Capitolo 5, fino a 5.1.9)

### 4.1 Il Passaggio Concettuale: Probabilità su un Intervallo (Sez. 5.1.1)

Quando lo spazio campionario $\Omega \subseteq \mathbb{R}$ è continuo:
* **La Regola d'Oro:** Per qualsiasi variabile aleatoria continua $X$, **la probabilità di assumere un singolo valore puntuale è sempre nulla**:
  $$\mathbb{P}(X = x) = 0 \quad \forall x \in \mathbb{R}$$
* Pertanto, ha senso calcolare la probabilità solo su **intervalli**:
  $$\mathbb{P}(a \le X \le b) = \mathbb{P}(a < X \le b) = \mathbb{P}(a \le X < b) = \mathbb{P}(a < X < b)$$
  *(Includere o escludere gli estremi non cambia il risultato numerico!)*

---

### 4.2 Densità di Probabilità - PDF (Sez. 5.1.2)

#### Definizione Matematica
La PDF $f_X(x)$ è definita tramite il limite del rapporto tra la massa di probabilità contenuta in un intorno centrato e l'ampiezza dell'intorno $\Delta x$:
$$\boxed{f_X(x) = \lim_{\Delta x \to 0} \frac{\mathbb{P}\left(x - \frac{\Delta x}{2} \le X \le x + \frac{\Delta x}{2}\right)}{\Delta x}}$$

#### Calcolo della Probabilità come Area
$$\mathbb{P}(a \le X \le b) = \int_{a}^{b} f_X(x) dx$$

#### I Due Vincoli Costitutivi della PDF
1. **Non-negatività:**
   $$f_X(x) \ge 0 \quad \forall x \in \mathbb{R}$$
2. **Normalizzazione (Integrale Unitario):**
   $$\int_{-\infty}^{+\infty} f_X(x) dx = 1$$

> **Errore tipico da evitare all'esame:**
> La PDF $f_X(x)$ **NON è una probabilità**: può benissimo essere maggiore di 1 (ad esempio, per una variabile uniforme su $[0, 0.1]$, la densità vale $f_X(x) = 10$). È solo l'area sottesa all'integrale a dover valere 1.

---

### 4.3 Funzione di Ripartizione - CDF (Sez. 5.1.3)

#### Definizione
$$F_X(x) = \mathbb{P}(X \le x) = \int_{-\infty}^{x} f_X(t) dt$$

#### Relazione Fondamentale con la PDF
Nei punti in cui $f_X(x)$ è continua:
$$f_X(x) = \frac{d}{dx} F_X(x)$$

#### Probabilità in un Intervallo tramite CDF
$$\mathbb{P}(a < X \le b) = F_X(b) - F_X(a)$$

#### CCDF (Complementary CDF / Funzione di Sopravvivenza)
$$F_X^c(x) = \mathbb{P}(X > x) = 1 - F_X(x) = \int_{x}^{+\infty} f_X(t) dt$$

#### Proprietà della CDF Continua
1. $0 \le F_X(x) \le 1$ per ogni $x \in \mathbb{R}$.
2. Monotona non decrescente: se $x_1 < x_2 \implies F_X(x_1) \le F_X(x_2)$.
3. Continua su tutto $\mathbb{R}$ (non presenta gradini/salti verticali, tipici invece delle variabili discrete).
4. Limiti asintotici:
   $$\lim_{x \to -\infty} F_X(x) = 0, \qquad \lim_{x \to +\infty} F_X(x) = 1$$

---

### 4.4 Media Statistica per Variabili Continue (Sez. 5.1.4)

$$\mathbb{E}[X] = \int_{-\infty}^{+\infty} x \, f_X(x) dx$$
* **Condizione di esistenza:** l'integrale deve convergere assolutamente:
  $$\int_{-\infty}^{+\infty} |x| f_X(x) dx < \infty$$
* **Valore atteso di una trasformazione (LOTUS continuo):**
  $$\mathbb{E}[g(X)] = \int_{-\infty}^{+\infty} g(x) \, f_X(x) dx$$

---

### 4.5 Distribuzioni Notevoli Continue (Sez. 5.1.5 - 5.1.8)

#### 1. Distribuzione Uniforme Continua: $X \sim \mathcal{U}(a, b)$ con $a < b$
* **Supporto:** $[a, b]$
* **PDF:**
  $$f_X(x) = \begin{cases} \frac{1}{b - a} & a \le x \le b \\ 0 & \text{altrove} \end{cases} = \frac{1}{b - a} [u(x - a) - u(x - b)]$$
* **CDF:**
  $$F_X(x) = \begin{cases} 0 & x < a \\ \frac{x - a}{b - a} & a \le x \le b \\ 1 & x > b \end{cases}$$
* **Media:** $\mathbb{E}[X] = \frac{a + b}{2}$
* **Varianza:** $\operatorname{Var}(X) = \frac{(b - a)^2}{12}$
* **Quando si usa:** Errore di quantizzazione round-off, fase casuale di un segnale sinusoidale ($\mathcal{U}(-\pi, \pi)$), arrivi casuali senza preferenza.

---

#### 2. Distribuzione Esponenziale: $X \sim \mathcal{E}(\lambda)$ con $\lambda > 0$
* **Supporto:** $[0, +\infty)$
* **Cosa indica $\lambda$ (Lambda)?**
  * **Significato fisico:** $\lambda$ è il **tasso medio di accadimento** (*rate parameter* o frequenza media degli eventi per unità di tempo o di spazio). Ad esempio: $\lambda = 3 \text{ richieste/secondo}$ o $\lambda = 0.01 \text{ guasti/ora}$.
  * **Unità di misura:** è l'inverso dell'unità di misura di $X$, ovvero $[\text{tempo}]^{-1}$.
  * **Legame fondamentale con la media:** $\mathbb{E}[X] = \frac{1}{\lambda}$. 
    * Se il tasso è $\lambda = 2 \text{ pacchetti/secondo}$, il tempo medio di attesa tra due pacchetti è $\frac{1}{2} = 0.5 \text{ secondi}$.
    * *All'aumentare di $\lambda$*, gli eventi avvengono più frequentemente e il tempo medio di attesa si accorcia ($\mathbb{E}[X] \to 0$).
  * **Effetto sulla forma della PDF:**
    * L'altezza massima del picco in $x = 0$ è pari proprio a $\lambda$ ($f_X(0) = \lambda$).
    * Un $\lambda$ alto genera una curva che parte molto in alto e decade ripidamente a zero (attese brevi concentrate vicino a 0).
    * Un $\lambda$ basso genera una curva piatta e allungata (attese mediamente più lunghe).
  * **Tasso di guasto costante (*Hazard rate*):** $h(x) = \frac{f_X(x)}{1 - F_X(x)} = \frac{\lambda e^{-\lambda x}}{e^{-\lambda x}} = \lambda$. Significa che l'intensità di rischio non varia nel tempo (nessun invecchiamento o usura).
* **PDF:**
  $$f_X(x) = \lambda e^{-\lambda x} u(x)$$
* **CDF:**
  $$F_X(x) = (1 - e^{-\lambda x}) u(x)$$
* **Coda (CCDF):** $\mathbb{P}(X > x) = e^{-\lambda x}$ (per $x \ge 0$)
* **Media:** $\mathbb{E}[X] = \frac{1}{\lambda}$
* **Varianza:** $\operatorname{Var}(X) = \frac{1}{\lambda^2}$
* **Proprietà Cardine - Assenza di Memoria (*Memoryless*):**
  $$\mathbb{P}(X > s + t \mid X > s) = \mathbb{P}(X > t) \quad \forall s, t \ge 0$$
* **Quando si usa:** Tempo di attesa tra eventi in processi di Poisson, durata fino al guasto per shock esterni senza usura, tempo di servizio di una coda.

---

#### 3. Distribuzione Laplaciana (Doppia Esponenziale): $X \sim \mathcal{L}(\lambda)$ con $\lambda > 0$
* **Supporto:** $\mathbb{R} = (-\infty, +\infty)$
* **Cosa indica $\lambda$ (Lambda)?**
  * **Significato matematico:** $\lambda$ è il **parametro di decadimento (o fattore di scala)** delle due ali esponenziali simmetriche attorno a zero ($e^{-\lambda |x|}$).
  * **Ruolo sulla dispersione:** Regola la larghezza della campana cuspidale (a punta):
    * Poiché la varianza è $\operatorname{Var}(X) = \frac{2}{\lambda^2}$, più grande è $\lambda$, più la campana è stretta e appuntita attorno a $x = 0$ (minore incertezza/dispersione).
    * Al contrario, un $\lambda$ piccolo rende le code più pesanti e allargate verso $\pm\infty$.
  * Spesso in letteratura tecnica si usa il parametro di scala $b = \frac{1}{\lambda}$, per cui la densità si riscrive come $\frac{1}{2b} e^{-|x|/b}$.
* **PDF:**
  $$f_X(x) = \frac{\lambda}{2} e^{-\lambda |x|}$$
* **CDF:**
  $$F_X(x) = \begin{cases} \frac{1}{2} e^{\lambda x} & x \le 0 \\ 1 - \frac{1}{2} e^{-\lambda x} & x > 0 \end{cases}$$
* **Media:** $\mathbb{E}[X] = 0$ (perché $x f_X(x)$ è una funzione dispari integrata su intervallo simmetrico).
* **Varianza:** $\operatorname{Var}(X) = \frac{2}{\lambda^2}$
* **Quando si usa:** Modellazione di rumore impulsivo, coefficienti di compressione audio/video (es. DCT/wavelet nel JPEG/MP3), errori a code più larghe della Gaussiana.

---

#### 4. Distribuzione di Cauchy: $X \sim \mathcal{C}(a, b)$ con $a \in \mathbb{R}$ e $b > 0$
* **Supporto:** $\mathbb{R} = (-\infty, +\infty)$
* **Parametri:** $a$ è la posizione (picco/moda/mediana), $b$ è la scala.
* **PDF:**
  $$f_X(x) = \frac{1}{b\pi} \frac{1}{1 + \left(\frac{x - a}{b}\right)^2}$$
* **CDF:**
  $$F_X(x) = \frac{1}{2} + \frac{1}{\pi} \arctan\left(\frac{x - a}{b}\right)$$
* **Media:** **NON DEFINITA** (l'integrale diverge: code pesanti $\sim \frac{1}{x^2}$).
* **Valore Principale di Cauchy:**
  $$\lim_{H \to \infty} \int_{-H}^{H} x f_X(x) dx = a$$
* **Quando si usa:** Rapporto tra due variabili gaussiane standard $Z = X/Y$ con $X, Y \sim \mathcal{N}(0, 1)$; proiezione su parete di un fascio luminoso rotante ad angolo uniforme (problema del faro); risonanze quantistiche / decadimenti (distribuzione di Breit-Wigner).

---

### 4.6 Legge della Probabilità Totale per PDF e Medie (Sez. 5.1.9, Pag. 93)

Data una partizione $\{E_m\}_{m=1}^M$ dello spazio campionario $\Omega$:

#### 1. Per la Funzione di Densità (PDF)
$$\boxed{f_X(x) = \sum_{m=1}^{M} f_{X \mid E_m}(x) \mathbb{P}(E_m)}$$

#### 2. Per la Funzione di Ripartizione (CDF)
$$\boxed{F_X(x) = \sum_{m=1}^{M} F_{X \mid E_m}(x) \mathbb{P}(E_m)}$$

#### 3. Per il Valore Atteso (Medie Condizionate)
$$\boxed{\mathbb{E}[X] = \sum_{m=1}^{M} \mathbb{E}[X \mid E_m] \mathbb{P}(E_m) = \sum_{m=1}^{M} \mathbb{P}(E_m) \int_{\mathbb{R}} x f_{X \mid E_m}(x) dx}$$

> **Quando si usa all'esame:**
> * Sistemi a commutazione o canali di trasmissione che trasmettono segnali diversi a seconda dell'ipotesi attiva ($H_1$ o $H_2$ equiprobabili).
> * Sorgenti miste in cui una componente viene scelta casualmente da più generatori (modelli a mistura / *mixture models*).

---

# Parte V: Prontuario Operativo d'Esame "Stile Mattera"

Questa sezione sintetizza le risposte standard ai quesiti che si ripetono regolarmente nei compiti d'esame raccolti in `esami_calcolo_probabilita.pdf`.

```
                  ┌──────────────────────────────────────────────┐
                  │ TIPOLOGIA DI ESERCIZIO ALL'ESAME CPS         │
                  └──────────────────────┬───────────────────────┘
                                         │
                 ┌───────────────────────┴───────────────────────┐
                 ▼                                               ▼
     ┌────────────────────────┐                     ┌────────────────────────┐
     │   ESERCIZIO 1:         │                     │   ESERCIZIO 2:         │
     │   Variabili Discrete   │                     │   Variabili Continue   │
     └───────────┬────────────┘                     └───────────┬────────────┘
                 │                                               │
     ├─ Marginale: sommatoria righe/colonne          ├─ Normalizzazione A: ∫ f(x)dx = 1
     ├─ Somma T = X + Y: unisci le coppie           ├─ Prob. puntuale: SEMPRE ZERO
     ├─ Condizionata: P(T=t ∩ Cond) / P(Cond)        ├─ Trasformata Y = g(X)
     └─ Indipendenza: P(X,Y) == P(X)P(Y)?           ├─ Moda (f'=0) e Mediana (F=1/2)
                                                     └─ Decisione Ottima: MAP / ML
```

---

### Esercizio Tipico 1: Variabili Discrete (Tabelle Congiunte)

**Dati tipici:** Alfabeti $X \in \{0, 1\}$, $Y \in \{0, 2\}$ con probabilità congiunte fornite.

#### 1. Determinare le PMF Marginali di $X$ e $Y$
* **Procedimento:** Costruisci la tabella a doppia entrata. La probabilità marginale $p_X(x)$ è la somma degli elementi sulla riga corrispondente; $p_Y(y)$ è la somma lungo la colonna.
* **Verifica:** Assicurati sempre che $\sum p_X(x) = 1$ e $\sum p_Y(y) = 1$.

#### 2. Determinare la PMF della Somma $T = X + Y$
* **Procedimento:**
  1. Elenca tutte le coppie $(x, y)$ con probabilità congiunta non nulla.
  2. Calcola il valore di $t = x + y$ per ogni coppia.
  3. Raggruppa i valori identici di $t$ sommando le relative probabilità congiunte:
     $$p_T(t) = \sum_{(x, y) \,:\, x + y = t} p_{X, Y}(x, y)$$

#### 3. Determinare la PMF Condizionata dato un Evento (es. $X \cdot Y = 0$ oppure $|V - 9/2| < 1$)
* **Procedimento:**
  1. Identifica l'evento condizionante $C$ (es. $C = \{X \cdot Y = 0\}$).
  2. Calcola $\mathbb{P}(C)$ sommando le probabilità congiunte delle coppie che soddisfano la condizione.
  3. Per ciascun valore $t$ di $T$, calcola l'intersezione $\{T = t\} \cap C$.
  4. Applica la formula:
     $$p_{T \mid C}(t) = \frac{\mathbb{P}(\{T = t\} \cap C)}{\mathbb{P}(C)}$$

#### 4. Verificare se $X$ e $Y$ sono Indipendenti
* **Procedimento:**
  * Calcola il prodotto $p_X(x) \cdot p_Y(y)$.
  * Se per **anche una sola coppia** $(x, y)$ si ha $p_{X, Y}(x, y) \neq p_X(x) \cdot p_Y(y)$, rispondi formalmente:  
    *"Le variabili non sono indipendenti in quanto $p_{X, Y}(x_0, y_0) \neq p_X(x_0) p_Y(y_0)$"*.

---

### Esercizio Tipico 2: Variabili Continue

**Dati tipici:** $f_X(x) = A x e^{-x^2} u(x)$, dove $u(x)$ è il gradino unitario:
$$u(x) = \begin{cases} 1 & x \ge 0 \\ 0 & x < 0 \end{cases}$$

#### 1. Calcolo del Parametro di Normalizzazione $A$
* **Formula:**
  $$\int_{-\infty}^{+\infty} f_X(x) dx = 1$$
* **Procedimento:**
  * Il gradino $u(x)$ imposta l'estremo inferiore dell'integrale a $0$:
    $$\int_{0}^{+\infty} A x e^{-x^2} dx = 1$$
  * Sostituzione immediata: $t = x^2 \implies dt = 2x dx \implies x dx = \frac{dt}{2}$:
    $$\frac{A}{2} \int_{0}^{+\infty} e^{-t} dt = \frac{A}{2} \left[ -e^{-t} \right]_0^{+\infty} = \frac{A}{2} (0 - (-1)) = \frac{A}{2}$$
  * Imponendo $\frac{A}{2} = 1$, si ottiene **$A = 2$**.

---

#### 2. La Domanda Tranello: Probabilità di Valori Discreti
* **Domanda tipica:** *"Determinare la probabilità che $Y \in \{0, \ln 3\}$"*.
* **Risposta istantanea e giustificazione d'esame:**
  $$\mathbb{P}(Y \in \{0, \ln 3\}) = \mathbb{P}(Y = 0) + \mathbb{P}(Y = \ln 3) = 0 + 0 = \mathbf{0}$$
  *Motivazione:* $Y$ è una variabile aleatoria continua, pertanto la probabilità associata a un qualsiasi insieme finito o numerabile di singoli punti è **identicamente nulla**.

---

#### 3. Calcolo e Confronto tra Moda e Mediana

##### A. Moda ($x_{\text{mode}}$ o $y_{\text{mode}}$)
La moda è il punto in cui la PDF assume il suo **valore massimo globale**.
* Si pone la derivata prima della PDF uguale a zero:
  $$\frac{d}{dx} f_X(x) = 0$$
* *Trucco operativo:* se la densità contiene un esponenziale $f_X(x) = 2x e^{-x^2}$, conviene calcolare la derivata del logaritmo naturale $\frac{d}{dx} \ln f_X(x) = 0$, oppure derivare direttamente:
  $$\frac{d}{dx}[2x e^{-x^2}] = 2 e^{-x^2} + 2x(-2x)e^{-x^2} = 2 e^{-x^2} (1 - 2x^2) = 0$$
  Poiché $e^{-x^2} \neq 0$, deve essere $1 - 2x^2 = 0 \implies x^2 = \frac{1}{2} \implies \mathbf{x_{\text{mode}} = \frac{1}{\sqrt{2}} = \frac{\sqrt{2}}{2}}$.

##### B. Mediana ($m$)
La mediana è il punto che divide l'area sottesa alla PDF esattamente a metà ($50\%$ a sinistra e $50\%$ a destra):
$$F_X(m) = \mathbb{P}(X \le m) = \int_{-\infty}^{m} f_X(x) dx = \frac{1}{2}$$
* Calcolo dell'integrale:
  $$\int_{0}^{m} 2x e^{-x^2} dx = \left[ -e^{-x^2} \right]_0^m = 1 - e^{-m^2} = \frac{1}{2}$$
* Risoluzione:
  $$e^{-m^2} = \frac{1}{2} \implies -m^2 = \ln\left(\frac{1}{2}\right) = -\ln(2) \implies m^2 = \ln(2) \implies \mathbf{m = \sqrt{\ln(2)}}$$

##### C. Confronto
Per stabilire quale grandezza sia maggiore:
* $\text{Moda} = \sqrt{\frac{1}{2}} = \sqrt{0.5} \approx 0.7071$
* $\text{Mediana} = \sqrt{\ln(2)} \approx \sqrt{0.6931} \approx 0.8325$
* Conclusione: $\mathbf{m > x_{\text{mode}}}$ (la mediana è strettamente maggiore della moda).

---

#### 4. Test di Decisione Binaria (MAP e ML)
Nel contesto delle prove d'esame con due ipotesi $H_1, H_2$ e osservazione $Z$:

* **Rapporto di Verosimiglianza (Likelihood Ratio):**
  $$\Lambda(z) = \frac{f_{Z \mid H_1}(z)}{f_{Z \mid H_2}(z)} \begin{matrix} \text{decidi } H_1 \\ \gtrless \\ \text{decidi } H_2 \end{matrix} \eta$$
* **Soglia di decisione ottima (Criterio MAP - Maximum A Posteriori):**
  $$\eta_{\text{MAP}} = \frac{\mathbb{P}(H_2)}{\mathbb{P}(H_1)}$$
* Se le ipotesi sono **equiprobabili** ($\mathbb{P}(H_1) = \mathbb{P}(H_2) = \frac{1}{2}$), il decisore MAP coincide con il decisore **ML (Maximum Likelihood)** e la soglia è unitaria:
  $$\eta_{\text{ML}} = 1 \implies \text{si sceglie } H_1 \text{ se } f_{Z \mid H_1}(z) > f_{Z \mid H_2}(z)$$
