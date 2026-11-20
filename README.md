# ArteAI · Un'intelligenza artificiale davanti a un quadro

*Progetto ad opera di Giulia Toniazzo Mat.76827A* · 


Che cosa vede un'intelligenza artificiale davanti a un quadro? E quanto cambia la sua lettura se le diamo un titolo, un autore o un contesto, veri o falsi?

---

## Il progetto in breve

- **23 opere d'arte**, dall'Ottocento all'arte contemporanea, da molto famose a poco note.
- **Gemma 4** (Google), un modello che legge testo e immagini, ha descritto ogni opera in **9 modi diversi**: con la sola immagine, con titolo, autore e contesto veri, oppure con un'informazione **falsa** preparata apposta (un titolo, un autore, un contesto o un dettaglio che nel quadro non c'è).
- Le risposte erano **a sezioni** (che cosa vedi, che cosa significa, che cosa sai, che opera è) oppure in **testo libero**.
- In tutto **207 risposte**, valutate da un secondo modello (**Qwen 3.5**) usato come giudice e, **71** di esse, anche a mano.

L'immagine resta sempre la stessa: se la risposta cambia, è merito (o colpa) delle parole.

---

## Domande di ricerca

1. **RQ1** · Che cosa comunica un'opera a chi la guarda senza saperne nulla?
2. **RQ2** · Come cambia la lettura con titolo, autore e contesto, veri o falsi?
3. **RQ3** · Il modello sa distinguere ciò che vede da ciò che interpreta?
4. **RQ4** · Le sue conoscenze sono corrette o le inventa?
5. **RQ5** · In quali casi un modello multimodale è un supporto affidabile all'analisi artistica, e quali sono i suoi limiti rispetto alla critica umana?

Risultati, grafici ed esempi sono nel notebook.

---

## Che cosa c'è nella repository

| File o cartella | Contenuto |
|---|---|
| `ArteAI_progetto.ipynb` | **Il notebook**: come è stato fatto il lavoro, poi l'analisi domanda per domanda, con grafici ed esempi di risposte |
| `ArteAI_Annotazioni_valutazione_umana.xlsx` | la valutazione a mano delle 71 risposte |
| `catalogo_opere.xlsx` | catalogo delle opere d'arte con tutte le informazioni |
| `data/artworks.json` | le 23 opere: dati del museo, elementi visibili, testo del museo, informazioni vere e false |
| `runs/responses.jsonl` | le 207 risposte di Gemma |
| `runs/giudice_v2.jsonl` | i giudizi di Qwen |
| `annotations/_KEY_risposte.csv` | collega i codici anonimi della valutazione (R0001…) alle risposte |
| `images/` | le immagini delle opere |
| `figures/` | i grafici prodotti dal notebook |

---

## Come aprire il notebook

1. Copiare la cartella in Google Drive come **`MyDrive/ArteAI`**.
2. Aprire **`ArteAI_Giulia-Toniazzo_Matricola_76827A.ipynb`** in Google Colab.
3. **Runtime → Esegui tutto.** Non serve la GPU e bastano pochi minuti.


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
