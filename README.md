# dizionario-it

Dizionario ortografico italiano per **Hunspell** (`it_IT.aff` / `it_IT.dic`),
rilasciato sotto licenza **MIT** (vedi `LICENSE`).

## Descrizione

Dizionario ortografico italiano con regole morfologiche complete: coniugazioni
verbali (regolari e irregolari), flessioni nominali e aggettivali, alterati,
prefissi con elisione, superlativi, avverbi in *-mente* e oltre 725.000 forme
generate da circa 39.000 lemmi.

## File

| File        | Descrizione                                                        |
|-------------|--------------------------------------------------------------------|
| `it_IT.aff` | Regole morfologiche (flessioni, coniugazioni, alterati, prefissi). |
| `it_IT.dic` | Lista lemmi con flag (~39.000 voci, ~725.000 forme generate).     |
| `LICENSE`   | Licenza MIT.                                                       |
| `SOURCES.md`| Registro delle fonti.                                              |

## Uso

```bash
hunspell -d it_IT parola_da_controllare
# oppure, in pipe:
echo "ciao monda" | hunspell -d it_IT
```

I due file devono chiamarsi `it_IT.aff` e `it_IT.dic` e trovarsi nella stessa
cartella (o in una directory di sistema di hunspell).

## Convenzione dei flag

Si usa `FLAG long` (ogni flag è **esattamente** 2 caratteri). I gruppi:

### Sostantivi

| Flag | Descrizione | Esempio |
|------|-------------|---------|
| `NO` | -o regolare | libro → libri |
| `NA` | -a regolare | casa → case |
| `NE` | -e regolare | fiume → fiumi |
| `MA` | -ma greco | problema → problemi |
| `FO` | -o invariante femminile | mano → mani |
| `NU` | -io → -i | bacio → baci |
| `NK` | -co/-go → -chi/-che | lago → laghi |
| `NM` | -co/-go → -i | medico → medici |
| `NC` | -cia dopo vocale → -cie | camicia → camicie |
| `NG` | -cia dopo consonante → -ce | pioggia → piogge |
| `NV` | -o invariante femminile | braccio → braccia |
| `NW` | -a invariante tema | collega → colleghi/colleghe |
| `NZ` | -a m/f separato | giornalista → giornalisti/giornaliste |
| `NX` | -e (carnefice) → -i | carnefice → carnefici |
| `NY` | -trice → -trici | attrice → attrici |
| `NI` | invariabile | città, caffè, re |

### Aggettivi

| Flag | Descrizione | Esempio |
|------|-------------|---------|
| `A1` | -o regolare | buono → buona/buoni/buone |
| `A2` | -e regolare | forte → forti |
| `AK` | -co → -chi/-che | bianco → bianchi/bianche |
| `AG` | -go → -ghi/-ghe | largo → larghi/larghe |
| `AM` | -co irregolare femminile | frenetico → frenetica/frenetici/frenetiche |
| `AB` | bello | bello → bella/belli/belle/bel/bei/begli |
| `AI` | invariabile | blu → blu |
| `ST` | superlativo assoluto | alto → altissimo |
| `ME` | avverbio in -mente | veloce → velocemente |

### Verbi regolari

| Flag | Descrizione | Esempio |
|------|-------------|---------|
| `V1` | 1ª coniugazione -are | amare |
| `V2` | 2ª coniugazione -ere | temere |
| `V3` | 3ª coniugazione -ire | partire |
| `VI` | -ire con inserto -isc- | capire → capisco |
| `VA` | -care (inserisce h) | giocare → giochiamo |
| `VB` | -giare/-ciare (i si assorbe) | mangiare → mangiamo |
| `VC` | -iare (inviare, sciare) | inviare → invii |
| `RF` | riflessivo con clitici | lavare → lavarsi |

### Verbi irregolari

| Flag | Verbo | Esempio forme irregolari |
|------|-------|--------------------------|
| `H1` | avere | ho, hai, ha, hanno |
| `F1` | fare | faccio, fai, fa, fanno |
| `D1` | dare | do, dai, dà, danno |
| `T1` | stare | sto, stai, sta, stanno |
| `P1` | potere | posso, puoi, può |
| `W1` | volere | voglio, vuoi, vuole |
| `O1` | dovere | devo, devi, deve |
| `X1` | venire | vengo, vieni, viene |
| `K1` | tenere | tengo, tieni, tiene |
| `B1`/`B2` | bere | bevo, bevi, beve (stem: bev-) |
| `I1` | dire | dico, dici, dice, dite |
| `AN`/`AW` | andare | vado, vai, va, vanno (stem: vad-) |
| `D2` | vedere | vedo, vedi, vidi, veduto |
| `M1`/`MU` | morire | muoio, muori, muore (stem: muo-) |
| `L1` | salire | salgo, sali, sale |
| `R1` | rimanere | rimango, rimani, rimasi |
| `Y1`/`Y2` | udire | odo, odi, ode (stem: od-) |
| `O2` | porre | pongo, poni, posi |
| `U1` | condurre | conduco, conduci, condussi |
| `Z1` | trarre | traggo, trai, trassi |
| `Q1` | piacere | piaccio, piaci, piacque |
| `R2` | vincere | vinco, vinci, vinsi |
| `G1` | aprire | apro, apri, aperto |

### Alterati (da concatenare al flag del sostantivo)

| Flag | Descrizione | Esempio |
|------|-------------|---------|
| `IN` | -ino/-ina | gatto → gattino |
| `ET` | -etto/-etta | libro → libretto |
| `EL` | -ello/-ella | albero → alberello |
| `ON` | -one/-ona | gatto → gattone |
| `AC` | -accio/-accia | parola → parolaccia |
| `UC` | -uccio/-uccia | casa → casuccia |
| `OZ` | -ozzo/-ozza | cosa → cosozza |
| `AS` | -astro/-astra | fratello → fratellastro |
| `BT` | alterati dal plurale | baci → bacetto |

### Prefissi (elisioni e prefissi)

| Flag | Descrizione | Esempio |
|------|-------------|---------|
| `DX` | l', all', dell', dall', nell', sull', coll', d' | l'isola, dell'acqua |
| `DU` | un' | un'amica |
| `PR` | ri- (iterativo su verbi) | riavere |
| `PS` | s- (privativo) | sfidare |
| `PD` | dis- | disarmare |
| `PI` | in-/im-/il-/ir- (negazione) | infelice |
| `PA` | anti- | antisettico |
| `PC` | co-/con- | coautore |
| `PE` | pre- | preriscaldare |
| `PF` | super- | supermercato |
| `PG` | sotto- | sottopassaggio |
| `PH` | contr-/contro- | contrattacco |
| `PJ` | extra-/ultra-/iper-/ipo-/inter- | extracurricolare |

## Disclaimer

Questo progetto è stato fortemente aiutato dall'intelligenza artificiale (IA)
in tutte le fasi di sviluppo: correzione dei bug morfologici nel `.aff`,
generazione del `.dic`, scrittura degli script di verifica e documentazione.
La supervisione umana ha guidato ogni decisione, ma la maggior parte del
lavoro tecnico è stata eseguita da un'IA.
