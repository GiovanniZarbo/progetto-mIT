# Contribuire

## Verificare il dizionario

Per scoprire parole mancanti o errate, usa uno di questi due metodi nel browser:

**A) mini-Hunspell** — singolo file HTML con JS inline, zero dipendenze, ~85–90% di accuratezza.

**B) [nspell](https://github.com/wooorm/nspell)** (MIT) con i nostri `.aff`/`.dic` — più accurato, ~95%, richiede un build step.

Entrambi caricano `it_IT.aff` e `it_IT.dic` da questo repo (non dizionari di terzi).

## Segnalare parole

Apri una [issue](../../issues) con:

- **parole mancanti** (valide ma rifiutate): lista una voce per riga, con il lemma base se possibile (es. `gattopardo` invece di `gattopardi`)
- **parole errate** (sbagliate ma accettate): indica la parola, perché è sbagliata e — se lo sai — quale regola del `.aff` la sta generando

Non serve verificare tutte le forme flesse: basta il lemma e il flag corretto (vedi la [tabella dei flag](./README.md#convenzione-dei-flag)).

Per proporre direttamente le parole nuove, modifica [`aggiunte.dic`](./aggiunte.dic) (non `it_IT.dic`) e apri una PR.
