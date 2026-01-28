# Sum of Squares ($A^2 + B^2$) - Digital Logic Design

Questo progetto consiste nella progettazione, simulazione e analisi di un circuito digitale sequenziale in grado di calcolare la somma dei quadrati di due numeri interi a 4 bit ($A^2 + B^2$).

Il sistema è stato sviluppato interamente in **TkGate 2.1** adottando una metodologia **Bottom-Up**: dalla realizzazione delle singole porte logiche a transistor (CMOS) fino all'assemblaggio di macro aritmetiche complesse.

## 🎯 Obiettivi del Progetto

L'obiettivo principale è stato l'ottimizzazione dell'Area (complessità circuitale). Per raggiungere questo scopo, il progetto implementa:
1.  **Resource Sharing:** Utilizzo di una singola unità di calcolo condivisa per elevare al quadrato entrambi gli operandi in due cicli di clock distinti.
2.  **Confronto Architetturale:** Sviluppo e analisi di due diverse architetture per dimostrare i vantaggi dell'hardware dedicato rispetto a quello generico.

## 🏗️ Architettura del Sistema

Il circuito è composto da un **Data Path** (gestione del flusso dati) e una **Control Unit** (sincronizzazione).

### Specifiche Tecniche
- **Input:** Due interi a 4 bit ($A, B \in [1]$).
- **Output:** Un intero a 9 bit ($Y \in $).
- **Logica di Controllo:** Macchina di Moore a 2 stati (FSM) che gestisce il multiplexing degli ingressi e l'accumulo dei risultati parziali.

### Le due varianti implementate

Il progetto mette a confronto due approcci per l'unità di calcolo principale:

*   **Architettura A (Generica):** Utilizza un **Moltiplicatore 4x4 standard** (`MUL4x4`). Calcola il quadrato eseguendo la moltiplicazione completa $A \times A$. Richiede una matrice completa di prodotti parziali (16 porte AND + 4 Half Adder + 8 Full Adder).
*   **Architettura B (Ottimizzata):** Utilizza un **Quadratore specifico** (`SQ4bit`). Sfruttando le proprietà algebriche del quadrato (commutatività e idempotenza), rimuove le ridondanze logiche. La matrice di calcolo è ridotta a soli 6 AND, 3 Half Adder e 3 Full Adder.

## 🛠️ Tecnologie Utilizzate

*   **Simulatore:** TkGate 2.1
*   **Design Level:** Gate Level & Register Transfer Level
*   **Componenti:** Custom library (CMOS gates, Flip-Flops, MUX, Adders).

## 🚀 Come eseguire la simulazione

1.  Clona questo repository.
2.  Apri i file `.v` con TkGate.
3.  Carica il modulo `Main`.
4.  Attiva il clock e il segnale `enable`.
5.  Imposta gli input sui Dip Switch, con lo Switch `clock` simula il trascorrere di 2 cicli e osserva il calcolo sulla Led Bar di output.

---
*Progetto realizzato per il corso di Reti Logiche - Università degli Studi di Urbino Carlo Bo.*
