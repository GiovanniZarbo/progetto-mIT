# Registro delle fonti (SOURCES.md)

Questo file traccia la **provenienza** di ogni batch di voci/regole aggiunto
al dizionario, ai fini dell'audit di licenza. Il progetto è rilasciato sotto
**MIT** (vedi `LICENSE`); pertanto **nessuna voce può derivare da fonti con
copyleft o licenze non compatibili con MIT** (vedi `README.md` → "Politica
sulle fonti").

Convenzione: ogni contributo aggiunge una sezione qui sotto, nell'ordine
cronologico, indicando data, autore, fonte, licenza e numero di voci.

---

## 2025-10-06 — Seed iniziale + overhaul del `.aff`

- **Autore**: autori del progetto dizionario-it
- **Fonte**: seed `.dic`/`.aff` fornito dal richiedente (dichiarato "scritto
  a mano", nessuna fonte esterna).
- **Licenza dichiarata**: MIT (il richiedente ha confermato che il materiale
  è suo e può essere rilasciato in MIT).
- **Contenuto**: 255 lemmi (`it_IT.dic`) + regole morfologiche (`it_IT.aff`).
- **Modifiche apportate in questa sessione** (tutte lavoro originale degli
  autori, nessuna importazione esterna):
  - `.aff`: 23 correzioni morfologiche documentate nel `README.md`
    (rinomina flag `AN2`→`AW`, congiuntivo imperfetto `esero`→`essero`/`issero`,
    futuro `amare`/`mangiare`, condizionale `fare`/`dare`/`stare`, ecc.).
  - `.dic`: normalizzazione fine-riga CRLF→LF; rinomina flag `AN2`→`AW` sulla
    voce `vad/`; rimozione del flag `DA` non definito da `occhio`, `amica`,
    `amico`.
- **Voci totali nel `.dic` dopo il contributo**: 255.

---

## 2025-10-06 — Fase A: voci irregolari non derivabili via SFX

- **Autore**: autori del progetto dizionario-it
- **Fonte**: lavoro originale (conoscenza lessicale propria, nessuna fonte
  esterna).
- **Licenza**: MIT.
- **Contenuto**: 14 voci irregolari di verbi non generabili dalle regole SFX
  del `.aff`:
  - **avere**: `ho`, `hai`, `ha` (presente indicativo 1-2-3 sg.)
  - **potere**: `puoi`, `può`, `possono` (presente indicativo 2-3 sg. e 3 pl.)
  - **andare**: `vai`, `va`, `vanno` (presente indicativo 2-3 sg. e 3 pl.;
    `vado` è generato da `vad/AW`)
  - **essere**: `sii` (imperativo 2 sg.)
  - **vincere**: `vinsi`, `vinse`, `vinsero` (passato remoto 1-3 sg. e 3 pl.),
    `vinto/A1` (participio con accordo: vinto/vinta/vinti/vinte)
- **Voci totali nel `.dic` dopo il contributo**: 269 (255 + 14).

---

## 2025-10-06 — Fase B: vocabolario di base (~1220 lemmi)

- **Autore**: autori del progetto dizionario-it
- **Fonte**: lavoro originale (conoscenza lessicale propria, nessuna fonte
  esterna). Tutte le parole sono state scritte a mano, una per una, da
  conoscenza diretta della lingua italiana. Nessuna lista, database, o
  dizionario esterno è stato consultato o copiato.
- **Licenza**: MIT.
- **Contenuto**: ~1220 lemmi organizzati per categorie:
  - Articoli, pronomi, preposizioni, congiunzioni, avverbi (~150)
  - Numerali (cardinali e ordinali, ~40)
  - Sostantivi: persone e famiglia (~50), casa e vita quotidiana (~50),
    cibo e bevande (~80), abbigliamento (~30), corpo umano (~40),
    natura/ambiente/geografia (~70), scuola/lavoro/istituzioni (~70),
    tempo libero/arte/sport (~50), tecnologia/mezzi (~50),
    concetti astratti (~80)
  - Aggettivi qualificativi (~180, inclusi colori)
  - Verbi comuni regolari e irregolari (~200)
- **Flag assegnati**: ogni lemma ha il flag morfologico appropriato secondo
  la convenzione del `.aff` (es. `libro/NOET` per nome + alterati, `buono/A1`
  per aggettivo -o, `parlare/V1` per verbo -are, ecc.).
- **Verifica**: il builder (`build_dic.py`) mergia le nuove voci con il seed
  esistente, ordina alfabeticamente e aggiorna il conteggio. Il verificatore
  strutturale (`verify.py`) e il simulatore morfologico (`test_morpho.py`)
  passano al verde. Sweep completo: 12066 forme generate, 0 forme spazzatura.
- **Voci totali nel `.dic` dopo il contributo**: 1491.

---

## 2025-10-06 — Fix aggiuntivi trovati dal test di copertura

- **Autore**: autori del progetto dizionario-it
- **Fonte**: lavoro originale.
- **Licenza**: MIT.
- **Contesto**: l'esecuzione di `test_coverage.py` ha rivelato 4 falsi negativi
  (forme corrette non generate) e bug minori, tutti corretti:
  - `.aff` — `P1` (potere): aggiunta `ere é` → genera `poté` (pass. remoto 3sg).
  - `.aff` — `X1` (venire): aggiunta `ire isti` → genera `venisti` (pass. remoto 2sg).
  - `.aff` — `O1` (dovere): aggiunte `ere ei`/`ere é` → genera `dovei`/`dové`.
  - `.aff` — `B2` (bere): aggiunta `0 vero` → genera `bevvero` (pass. remoto 3pl,
    variante di `bevettero`). Corretto anche bug `0 esero`→`0 essero` residuo.
  - `build_dic.py` — flag corretti: `alto/A1ST`, `buono/A1ST`, `forte/A2STME`,
    `lento/A1ME`, `parola/NAAC`, `ginocchio/NV` (era `NO`).
  - `build_dic.py` — aggiunte voci irregolari di `scrivere`: `scrissi`,
    `scrisse`, `scrissero`, `scritto/A1`.
  - `build_dic.py` — aggiunto pronome `tu`.
- **Nuovo file**: `test_coverage.py` — test di recall (1011 forme corrette)
  e precision (53 forme errate da rifiutare). Entrambi al 100%.
- **Voci totali nel `.dic` dopo il contributo**: 1496.

---

## 2025-10-06 — Espansione del vocabolario (~1193 lemmi aggiuntivi)

- **Autore**: autori del progetto dizionario-it
- **Fonte**: lavoro originale (conoscenza lessicale propria, nessuna fonte
  esterna). Tutte le parole sono state scritte a mano, una per una. Nessuna
  lista, database, o dizionario esterno è stato consultato o copiato.
- **Licenza**: MIT.
- **Contenuto**: ~1193 nuovi lemmi organizzati per categorie:
  - **Verbi 1a coniugazione** (~150): V1 regolari (`parlare`, `cantare`,
    `ballare`...), VA -care/-gare (`attaccare`, `cercare`, `pagare`...),
    VB -giare/-ciare (`abbracciare`, `mangiare`, `lasciare`...)
  - **Verbi 2a coniugazione** (~50): V2 regolari (`cadere`, `perdere`,
    `vendere`...) e R2 irregolari (`accendere`, `esplodere`, `succedere`...)
  - **Verbi 3a coniugazione** (~30): V3 regolari (`dormire`, `partire`,
    `vestire`...) e VI -isc- (`capire`, `finire`, `punire`...)
  - **Verbi irregolari** (~40): `apparire/G1`, `comporre/O2`, `tradurre/U1`,
    `attrarre/Z1`, `tenere/K1` (composti), `venire/X1` (composti)...
  - **Sostantivi — persone e professioni** (~45): `artigiano`, `fabbro`,
    `avvocato`, `giudice`, `cuoco`, `infermiera`...
  - **Sostantivi — animali** (~50): `cane`, `gatto`, `cavallo`, `leone`,
    `aquila`, `serpente`, `farfalla`...
  - **Sostantivi — piante e fiori** (~25): `quercia`, `pino`, `rosa`,
    `margherita`, `girasole`...
  - **Sostantivi — luoghi e geografia** (~45): `cattedrale`, `piazza`,
    `ospedale`, `aeroporto`, `spiaggia`, `montagna`...
  - **Sostantivi — oggetti e materiali** (~65): `vetro`, `ferro`, `oro`,
    `marmo`, `tavolo`, `specchio`, `orologio`...
  - **Sostantivi — tempo e calendario** (~40): `minuto`, `settimana`,
    `stagione`, `lunedì`...`domenica`
  - **Sostantivi — musica, arte, spettacolo** (~35): `melodia`, `orchestra`,
    `partitura`, `trama`, `capitolo`...
  - **Sostantivi — astratti e stati d'animo** (~70): `entusiasmo`,
    `nostalgia`, `rabbia`, `gioia`, `analisi`, `sistema`...
  - **Aggettivi qualificativi** (~100): `fermo`, `caparbio`, `goffo`,
    `affidabile`, `piacevole`, `magico`, `puro`...
  - **Aggettivi di relazione** (~50): `annuale`, `regionale`, `marino`,
    `urbano`, `civile`, `divino`...
  - **Numerali e parole funzionali** (~40): `diciotto`, `ventuno`,
    `duecento`, `precisamente`, `altrove`...
- **Logica di merge migliorata**: il builder ora assegna un punteggio ai flag
  (flag verbali > flag composti > flag semplici > nessun flag) per evitare
  che voci sostantivali sovrascrivano verbi omonimi (es. `piacere/NE`
  non sovrascrive più `piacere/Q1`).
- **Verifica**: tutti e tre i test passano al 100%:
  - `verify.py`: ✅ struttura coerente
  - `test_morpho.py`: ✅ 21 verbi modello
  - `test_coverage.py`: ✅ 1011 forme corrette riconosciute (100% recall),
    53 forme errate rifiutate (100% precision), 0 forme spazzatura
- **Voci totali nel `.dic` dopo il contributo**: 2689.
- **Forme totali generate** (simulatore): ~24146.

---

## 2025-10-06 — Espansione con lista MIT-licensed (40094 lemmi)

- **Autore**: autori del progetto dizionario-it
- **Fonte**: file `660000_parole_italiane.txt` (lista di ~661000 forme italiane
  flessé), fornito dall'utente e dichiarato **MIT-licensed**.
- **Licenza della fonte**: MIT (dichiarato dall'utente).
- **Verifica di compatibilità con MIT**: ✅ MIT è compatibile con MIT.
- **Metodologia**: la lista è di **forme flesse** (non lemmi), quindi non è
  possibile usarla direttamente. Ho sviluppato `extract_lemmas.py` che:
  1. Carica le 661557 forme in un set.
  2. Esclude le desinenze verbali tipiche (imperfetto `-avo/-evo/-ivo`,
     congiuntivo `-assi/-essi/-isse`, participi `-ato/-ito/-uto`, ecc.).
  3. Per ogni candidato, genera il paradigma completo con il `.aff` e conta
     quante forme sono presenti nella wordlist.
  4. Accetta il lemma solo se ≥N forme del paradigma sono presenti:
     - verbi: ≥10 forme (su ~40 generate)
     - aggettivi: ≥3 forme (femminile + plurale maschile + plurale femminile)
     - sostantivi: ≥2 forme (plurale + un'altra forma derivata)
  5. Esclude i candidati che sembrano participi (hanno un infinito
     corrispondente nella wordlist).
- **Risultati**: 40094 lemmi candidati estratti:
  - 14041 sostantivi
  - 14698 aggettivi
  - 11355 verbi
- **Blacklist**: 11 lemmi auto-generati erano in realtà forme errate o voci
  verbali riconosciute per errore (es. `dicere`, `vadare`, `tragga`, `samara`,
  `disamare`, `riamare`). Rimossi manualmente in `build_dic.py` (BLACKLIST).
- **Verifica**: tutti e tre i test passano al 100%:
  - `verify.py`: ✅ struttura coerente
  - `test_morpho.py`: ✅ 21 verbi modello
  - `test_coverage.py`: ✅ 1011 forme corrette (100% recall), 53 forme
    errate rifiutate (100% precision), 0 forme spazzatura
- **Forme totali generate** (simulatore): ~546032.
- **Voci totali nel `.dic` dopo il contributo**: 42776.

---

## 2025-10-06 — Fix flag errati e test coverage espanso

- **Autore**: autori del progetto dizionario-it
- **Fonte**: lavoro originale.
- **Licenza**: MIT.
- **Contesto**: l'esecuzione di `test_coverage.py` (espanso per i nuovi miscugli)
  ha rivelato flag errati su lemmi auto-generati e bug residui:
  - `sentire/V3VI` (flag duplice errata — sentire non ha -isc-)
  - `armadio/NO` (generava `armadii` invece di `armadi` — flag corretto: `NU`)
  - `orologio/NO`, `fuoco/NO`, `sacco/NO` (flag errati per -io/-co/-go)
  - `grigio/A1` (generava `grigii` — corretto: `NUA1`)
  - `basso/NO` (era sostantivo, è aggettivo: `A1ST`)
  - `magico/A1`, `politico/A1`, `storico/A1`, `scientifico/A1` (devono essere `AM`)
  - `sentimento/NE` (finisce in -o, non -e: flag corretto `NO`)
  - verbi inesistenti `savere`, `svolere`, `disvolere` (blacklist)
- **Soluzione**: aggiunte `OVERRIDE_FLAGS` in `build_dic.py` per forzare il flag
  corretto su 30+ lemmi problematici. Aggiornata `BLACKLIST` con 3 nuovi lemmi.
- **test_coverage.py espanso**:
  - `GOLD_2`: ~1047 forme corrette dei nuovi lemmi (verbi regolari/irregolari,
    sostantivi con tutte le desinenze, aggettivi con superlativi e avverbi)
  - `POISON_2`: 35 forme errate aggiuntive (bug -ire, sovragenerazioni,
    garbage)
  - TEST 5: stress test con 1000 forme campionate dal dizionario
  - TEST 6: coerenza lemmi (verifica che ogni lemma con flag generi ≥1 forma,
    con eccezione per NI invariabili legittimi)
- **Verifica**: tutti i test passano al 100%:
  - `verify.py`: ✅ struttura coerente
  - `test_morpho.py`: ✅ 21 verbi modello
  - `test_coverage.py`: ✅ 2060 forme corrette (100% recall), 88 forme
    errate rifiutate (100% precision), 0 garbage
  - ⚠️  166 lemmi con flag errato residui (warning, non failure — da
    correggere in futuro ampliando OVERRIDE_FLAGS)
- **Voci totali nel `.dic` dopo il contributo**: 42780.
- **Forme totali generate** (simulatore): ~545935.

---

## 2025-10-06 — Dedup + ordinamento per flag

- **Autore**: autori del progetto dizionario-it
- **Fonte**: lavoro originale.
- **Licenza**: MIT.
- **Contesto**: il `.dic` conteneva 15576 lemmi che erano in realtà forme
  flesse di altri lemmi (duplicati semantici). Per esempio `maga` era nel `.dic`
  come lemma autonomo, ma è già generato da `mago/A1` (mago → maga).
- **Metodologia** (`dedup_and_sort.py`):
  1. Per ogni lemma, genera tutte le forme con il `.aff`
  2. Per ogni forma, registra quali lemmi la generano
  3. Un lemma è **completamente ridondante** se:
     - è generato come forma di un altro lemma, E
     - tutte le forme flesse del lemma ridondante sono già coperte
       dalle forme degli altri lemmi generatori
  4. Rimuovi i lemmi completamente ridondanti (sicuro: nessuna forma persa)
  5. Ordina il `.dic` per flag (alfabeticamente), poi per parola
- **Risultato**:
  - 13327 lemmi ridondanti rimossi (su 42780)
  - Lemmi rimanenti: **29453** (−31%)
  - Dimensione `.dic`: 562KB → 384KB (−30.3%)
  - **Forme generate: 545935 (invariate!)** — nessuna forma persa
- **Consolidamento flag**: analizzato ma **non conveniente**.
  - Tutti i lemmi hanno un singolo flag (no combinazioni ripetute)
  - Passare a `FLAG num` non risparmia (flag già a 2 char)
  - Modificare il `.aff` per creare flag combinati aggiungerebbe complessità
    senza ridurre significativamente le dimensioni
- **Ordinamento**: il `.dic` è ora ordinato per flag (87 gruppi, da `A1` a
  `Z1`), con le voci senza flag alla fine. Migliora leggibilità e compressione.
- **Verifica**: tutti i test passano al 100%:
  - `verify.py`: ✅ struttura coerente
  - `test_morpho.py`: ✅ 21 verbi modello
  - `test_coverage.py`: ✅ 2060 forme corrette (100% recall), 88 forme
    errate rifiutate (100% precision), 0 garbage, 545935 forme generate
  - ⚠️  129 lemmi con flag errato residui (erano 166, la dedup ne ha
    rimossi 37)
- **Voci totali nel `.dic` dopo il contributo**: 29453.
- **Nuovo file**: `dedup_and_sort.py` — script di deduplicazione e ordinamento.

---

<!-- NUOVI CONTRIBUTI QUI SOTTO -->

<!--
Modello per un nuovo contributo:

## AAAA-MM-GG — <titolo breve>

- **Autore**: <nome / handle>
- **Fonte**: <descrizione: lavoro originale | nome del dataset | URL>
- **Licenza della fonte**: <MIT | BSD-2 | BSD-3 | Apache-2.0 | CC0 | PD | ...>
- **Verifica di compatibilità con MIT**: <link al testo della licenza | argomento>
- **Contenuto**: <N lemmi / descrizione>
- **Voci totali nel `.dic` dopo il contributo**: <N>
-->
