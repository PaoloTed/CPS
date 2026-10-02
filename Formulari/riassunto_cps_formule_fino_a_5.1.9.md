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
  *(Non serve calcolare esplicitamente la PMF di $Y$ per tr### 2.2 Distribuzioni Notevoli Discrete: Guida Completa alla Scelta e Significato Fisico

Le distribuzioni notevoli non sono formule da memorizzare passivamente, ma la formalizzazione matematica di precisi **meccanismi fisici di generazione dei dati**. 

All'esame, per individuare all'istante quale distribuzione discreta utilizzare, poniti queste **tre domande sequenziali**:
1. *È una sola prova con esito dicotomico?* $\implies$ **Bernoulli**
2. *È una serie di prove indipendenti con probabilità costante $p$?*
   * **Se il numero di prove $n$ è fissato a priori** e conto i successi $\implies$ **Binomiale**
   * **Se il successo è fissato** (voglio il primo!) e conto quante prove servono $\implies$ **Geometrica**
3. *Sto contando eventi indipendenti e rari che arrivano in un intervallo continuo (tempo/spazio)?* $\implies$ **Poisson**


#### 1. Distribuzione di Bernoulli: $\mathcal{B}(p)$
* **Meccanismo fisico**: Una singola prova con due soli esiti possibili: **Successo ($1$)** con probabilità $p$, oppure **Insuccesso ($0$)** con probabilità $1-p$.
* **PMF e Momenti**:
  $$p_X(1) = p, \quad p_X(0) = 1-p \implies p_X(k) = p^k (1-p)^{1-k} \quad (k \in \{0, 1\})$$
  $$\mathbb{E}[X] = p, \qquad \operatorname{Var}(X) = p(1-p)$$
* **Quando si usa all'esame?**
  * Singolo lancio di una moneta (anche truccata).
  * Trasmissione di un singolo bit attraverso un canale rumoroso ($1$ se errato, $0$ se corretto).
  * **Variabile indicatrice di un evento $A$ ($I_A$ o $\mathbf{1}_A$)**: vale $1$ se $A$ accade e $0$ altrimenti. Proprietà fondamentale: $\mathbb{E}[I_A] = \mathbb{P}(A)$ e $\operatorname{Var}(I_A) = \mathbb{P}(A)(1-\mathbb{P}(A))$.
* **Frasi sentinella nel testo**: *"Si consideri una singola prova con esito binario..."*, *"Sia $X$ l'indicatore dell'evento $A$..."*, *"Un bit trasmesso..."*.

---

#### 2. Distribuzione Binomiale: $\mathcal{B}(n, p)$
* **Meccanismo fisico**: Si ripete la prova di Bernoulli per un numero **noto e fissato a priori di $n$ volte**, in modo rigorosamente indipendente e con probabilità di successo $p$ identica ad ogni prova. La variabile $X$ conta: **«Quanti successi ho ottenuto in questi $n$ tentativi?»**
* **Perché la formula è strutturata così?**
  $$p_X(k) = \underbrace{\binom{n}{k}}_{\text{in quanti modi diversi}} \cdot \underbrace{p^k}_{\text{i } k \text{ successi}} \cdot \underbrace{(1-p)^{n-k}}_{\text{gli } n-k \text{ insuccessi}}, \quad k \in \{0, 1, \dots, n\}$$
  Il coefficiente binomiale $\binom{n}{k} = \frac{n!}{k!(n-k)!}$ conta in quanti ordini temporali distinti i $k$ successi possono distribuirsi all'interno degli $n$ slot di prova.
* **Le 3 condizioni tassative di applicabilità**:
  1. Numero di prove $n$ **costante e fissato a priori** (non dipende dagli esiti).
  2. Esiti delle prove **mutualmente indipendenti**.
  3. Probabilità $p$ costante ad ogni prova (ad es. estrazioni **con reimmissione**).
* **Momenti**:
  $$\mathbb{E}[X] = np, \qquad \operatorname{Var}(X) = np(1-p)$$
* **Quando si usa all'esame?**
  * Trasmissione di pacchetti o blocchi di $n$ bit: probabilità di avere $k$ bit errati.
  * Collaudo di lotti industriali: conteggio pezzi difettosi su un campione estratto di $n$ pezzi.
* **Frasi sentinella nel testo**: *"Su $n$ prove indipendenti..."*, *"Si eseguono $n$ lanci consecutivi..."*, *"Un pacchetto di $n$ bit..."*.
* **La trappola classica d'esame («Almeno un successo»)**:
  Se il testo chiede *"calcolare la probabilità che si verifichi **almeno un successo** su $n$ tentativi"*, non sommare $\sum_{k=1}^n \binom{n}{k}\dots$, ma passa istantaneamente all'evento complementare:
  $$\mathbb{P}(X \ge 1) = 1 - \mathbb{P}(X = 0) = 1 - \binom{n}{0}p^0(1-p)^n = 1 - (1-p)^n$$

---

#### 3. Distribuzione Geometrica: $\mathcal{G}(p)$
* **Meccanismo fisico**: È la prospettiva duale della Binomiale:
  * Nella Binomiale **fissi le prove $n$** e conti quanti successi ottieni.
  * Nella Geometrica **fissi il successo (il primo!)** e conti **quante prove devi effettuare prima di ottenerlo**.
  * Qui il numero di tentativi $X$ è aleatorio e potenzialmente illimitato: $\mathcal{X} = \{1, 2, 3, \dots\}$.
* **Perché la formula è strutturata così?**
  $$p_X(k) = (1-p)^{k-1} \cdot p, \quad k \in \{1, 2, 3, \dots\}$$
  Per fermarsi esattamente al tentativo $k$, devi aver collezionato una sequenza obbligata di $k-1$ fallimenti consecutivi seguiti dal successo finale al tentativo $k$. L'ordine temporale è unico e rigido, dunque **non c'è alcun coefficiente binomiale**.
* **Proprietà Cardine: Assenza di Memoria (*Memoryless* discreta)**:
  $$\mathbb{P}(X > n + k \mid X > n) = \mathbb{P}(X > k) = (1-p)^k$$
  *Significato operativo*: Se hai già tentato $n$ volte senza successo, il fatto di aver fallito nel passato non aumenta né riduce la probabilità di successo futuro. Il sistema riparte da zero come se fosse la prima prova.
* **Momenti**:
  $$\mathbb{E}[X] = \frac{1}{p}, \qquad \operatorname{Var}(X) = \frac{1-p}{p^2}$$
* **Quando si usa all'esame?**
  * Protocolli di ritrasmissione a tempo discreto (es. ARQ Stop-and-Wait): numero di invii fino al primo ACK ricevuto.
  * Tentativi di connessione o di autenticazione fino al primo accesso riuscito.
  * Prove di vita a cicli discreti (accensioni prima del primo guasto).
* **Frasi sentinella nel testo**: *"Si ripete l'esperimento finché non si ottiene un successo per la prima volta..."*, *"Numero di tentativi necessari per..."*, *"Al primo successo il processo si arresta..."*.

---

#### 4. Distribuzione di Poisson: $\mathcal{P}(\lambda)$
* **Meccanismo fisico**: È la **legge degli eventi rari nel continuo temporale o spaziale**.
  * Nasce come limite asintotico della Binomiale quando il numero potenziale di prove tende a infinito ($n \to \infty$) e la probabilità del singolo evento diventa infinitesima ($p \to 0$), mantenendo costante e finito il prodotto $\lambda = n \cdot p$.
* **Perché è essenziale in informatica e telecomunicazioni?**
  Perché in un sistema reale (es. un server web o una cella radio) non si conosce il numero totale $n$ di utenti connessi, ma si misura sperimentalmente il **tasso medio di arrivo $\lambda$** (es. $\lambda = 5 \text{ pacchetti al millisecondo}$).
* **PMF e Momenti**:
  $$p_X(k) = \frac{\lambda^k}{k!} e^{-\lambda}, \quad k \in \mathbb{N}_0 = \{0, 1, 2, \dots\}$$
  $$\mathbb{E}[X] = \operatorname{Var}(X) = \lambda$$
  *(Uguaglianza tra media e varianza: è la firma inconfondibile della distribuzione di Poisson).*
* **Quando si usa all'esame?**
  * Conteggio di arrivi: chiamate a un centralino, accessi HTTP a un server web, interruzioni hardware per secondo.
  * Conteggio difetti: numero di imperfezioni su un cavo in fibra ottica di lunghezza fissata.
  * **Tipico quesito d'esame (Stile Mattera)**: Viene assegnata una PMF su $\mathbb{N}_0$ con un parametro ignoto $A$:
    $$P(X = k) = A \frac{c^k}{k!}, \quad k \in \{0, 1, 2, \dots\}$$
    Riconoscendo lo sviluppo in serie di Taylor dell'esponenziale $\sum_{k=0}^{\infty} \frac{c^k}{k!} = e^c$, si impone:
    $$\sum_{k=0}^{\infty} P(X = k) = 1 \implies A \sum_{k=0}^{\infty} \frac{c^k}{k!} = A e^c = 1 \implies A = e^{-c}$$
    e si deduce che $X \sim \mathcal{P}(c)$ con media $c$.
* **Frasi sentinella nel testo**: *"In media arrivano $\lambda$ eventi al minuto..."*, *"Processo di arrivo di pacchetti..."*, *"Formula con $k!$ a denominatore e potenze a numeratore"*.

---

#### 5. Distribuzione Uniforme Discreta: $\mathcal{U}(\{x_1, \dots, x_M\})$
* **Meccanismo fisico**: Discende dal *principio di ragione insufficiente* di Laplace: quando uno spazio finito di $M$ elementi non presenta alcun motivo per favorire un esito rispetto agli altri, tutti gli esiti sono equiprobabili.
* **PMF e Momenti**:
  $$p_X(x_i) = \frac{1}{M}, \quad \forall i \in \{1, \dots, M\}$$
  Per valori interi consecutivi $\{0, 1, \dots, M-1\}$:
  $$\mathbb{E}[X] = \frac{M-1}{2}, \qquad \operatorname{Var}(X) = \frac{M^2 - 1}{12}$$
* **Quando si usa all'esame?**
  * Lancio di dadi equi a $M$ facce o estrazione di numeri/carte.
  * Scelta pseudo-casuale uniforme di uno slot trasmissivo tra $M$ disponibili (TDMA).
  * Funzione di hash ideale che distribuisce le chiavi in modo uniforme tra $M$ bucket.
* **Frasi sentinella nel testo**: *"Perfettamente equiprobabili"*, *"Un dado non truccato"*, *"Scelta puramente casuale tra $M$ alternative"*.

---

#### 6. Il Caso Speciale dell'Esame Mattera: Tabelle Congiunte senza Nome
> [!IMPORTANT]
> **Attenzione alla struttura dell'Esercizio 1 d'esame**:
> Nella quasi totalità delle prove scritte (stile Mattera), l'Esercizio 1 presenta variabili discrete $X$ e $Y$ con alfabeti cortissimi (es. $X \in \{0, 1\}$ e $Y \in \{0, 2\}$ oppure $X \in \{0, 2\}$ e $Y \in \{1, 3\}$).
> * **Queste variabili NON appartengono a una famiglia notevole (non sono né Binomiali né di Poisson)**.
> * Si gestiscono compilando la **matrice congiunta $p_{X,Y}(x,y)$**:
>   * Marginali: somme per righe e per colonne.
>   * Somma $T = X+Y$: raggruppamento delle coppie $(x,y)$ che danno lo stesso valore $t$.
>   * Indipendenza: verifica se per ogni cella vale $p_{X,Y}(x,y) = p_X(x)p_Y(y)$.

---

#### Tabella Sinottica Comparativa per il Riconoscimento Rapido

| Distribuzione | Cosa conta la variabile $X$? | Parametri | Alfabeto $\mathcal{X}$ | PMF $p_X(k)$ | Condizione discriminante |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Bernoulli** | Singola prova (0 o 1) | $p$ | $\{0, 1\}$ | $p^k (1-p)^{1-k}$ | Una sola esecuzione dicotomica |
| **Binomiale** | Numero di successi su $n$ prove | $n, p$ | $\{0, 1, \dots, n\}$ | $\binom{n}{k} p^k (1-p)^{n-k}$ | $n$ prove indipendenti fissate a priori |
| **Geometrica** | Tentativi necessari fino al 1° successo | $p$ | $\{1, 2, 3, \dots\}$ | $(1-p)^{k-1} p$ | Numero di prove aleatorio (memoryless) |
| **Poisson** | Eventi in tempo/spazio continuo | $\lambda$ | $\{0, 1, 2, \dots\}$ | $\frac{\lambda^k}{k!} e^{-\lambda}$ | Tasso medio $\lambda$, supporto illimitato $\mathbb{N}_0$ |
| **Uniforme** | Scelta equiprobabile tra $M$ opzioni | $M$ | $\{x_1, \dots, x_M\}$ | $\frac{1}{M}$ | Tutte le probabilità sono identiche |

---

### 2.3 PMF Condizionale e Funzioni di Variabili Discretembda}$ | $\mathbb{E}[X] = \operatorname{Var}(X) = \lambda$ |
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

### 4.5 Distribuzioni Notevoli Continue: Guida Completa alla Scelta

Per individuare quale distribuzione continua governa il fenomeno esaminato, poniti questa domanda: **«Qual è la natura fisica della grandezza misurata?»**

```text
                     ALBERO DI DECISIONE: VARIABILI CONTINUE
                                       │
         ┌─────────────────────────────┼─────────────────────────────┐
         ▼                             ▼                             ▼
Attesa continua / durata      Equiprobabilità su un         Somma di disturbi /
 prima del primo evento         intervallo limitato          rumore fisico (TLC)
         │                             │                             │
    ESPONENZIALE                   UNIFORME                      GAUSSIANA
$[0, \infty)$, memoryless            $[a, b]$             $\mathbb{R}, \mathcal{N}(\mu, \sigma^2)$
                                                                     │
                                                        ┌────────────┴────────────┐
                                                        ▼                         ▼
                                                 Ampiezza inviluppo         Code pesanti /
                                                 due gaussiane ortogonali   rumore a impulsi
                                                        │                         │
                                                     RAYLEIGH                 LAPLACIANA
                                               $Ax e^{-x^2}u(x)$             $\frac{\lambda}{2}e^{-\lambda|x|}$
```

---

#### 1. Distribuzione Uniforme Continua: $X \sim \mathcal{U}(a, b)$ con $a < b$
* **Meccanismo fisico**: La variabile può cadere in qualsiasi punto dell'intervallo $[a, b]$ senza alcuna preferenza o polarizzazione.
* **Supporto:** $[a, b]$
* **PDF e CDF:**
  $$f_X(x) = \begin{cases} \frac{1}{b - a} & a \le x \le b \\ 0 & \text{altrove} \end{cases} = \frac{1}{b - a} [u(x - a) - u(x - b)]$$
  $$F_X(x) = \begin{cases} 0 & x < a \\ \frac{x - a}{b - a} & a \le x \le b \\ 1 & x > b \end{cases}$$
* **Momenti:** $\mathbb{E}[X] = \frac{a + b}{2}, \quad \operatorname{Var}(X) = \frac{(b - a)^2}{12}$
* **Quando si usa all'esame?**
  * Errore di quantizzazione / arrotondamento (round-off): $X \sim \mathcal{U}[-\frac{\Delta}{2}, \frac{\Delta}{2}]$.
  * Fase casuale di un'oscillazione sinusoidale / portante: $\Theta \sim \mathcal{U}[-\pi, \pi]$ o $\mathcal{U}[0, 2\pi]$.
  * Ritardo di propagazione casuale compreso tra due estremi noti.
* **Frasi sentinella nel testo**: *"Uniformemente distribuita nell'intervallo..."*, *"Priva di polarizzazione tra $a$ e $b$"*.

---

#### 2. Distribuzione Esponenziale: $X \sim \mathcal{E}(\lambda)$ con $\lambda > 0$
* **Meccanismo fisico**: Modella il **tempo continuo di attesa** fino al verificarsi del primo evento (o la durata di vita di un componente che non soffre di usura). È il corrispondente continuo della Geometrica.
* **Supporto:** $[0, +\infty)$
* **Cosa indica $\lambda$ (Lambda)?**
  * $\lambda$ è il **tasso medio di accadimento** per unità di tempo.
  * Legame con la media: $\mathbb{E}[X] = \frac{1}{\lambda}$. Più alto è $\lambda$, più frequenti sono gli eventi e più breve è il tempo medio di attesa.
  * Tasso di guasto costante (*Hazard rate*): $h(t) = \frac{f(t)}{1-F(t)} = \lambda$ (nessun invecchiamento fisico).
* **PDF e CDF:**
  $$f_X(x) = \lambda e^{-\lambda x} u(x)$$
  $$F_X(x) = (1 - e^{-\lambda x}) u(x)$$
* **Coda (CCDF / Affidabilità):** $\mathbb{P}(X > x) = e^{-\lambda x}$ (per $x \ge 0$)
* **Momenti:** $\mathbb{E}[X] = \frac{1}{\lambda}, \quad \operatorname{Var}(X) = \frac{1}{\lambda^2}$
* **Proprietà Cardine - Assenza di Memoria (*Memoryless* continua):**
  $$\mathbb{P}(X > s + t \mid X > s) = \mathbb{P}(X > t) \quad \forall s, t \ge 0$$
* **Quando si usa all'esame?**
  * Tempo di interarrivo tra pacchetti consecutivi in reti a coda $M/M/1$.
  * Durata fino al guasto per shock ambientali casuali.
  * Tempo di servizio / elaborazione di una richiesta in un server.
* **Frasi sentinella nel testo**: *"Tempo di attesa fino al prossimo arrivo..."*, *"Tempo di vita con tasso di guasto costante $\lambda$..."*.

---

#### 3. Distribuzione Gaussiana (Normale): $X \sim \mathcal{N}(\mu, \sigma^2)$
* **Meccanismo fisico**: È la distribuzione regina della statistica applicata e delle telecomunicazioni. Per il **Teorema del Limite Centrale (TLC)**, la somma di un numero elevato di contributi casuali indipendenti tende asintoticamente a una variabile Gaussiana, a prescindere dalla distribuzione dei singoli addendi.
* **Supporto:** $\mathbb{R} = (-\infty, +\infty)$
* **PDF:**
  $$f_X(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$$
* **Momenti:** $\mathbb{E}[X] = \mu, \quad \operatorname{Var}(X) = \sigma^2$
* **Come si risolve all'esame? (Standardizzazione e Funzione $Q(x)$)**:
  Non si calcola mai l'integrale a mano! Si passa alla variabile normale standard $Z = \frac{X - \mu}{\sigma} \sim \mathcal{N}(0, 1)$:
  $$\mathbb{P}(X > x) = Q\left(\frac{x - \mu}{\sigma}\right), \qquad \mathbb{P}(X \le x) = 1 - Q\left(\frac{x - \mu}{\sigma}\right) = \Phi\left(\frac{x - \mu}{\sigma}\right)$$
  dove $Q(x) = \frac{1}{\sqrt{2\pi}} \int_x^{+\infty} e^{-t^2/2} dt$.
* **Proprietà e valori notevoli di $Q(x)$ da ricordare a memoria**:
  * Simmetria: $Q(-x) = 1 - Q(x)$.
  * $Q(0) = 0.5$ (la metà dell'area è a destra dello zero).
  * $Q(1) \approx 0.1587 \quad (\approx 16\%)$
  * $Q(2) \approx 0.0228 \quad (\approx 2.3\%)$
  * $Q(3) \approx 0.00135 \quad (\approx 0.13\%)$
* **Quando si usa all'esame?**
  * Rumore termico additivo bianco gaussiano (AWGN) nei canali di telecomunicazione.
  * Errore di misura complessivo risultante da molteplici disturbi fisici indipendenti.
  * Approssimazione normale per Binomiali con $n$ grande ($np > 5$).
* **Frasi sentinella nel testo**: *"Rumore gaussiano con potenza $\sigma^2$..."*, *"Segnale disturbato da rumore termico AWGN..."*, *"Distribuzione normale con media $\mu$ e varianza $\sigma^2$..."*.

---

#### 4. Il Modello di Rayleigh / Decadimento Quadratico (Il "Classico" Mattera)
* **Forma analitica ricorrente d'esame**:
  $$f_X(x) = A x e^{-x^2} u(x)$$
* **Origine fisica**: Rappresenta l'ampiezza dell'inviluppo di un segnale in presenza di due componenti gaussiane ortogonali indipendenti a media nulla $R = \sqrt{X_1^2 + X_2^2}$ (canale radio con fading di Rayleigh / multipath).
* **I passaggi operativi obbligatori all'esame**:
  1. **Determinazione immediata di $A$**:
     $$\int_0^{+\infty} x e^{-x^2} dx = \left[ -\frac{1}{2} e^{-x^2} \right]_0^{+\infty} = \frac{1}{2} \implies A \cdot \frac{1}{2} = 1 \implies \mathbf{A = 2}$$
  2. **Trasformazioni tipiche ($Y = \sqrt{X}$ oppure $Y = \ln X$)**:
     * $Y = \sqrt{X} \implies x = y^2, \, \left|\frac{dx}{dy}\right| = 2y \implies f_Y(y) = 2(y^2)e^{-y^4} \cdot 2y = 4y^3 e^{-y^4} u(y)$.
     * $Y = \ln X \implies x = e^y, \, \left|\frac{dx}{dy}\right| = e^y \implies f_Y(y) = 2e^{2y} e^{-e^{2y}}$.
  3. **Calcolo di Moda e Mediana**:
     * **Moda ($m_o$)**: si annulla la derivata prima: $\frac{d}{dy} f_Y(y) = 0$.
     * **Mediana ($m_e$)**: si impone l'area a sinistra pari a $1/2$: $F_Y(m_e) = \frac{1}{2}$.
* **Frasi sentinella nel testo**: *"Sia $X$ con densità $f(x) = A x \exp(-x^2) u(x)$..."*, *"Si valuti il parametro di normalizzazione $A$..."*.

---

#### 5. Distribuzione Laplaciana (Doppia Esponenziale): $X \sim \mathcal{L}(\lambda)$ con $\lambda > 0$
* **Meccanismo fisico**: Due ali esponenziali simmetriche incollate attorno a zero ($e^{-\lambda |x|}$).
* **Supporto:** $\mathbb{R} = (-\infty, +\infty)$
* **PDF e CDF:**
  $$f_X(x) = \frac{\lambda}{2} e^{-\lambda |x|}$$
  $$F_X(x) = \begin{cases} \frac{1}{2} e^{\lambda x} & x \le 0 \\ 1 - \frac{1}{2} e^{-\lambda x} & x > 0 \end{cases}$$
* **Momenti:** $\mathbb{E}[X] = 0, \quad \operatorname{Var}(X) = \frac{2}{\lambda^2}$
* **Quando si usa all'esame?** Rumore a impulsi (*impulsive noise*), coefficienti di trasformata (DCT/wavelet nei codec JPEG/MP3), errori di stima simmetrici a code più pesanti della Gaussiana.

---

#### 6. Distribuzione di Cauchy: $X \sim \mathcal{C}(a, b)$ con $a \in \mathbb{R}$ e $b > 0$
* **Supporto:** $\mathbb{R} = (-\infty, +\infty)$
* **PDF e CDF:**
  $$f_X(x) = \frac{1}{b\pi} \frac{1}{1 + \left(\frac{x - a}{b}\right)^2}, \qquad F_X(x) = \frac{1}{2} + \frac{1}{\pi} \arctan\left(\frac{x - a}{b}\right)$$
* **Media:** **NON DEFINITA** (le code decadono come $1/x^2$, l'integrale del primo momento non converge assolutamente).
* **Quando si usa all'esame?** Rapporto tra due variabili gaussiane standard $Z = X/Y$ con $X, Y \sim \mathcal{N}(0, 1)$, problema geometrico del fascio rotante (faro che spazza una parete).

---

#### Tabella Sinottica Comparativa delle Variabili Continue

| Distribuzione | Supporto | PDF $f_X(x)$ | $\mathbb{E}[X]$ | $\operatorname{Var}(X)$ | Quando riconoscerla |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Uniforme** | $[a, b]$ | $\frac{1}{b-a}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ | Ignoranza a priori o quantizzazione |
| **Esponenziale** | $[0, +\infty)$ | $\lambda e^{-\lambda x} u(x)$ | $\frac{1}{\lambda}$ | $\frac{1}{\lambda^2}$ | Attese continue tra arrivi, memoryless |
| **Gaussiana** | $(-\infty, +\infty)$ | $\frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | $\mu$ | $\sigma^2$ | Rumore termico AWGN, somma di effetti (TLC) |
| **Rayleigh (Mattera)** | $[0, +\infty)$ | $2x e^{-x^2} u(x)$ | $\frac{\sqrt{\pi}}{2}$ | $\frac{4-\pi}{4}$ | Esercizio 2 esame scritto ($A=2$), inviluppo |
| **Laplaciana** | $(-\infty, +\infty)$ | $\frac{\lambda}{2} e^{-\lambda |x|}$ | $0$ | $\frac{2}{\lambda^2}$ | Rumore impulsivo a campana appuntita |
| **Cauchy** | $(-\infty, +\infty)$ | $\frac{1}{\pi(1+x^2)}$ | Non def. | Non def. | Rapporto di due gaussiane $X/Y$ |

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
