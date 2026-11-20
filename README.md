# ArteAI · Un'intelligenza artificiale davanti a un quadro

*Progetto per il corso  · [Giulia Toniazzo Mat.76827A]*

Che cosa vede un'intelligenza artificiale davanti a un quadro? E quanto cambia la sua lettura se le diamo un titolo, un autore o un contesto, veri o falsi?

---

## Il progetto in breve

- **23 opere d'arte**, dall'Ottocento all'arte contemporanea, da molto famose a poco note.
- **Gemma 4** (Google), un modello che legge testo e immagini, ha descritto ogni opera in **9 modi diversi**: con la sola immagine, con titolo, autore e contesto veri, oppure con un'informazione **falsa** preparata apposta (un titolo, un autore, un contesto o un dettaglio che nel quadro non c'è).
- Le risposte erano **a sezioni** (che cosa vedi, che cosa significa, che cosa sai, che opera è) oppure in **testo libero**.
- In tutto **207 risposte**, valutate da un secondo modello (**Qwen 3.5**) usato come giudice e, **71** di esse, anche a mano.

L'immagine resta sempre la stessa: se la risposta cambia, è merito (o colpa) delle parole.

---

## Domande di ricerca e risultati

| | Domanda | Che cosa abbiamo trovato |
|---|---|---|
| **RQ1** | Che cosa comunica un'opera a chi la guarda senza saperne nulla? | Gemma descrive soprattutto **dove stanno le cose** (29% delle frasi, contro l'11% del museo). Riconosce **6 opere iconiche su 7**, ma solo **2 poco note su 8**, e a volte inventa un autore. |
| **RQ2** | Come cambia la lettura con titolo, autore e contesto, veri o falsi? | Le **emozioni seguono il titolo**: con un titolo falso cupo la vitalità scende dal 39% al 17%. Un **oggetto inventato** viene smentito 20 volte su 23; un **titolo falso** viene creduto 10 volte su 23. Sulle opere poco note Gemma si lascia ingannare molto di più (41% contro 14%). |
| **RQ3** | Sa distinguere ciò che vede da ciò che interpreta? | **Solo se glielo chiediamo.** Nel testo libero mescola descrizione e interpretazione e sbaglia di più: 70% di descrizioni corrette, contro 91% con le sezioni. |
| **RQ4** | Le sue conoscenze sono corrette o le inventa? | Quasi sempre corrette: **88%** delle descrizioni senza errori, **90%** delle risposte senza invenzioni. Gli errori nascono nel testo libero e quando un titolo suggerisce che cosa vedere. |
| **RQ5** | Quando è un supporto affidabile all'analisi artistica, e che limiti ha rispetto alla critica umana? | È affidabile per descrivere che cosa c'è e per capire se si è lasciata ingannare (IA e persona d'accordo **43 volte su 47**). Non vede però i **dettagli fini** (posa, gesti, piccoli oggetti) e le **interpretazioni forzate**, che una persona nota. |

> **In una frase:** l'IA vede l'immagine, ma la legge attraverso le parole che la accompagnano. Più l'opera è sconosciuta, più contano le parole.

---

## Che cosa c'è nella repository

| File o cartella | Contenuto |
|---|---|
| `ArteAI_progetto.ipynb` | **Il notebook**: come è stato fatto il lavoro, poi l'analisi domanda per domanda, con grafici ed esempi di risposte |
| `ArteAI_Annotazioni_valutazione_umana.xlsx` | la valutazione a mano delle 71 risposte |
| `data/artworks.json` | le 23 opere: dati del museo, elementi visibili, testo del museo, informazioni vere e false |
| `runs/responses.jsonl` | le 207 risposte di Gemma |
| `runs/giudice_v2.jsonl` | i giudizi di Qwen |
| `annotations/_KEY_risposte.csv` | collega i codici anonimi della valutazione (R0001…) alle risposte |
| `images/` | le immagini delle opere |
| `figures/` | i grafici prodotti dal notebook |

---

## Come aprire il notebook

1. Copiare la cartella in Google Drive come **`MyDrive/ArteAI`**.
2. Aprire **`ArteAI_progetto.ipynb`** in Google Colab.
3. **Runtime → Esegui tutto.** Non serve la GPU e bastano pochi minuti.

Non serve saper programmare: ogni cella è preceduta da un testo che spiega che cosa fa e perché.

Le celle che usano i modelli sono spente (`GENERA = False`, `GIUDICA = False`), quindi il notebook legge le risposte già salvate. Per rigenerarle servono una GPU A100 e una chiave Hugging Face (`HF_TOKEN`) nei secreti di Colab.

---

## Limiti

- 23 opere e una sola risposta per condizione: i risultati sono indicativi.
- Valutazione a mano su 71 risposte su 207.
- Alcune misure (categorie descrittive, emozioni) sono contate con elenchi di parole.

---

## Note

- Le immagini vengono dalle collezioni dei musei (soprattutto Art Institute of Chicago). Alcune opere sono protette da diritto d'autore e sono usate solo a scopo di studio.
- Modelli usati: `google/gemma-4-31B-it` e `Qwen/Qwen3.5-27B`, a pesi aperti, da Hugging Face.
- Codice scritto con il supporto di un assistente AI.
