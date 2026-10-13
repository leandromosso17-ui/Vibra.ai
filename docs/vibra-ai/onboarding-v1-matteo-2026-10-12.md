# vibra.ai: documento di onboarding per il Claude di Leandro

Versione 1, 12 ottobre 2026. Redatto da Matteo (con il suo Claude) per portare il Claude di Leandro allo stesso livello di contesto. Dominio: vibra-ai.net.

## 0. Come usare questo documento (istruzioni per il Claude che lo legge)

Sei il Claude di Leandro, co-founder di vibra.ai. Questo documento ti dà il contesto condiviso. Regole di lavoro:

1. **Sparring partner critico, non validatore.** Dai analisi diretta e pushback con numeri e ipotesi esplicite. Se Leandro ha preferenze diverse sul tono, seguile.
2. **Non inventare dati.** Se manca un numero, chiedilo a Leandro o segnalalo come lacuna.
3. **Distingui sempre la natura di ogni affermazione**, usando queste etichette:
   - `[VERIFICATO]` letto su una fonte (indicata in fondo), con data.
   - `[DICHIARATO]` detto da Matteo o Leandro, non verificato.
   - `[IPOTESI]` stima o assunzione da testare.
   - `[DECISO]` scelta già presa dai founder.
   - `[PROPOSTA]` suggerimento fatto da un Claude, non ancora accettato dai founder. Non trattarlo come deciso.
4. **I prezzi e le tariffe cambiano.** Riverificali prima di usarli in decisioni o nei materiali verso clienti.
5. **Non sei un consulente legale, fiscale o finanziario.** Sui punti della sezione 9 dai informazioni e domande da portare a un professionista, non raccomandazioni definitive.
6. **Non sovrascrivere il lavoro del Claude di Matteo.** Vedi sezione 12.

## 1. Il progetto in 60 secondi

vibra.ai è un receptionist AI al telefono per piccole attività. Un agente vocale risponde 24/7 al telefono dell'attività, prende prenotazioni e appuntamenti, risponde a domande su orari, servizi e prezzi, e gestisce più chiamate in contemporanea. Le prenotazioni finiscono in un calendario e arrivano via email.

Problema che risolve: chiamate perse quando hai le mani occupate, sei fuori orario o sei già al telefono.

Fase: **validazione**. Nessuna società costituita, nessun cliente pagante.

## 2. Team

- **Matteo:** ex consulente in una boutique di AI consulting, dove ha costruito voicebot, campagne outbound e copilot per call center. Precedente esperienza in Amazon. Studia il MiM a ESCP. Costruisce il prodotto (landing, demo, integrazioni). Al momento è in Francia. `[DICHIARATO]`
- **Leandro:** compagno ESCP, tre esperienze nel venture capital e analisi approfondita del mercato voicebot. Complementare a Matteo. Co-founder. `[DICHIARATO]`
- **Ruoli di dettaglio e quote:** non definiti in questo documento. `[LACUNA]` da chiarire tra voi (chi fa vendite, chi onboarding, chi legale/amministrazione).
- **Capacità:** da gennaio la disponibilità di Matteo dipende dal lavoro che troverà e da dove. `[DICHIARATO]` Va considerato nella pianificazione.

## 3. Prodotto

**Settori con demo pronta:** ristoranti, hotel, studi dentistici, idraulici. Aperti ad altri settori su richiesta.

**Lingue:** oggi inglese; l'agente passa all'italiano se il chiamante lo parla. Pagine e agenti IT/FR pianificati, `[DECISO]` dopo la gestione del form di personalizzazione (che è stato poi abbandonato, vedi sezione 5).

**Funnel attuale**
1. Landing con demo live: il prospect lascia il numero, l'AI lo chiama in circa 10 secondi e lui fa la parte del cliente (circa 2 minuti). Riceve poi il riepilogo via email.
2. Fase 2 (implementazione): il cliente manda sito o punti elenco (servizi, orari, prezzi, regole, FAQ) e l'agente viene configurato sulla sua attività.
3. Prezzi non pubblici: sezione "Let's schedule a call". Sulla landing c'è un calcolatore del costo delle chiamate perse (chiamate/mese × % perse × 40% che volevano prenotare × scontrino medio). Il 40% è arbitrario. `[IPOTESI]`

**Stack**
- Voce/LLM: ElevenLabs Agents.
- Telefonia: Twilio (oggi numero US per le demo; servirà numero locale IT/FR).
- Hosting Render, database Supabase, email Resend (piani free o low cost).
- Repo privato su GitHub di Matteo. `[DECISO]` non pubblicarlo finché non ci sono più funzioni.

## 4. Stato attuale (12 ottobre 2026)

- Landing e demo funzionanti, design in Figma, feedback già raccolto da un professore e da Leandro. `[DICHIARATO]`
- In sviluppo: area "Your space": il prospect accede con la mail usata per la demo e vede il calendario delle prenotazioni prese nelle sue chiamate demo, alimentato dal webhook post-call di ElevenLabs, con Supabase. `[DICHIARATO]`
- Pitch di 7 minuti in preparazione, in forma di scenetta (non un pitch da VC) che mostra il dolore delle chiamate senza risposta. `[DICHIARATO]`
- Traction dichiarata: circa 100 interviste fatte e 10 prospect in conversazione. `[DICHIARATO da Matteo, da riconfermare con Leandro]`
- Società non costituita. Matteo ha ancora la P.IVA da consulente.

## 5. Decisioni prese `[DECISO]`

| Decisione | Note |
|---|---|
| Nome prodotto vibra.ai, dominio vibra-ai.net | |
| Demo standard per settore, senza form di personalizzazione | La landing dice "prova la demo"; la personalizzazione avviene in fase 2 |
| Agenti demo in inglese con passaggio all'italiano | Mantenere questo comportamento |
| Landing per settore in EN, IT, FR, ciascuna con agente nella lingua | Dopo le priorità attuali |
| Repo non pubblico per ora | |
| Anti-abuso rimandato | Le demo girano solo con Matteo presente |
| Validare con pilota gratuiti di un mese, far partire i pagamenti a gennaio e costituire la società a gennaio, quando si sa dove lavora Matteo | |
| Coordinamento con un foglio di stato condiviso | Da creare (sezione 12) |

## 6. Unit economics

**Costi variabili (USD, da riverificare)**
- ElevenLabs Agents: $0,08/min su tutti i piani. L'inclusione di minuti nei piani non abbassa il prezzo (es. Business: $990 per 12.375 min, sempre $0,08). Tariffa burst $0,16/min per i picchi. LLM e telefonia fatturati a parte. `[VERIFICATO, settembre 2026]`
- LLM leggero: Gemini 2.5 Flash circa $0,0012/min nel calcolatore ElevenLabs. `[VERIFICATO]`
- Twilio Italia: circa $0,004/min per ricevere su numero locale (la tabella estratta era confusa). `[DA VERIFICARE sul proprio account]`. Costo mensile del numero e requisiti regolatori IT: non trovati.
- ElevenLabs è circa il 90% del costo; la telefonia conta poco.

**Modello usato:** costo all-in `[IPOTESI]` €0,11/min (circa €0,09 base più il 20% di "minuti sporchi": silenzi, spam, chiamate interrotte, test). Cambio USD/EUR approssimato.

| Chiamate/mese | 1,5 min/chiamata | 2 min/chiamata |
|---|---|---|
| 100 | 150 min, €17 | 200 min, €22 |
| 300 | 450 min, €50 | 600 min, €66 |
| 600 | 900 min, €99 | 1.200 min, €132 |
| 1.000 | 1.500 min, €165 | 2.000 min, €220 |

Più circa €3/mese di numero `[IPOTESI]`.

**Conseguenze**
- Un piano flat a €99 con margine lordo dell'80% regge solo fino a circa 180 minuti (circa 90–120 chiamate). Un flat senza tetto di minuti è un rischio.
- Il costo vero è il tempo umano: onboarding stimato 3 h e call di vendita 1–1,5 h per cliente `[IPOTESI]`. A €30/h sono circa €135 per cliente, cioè circa 2 mesi di margine su un piano da €89.
- LTV `[IPOTESI]`: con churn PMI al 5%/mese e margine lordo circa 75%, LTV circa €1.300, CAC massimo sostenibile circa €400 (3:1).
- Build vs buy: l'orchestrazione (hosting) vale quasi tutto il costo. Uno stack proprio (Matteo ha esperienza con Pipecat) potrebbe ridurlo, ma va quantificato prima di decidere. `[LACUNA]` nessun numero verificato.

## 7. Mercato e concorrenti

**HeyDiga (Spagna/Italia)**, listino letto dalla loro pagina il 9 ottobre 2026, prezzi IVA esclusa `[VERIFICATO]`:

| Piano | €/mese | Minuti | Chiamate in contemporanea | €/min |
|---|---|---|---|---|
| Lite | 49 | 200 | 5 | 0,245 |
| Start (consigliato) | 99 | 500 | 10 | 0,198 |
| Growth | 169 | 900 | 15 | 0,188 |
| Pro | 279 | da 1.500 | 25 | 0,186 |

- WhatsApp conversazionale come add-on da €39/mese su ogni piano (200 / 500 / 1.000 / 1.500 conversazioni).
- Lite: "Inizia gratis", configurazione autonoma. Start: collegato al gestionale. Growth: lista d'attesa, cancellazioni con carta, recensioni, export e report. Pro: più sedi, API, revisione trimestrale.
- Scala quasi lineare (circa €0,17 per minuto in più): non c'è sconto di volume vero, si vende per funzioni.
- Margine stimato nostro `[IPOTESI]`: circa 40–55% a uso pieno; per un margine SaaS normale devono contare su un utilizzo medio sotto il 50% dei minuti inclusi.
- Funding: seed da €5,5M guidato da 6DC con Kfund, Italian Founders Fund e Decelera. Cinque verticali: bellezza, auto, salute, ristorazione, immobiliare. Dichiarano 78% di automazione e 85,3% di risoluzione (dati loro, non verificati). `[VERIFICATO come notizia]`
- Hotel e idraulici/trades non compaiono tra i loro verticali. `[DA CONFERMARE sul loro menu "Attività"]`

**Altri:** CloudTalk AI Receptionist da €99/mese per 200 minuti, più un piano telefonico da €25/utente. Retell, Vapi, Bland, Synthflow: piattaforme per sviluppatori con prezzi tra circa $0,05 e $0,31/min a seconda dei componenti. Wonderful (enterprise): ancora da mappare. `[LACUNA]`

## 8. Pricing: stato della discussione (nulla di questo è deciso)

**Opzioni valutate:** flat a scaglioni, a minuto/chiamata, a prenotazione, setup più canone.
- A chiamata: il margine dipende dalla durata, che non è ancora misurata. A €0,11/min, una chiamata da 3 minuti costa €0,33 e da 5 minuti €0,55. Se la durata è lunga il margine crolla.
- A minuto: protegge il margine, ma le PMI temono la bolletta variabile.
- A prenotazione: allinea il valore, ma ha problemi di attribuzione, no-show e ricavi volatili.

**`[PROPOSTA]`** Misurare a minuto ma comunicare in chiamate: pacchetto di minuti incluso (es. "circa 75 chiamate"), overage a minuto, nessuna setup fee, configurazione inclusa, prezzo Start allineato a quello di HeyDiga (circa €99, circa 400 minuti) e posizionamento in verticali non coperti (hotel, idraulici). Rischio: se l'onboarding resta manuale (3 h), il margine non lo copre; va portato sotto i 30–45 minuti generando la configurazione dal sito del cliente.

**`[PROPOSTA]`** Non competere sul prezzo contro un concorrente finanziato; un prezzo molto basso su un servizio dove un errore costa un cliente segnala bassa qualità.

**Prezzi nascosti:** in validazione servono come strumento per testare ancoraggi diversi, a patto di registrare ogni preventivo e la reazione. Con l'ancora pubblica a €99 di HeyDiga, i prospect useranno quel numero. Da rivedere.

## 9. Legale e fiscale (informazioni, non consulenza)

- **P.IVA individuale di Matteo:** utilizzabile per i primi pilota a pagamento. Da verificare con un commercialista: codice ATECO, regime (forfettario o ordinario), tetto di €85.000 di ricavi, compatibilità con una futura società.
- **Limiti della P.IVA individuale:** il fatturato è tutto di Matteo (non si può dividere con Leandro in modo pulito); la responsabilità è personale; gli investitori non investono in una persona fisica.
- **SRL / SRLS in Italia:** costi di apertura riportati tra circa €500 e circa €800 (capitale escluso) per una SRLS, e oltre €2.600 per una SRL ordinaria, con fonti discordanti. La firma può avvenire in videoconferenza. Servono verifiche sui requisiti per essere "startup innovativa". Costi correnti e di chiusura non verificati.
- **EU Inc. (28° regime):** proposta della Commissione del 18 marzo 2026, in iter legislativo, obiettivo di accordo a fine 2026, servono atti di attuazione. Non utilizzabile ora. Non cambia le norme fiscali e del lavoro nazionali.
- **Società estone (OÜ, e-Residency):** circa €415 di costi statali iniziali, poi €700–2.000 l'anno o più (altre fonti fino a €4.000). Richiede indirizzo legale e referente in Estonia. Rischio di esterovestizione: se le decisioni sono prese dall'Italia, le autorità italiane possono trattarla come società italiana. Nessun beneficio fiscale se gestita da un solo paese. La registrazione IVA estone è stata irrigidita. `[PROPOSTA]` sconsigliata ora.
- **Francia:** ora i founder sono in Francia, quindi una società francese potrebbe essere più coerente, ma non ne abbiamo verificato costi e requisiti. `[LACUNA]`
- **Dati personali:** si trattano voci e dati dei clienti dei clienti. Servono DPA con i clienti e con i sub-fornitori (ElevenLabs, Twilio), consenso dove serve e un avviso "stai parlando con un'IA". Per i dati sanitari (dentisti) servono cautele speciali: `[PROPOSTA]` evitare i dentisti per i pilota finché non c'è società e DPA.
- **Piano deciso:** pilota gratuiti da ora, pagamenti da gennaio, costituzione della società a gennaio.

## 10. Piano pilota `[PROPOSTA]`, da accettare o modificare

- Due coorti da 5 clienti: la prima circa dal 15 ottobre al 15 novembre, la seconda fino a metà dicembre.
- Prima di attivare, una lettera d'intenti: "dopo 30 giorni, se continuo, pago €X al mese da data Y". Chi rifiuta di firmare dà già la risposta.
- Tetto di minuti gratuiti per cliente (es. 200) e data di fine fissa. Alla fine o paga o si spegne.
- Accordo di pilota di una pagina: servizio sperimentale, nessuna garanzia di prenotazioni, il cliente può staccare il forwarding in qualsiasi momento, l'agente dichiara di essere un'IA, cosa succede ai dati a fine pilota.
- Partire da ristoranti, hotel e idraulici.
- Limite: da gennaio la gestione dipende dalla capacità di Matteo (5–8 ore a settimana?), quindi meglio coorti piccole e curate che 20 clienti trascurati.

## 11. Ipotesi più rischiose e come testarle

| # | Ipotesi | Test | Soglia |
|---|---|---|---|
| 1 | Il cliente paga ≥€89/mese | Pilota a pagamento o lettera d'intenti | ≥3 su 10 prospect qualificati |
| 2 | Le chiamate perse sono tante e di clienti nuovi | 30 giorni di registro chiamate dalla telefonia del cliente | ≥15 perse/mese |
| 3 | Il calendario non è un ostacolo | Chiedere il gestionale usato; il rischio principale è la doppia prenotazione con un calendario separato | Integrazione fattibile o escludere il settore |
| 4 | Il forwarding funziona in Italia e Francia | Provarlo con 5 attività reali | Attivo in meno di 1 h, senza costi extra per il cliente |
| 5 | La qualità in italiano regge | 50 chiamate reali; misurare risolte senza umano ed errori su prezzi/orari | ≥80% risolte, 0 prenotazioni sbagliate |
| 6 | La durata media è 1,5–2 min | Misurarla nel pilota (e guardare la distribuzione, non solo la media) | Costo per cliente dentro il piano |
| 7 | La parte legale è a posto | Società o P.IVA, DPA, avviso IA | Prima di incassare |

## 12. Come lavorate in due, e come lavorano i due Claude

**Stato condiviso `[DECISO]` ma da creare:** un foglio (es. Google Sheet) con una riga per attività:

| Attività | Owner (Matteo/Leandro) | Stato | Ultimo aggiornamento | Link/note |
|---|---|---|---|---|

**Convenzioni per entrambi i Claude**
1. Prima di iniziare un lavoro, leggi il foglio di stato. Se un'attività è già in corso con un altro owner, avvisa Leandro prima di toccarla.
2. Ogni documento prodotto riporta data, autore e versione. Non sovrascrivere versioni del collega: crea una nuova versione.
3. Se le informazioni di Matteo e Leandro si contraddicono, segnalalo a entrambi. Non risolvere in silenzio.
4. Dati di terzi (clienti, prospect): non inserirli in documenti condivisi oltre il minimo necessario.
5. Fine sessione: scrivi un handoff di 5 righe (cosa è stato fatto, cosa resta aperto, decisioni prese, dati mancanti, prossimo passo).

## 13. Domande aperte (da risolvere tra voi)

1. Ruoli, quote e accordi tra i due founder.
2. Dove vivranno entrambi nei prossimi 12 mesi, e se Leandro è residente fiscale nello stesso paese.
3. L'AI risponde a tutte le chiamate o solo a quelle perse e fuori orario (overflow)?
4. Quali sono i 10 prospect (settore, dimensione, che calendario/gestionale usano) e a che punto sono?
5. Cosa è emerso nelle 100 interviste, in particolare sul prezzo?
6. Quanto tempo reale richiede oggi un onboarding?
7. Competitor in Francia e paese di lancio.
8. Cassa disponibile per i pilota.
9. Cosa include il "Inizia gratis" di HeyDiga Lite.

## 14. Prima istruzione da dare al Claude di Leandro (da incollare insieme a questo documento)

> Leggi il documento. Poi, senza chiedermi nulla prima: (1) riassumilo in 10 righe per verificare di averlo capito; (2) elenca le 5 cose che contesti di più, con motivazione e numeri; (3) elenca le 5 informazioni mancanti che ti servono per darmi analisi migliori. Da qui in poi lavora come sparring partner critico, distingui verificato/ipotesi/deciso e non inventare dati.

## Fonti (consultate tra il 9 e il 12 ottobre 2026; riverificare)

- ElevenLabs Agents pricing: https://www.getmacha.com/blog/elevenlabs-agents-pricing-explained
- Conversational AI pricing 2026: https://trtc.io/blog/conversational-ai-pricing-2026
- Twilio Voice, Italia: https://www.twilio.com/de-de/voice/pricing/it
- HeyDiga (pagina prezzi: screenshot di Matteo del 9 ottobre 2026; funding): https://emprendedores.es/startups/heydiga-levanta-55-millones-de-euros-en-su-ultima-ronda-de-inversion/ e https://ecosistemastartup.com/heydiga-levanta-e5-5m-para-automatizar-llamadas-con-ia/
- CloudTalk: https://www.cloudtalk.io/it/blog/quanto-costa-servizio-risposta-ia/
- EU Inc.: https://www.eubelius.com/en/news/the-eu-inc-the-european-commissions-proposal-for-a-28th-corporate-regime
- Estonia e-Residency: https://enty.io/blog/estonian-e-residency-fees-2026-every-cost-line-item e https://www.e-resident.gov.ee/blog/posts/company-registration-in-italy-vs-estonia/
- Costi SRL/SRLS: https://www.economyup.it/startup/startup-tutto-quel-che-c-e-da-pagare-per-mettersi-in-societa/ e https://www.emiliaromagnastartup.it/it/node/164180
