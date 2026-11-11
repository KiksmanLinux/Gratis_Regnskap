# Funksjonskart: norske regnskapsprogrammer, regelverk og nye krav

**Status:** kartlegging per 11. november 2026
**Formål:** gi en så komplett funksjonsliste som mulig for de vanligste regnskapsprogrammene i Norge, og samtidig vise hvilke regelverk og kommende krav som påvirker hva et regnskapsprogram må kunne.
**Bruk:** hver funksjon har en ID (for eksempel `BOK-014`). ID-ene kan brukes direkte som backlog, kravspesifikasjon eller sjekkliste i `Gratis_Regnskap`.

> Forbehold: Funksjonsomfang varierer med pakke, avtale og versjon. Matrisen er laget på grunnlag av leverandørenes egne produkt- og hjelpesider, offentlige sammenligninger og Skatteetatens/Lovdata sine sider. Der noe ikke er bekreftet i offentlig dokumentasjon, er det markert `?`. Priser er utelatt fordi de endres ofte; forretningsmodellene er omtalt der de påvirker funksjonstilgangen.

**Kort oppsummert:** katalogen inneholder **658 unike funksjoner** fordelt på **16 domener**, en modulmatrise for **10 systemer**, og en tidslinje for regelendringene fram til 2030. De viktigste nye kravene er e-faktura fra 2027, SAF-T 1.40 fra 2027, kjøpers organisasjonsnummer på faktura fra 2028, og plikt til å motta e-faktura og bokføre elektronisk fra 2030.

---

## 1. Hvilke programmer er «de vanligste»?

Markedet er ikke ett marked. Det deles i praksis i fem lag:

### 1.1 Småbedriftsystemer (ENK, små AS, selvstendige)

Disse er de mest brukte i den brede småbedriftsmassen, og de fem som oftest sammenlignes:

| System | Typisk bruker | Kjennetegn |
|---|---|---|
| **Fiken** | ENK, små AS, gründere | Én grunnpris, ubegrenset bilag og brukere, enkel fakturering, tillegg for bank, lønn, prosjekt, tid, KID og API |
| **Conta** | ENK, små AS | Norsk, årsfakturert abonnement, mobilapp, AI-kontering («Kaia»), KID/EHF i Smart-pakken, prosjekt i Smart |
| **Tripletex** | Små og mellomstore AS | Modulbasert: regnskap, faktura, lønn, prosjekt, tid, lager, CRM, bransjemoduler for elektro/VVS/landbruk, stort API og mange integrasjoner |
| **PowerOffice Go** | Små og mellomstore AS | Modulær økonomiflyt: regnskap, faktura, bank/betaling, lønn, prosjekt, tid, reiseregning, godkjenningsflyt, 300+ integrasjoner |
| **Visma eAccounting** | ENK og små AS | Enkel regnskap/faktura, bank og årsoppgjør; lønn er avviklet fra 2024; moduler for tilbud/ordre, lager, prosjekt og rapportering |

### 1.2 Mellomstore systemer og ERP

Brukes når flere selskaper, avdelinger, lager, produksjon eller konsern skal håndteres i samme løsning:

- **24SevenOffice** (nå profilert som **Finago**) – regnskap, faktura, CRM, prosjekt, tid, lønn, lager, AI-bokføring.
- **Duett** – norsk økonomisystem med røtter til 1983, utbredt hos regnskapskontorer og SMB; regnskap, faktura, lønn, rapporter, budsjett, kontrollsenter.
- **Uni Economy / Unimicro** – norsk regnskap og ERP, mye brukt av regnskapsbyråer og mellomstore bedrifter.
- **Xledger** – skybasert ERP med én database: regnskap, bank, fakturering, budsjett, anlegg, lønn/reise, prosjekt, BI, konsern, ESG.
- **Visma Net** – standardisert ERP for mellomstore: økonomi, logistikk, lønn/HR, prosjekt, rapportering.
- **Visma Business / Business NXT** – Norges mest utbredte tradisjonelle økonomisystem; NXT er skyversjonen med finans, HR/lønn, logistikk, lager, produksjon, konsern og API/GraphQL.
- **Visma Global, Visma Enterprise, Visma Contracting** – eldre og bransjespesifikke Visma-løsninger.
- **Microsoft Dynamics 365 Business Central** – alt-i-ett ERP med stort AppSource-økosystem.
- **Mamut, Zirius, Systema, InfoEasy, Matrix, DI-Systemer, Unit4 Agresso, Sage, Odoo, Fortnox, e-conomic** – øvrige systemer man møter i det norske markedet, særlig hos byråer og bransjevirksomheter.

### 1.3 Lønn og HR (ofte egne systemer)

- **Visma Lønn**, **Huldt & Lillevik Lønn**, **PowerOffice Go Lønn**, **Tripletex Lønn**, **Fiken Lønn**, **Conta Lønn**, **24SevenOffice Lønn**, **Xledger Lønn**, **Visma Payroll**.
- **Simployer** og tilsvarende for HR, personalhåndbok, HMS og opplæring.

### 1.4 Årsoppgjør, skatt og revisjon

- **Visma Finale** (årsoppgjør, skatt, konsern, driftsmidler, avstemming), **Sticos Oppslag**, **Talla**, **Aspia**, **Aider** og byråenes egne årsoppgjørsavdelinger.
- Revisjonsverktøy og attestasjon integreres typisk via API, SIE-4 eller SAF-T.

### 1.5 Bransje- og fagsystemer som kobles til regnskapet

- Bygg/anlegg: **Proresult**, **SmartDok**, **Visma Contracting**, **Telaris**.
- Handel/POS: **Front Systems**, **PCKasse**, **Susoft**, **Zettle**, **Vipps**, **Stripe**.
- Nettbutikk: Shopify, WooCommerce, Mystore, Adobe Commerce og norske markedsplasser.
- Landbruk: **Agro Økonomi**, Tripletex landbruk.
- Integrasjonsplattformer: **iizy**, **Telaris**, **PowerOffice-appen**, **Tripletex-appen**, **Visma App Store**.

---

## 2. Slik leses funksjonskatalogen

Hver linje er én funksjon eller ett funksjonskrav. ID-ene er gruppert etter domene:

| Prefiks | Domene |
|---|---|
| `GRU` | Plattform, arkitektur og fellesfunksjoner |
| `OPP` | Oppsett, konfigurasjon og migrering |
| `BOK` | Bokføring, bilag og løpende regnskap |
| `SAL` | Salg, fakturering og kundefordringer |
| `INN` | Innkjøp, leverandørfaktura og betaling |
| `BAN` | Bank, finans og likviditet |
| `LØN` | Lønn, HR og reise/utlegg |
| `PRO` | Prosjekt, tid og ressursstyring |
| `VAR` | Varelager, logistikk og produksjon |
| `RAP` | Rapportering, analyse og styring |
| `ÅRS` | Årsoppgjør, skatt og myndighetsrapportering |
| `MVA` | Merverdiavgift og avgiftsoppgjør |
| `AUT` | Automatisering, AI og datadeling |
| `BRA` | Bransje- og selskapsformspesifikke funksjoner |
| `UX` | Brukeropplevelse, samarbeid og support |
| `SIK` | Sikkerhet, personvern og compliance |

---

## 3. Funksjonskatalog

### 3.1 Plattform, arkitektur og fellesfunksjoner (`GRU`)

- **GRU-001 Skybasert løsning** – tilgang i nettleser uten lokal installasjon; data og oppdateringer driftes av leverandøren.
- **GRU-002 On-premise / privat sky** – for ERP-kunder med krav om egen drift eller eget datasenter.
- **GRU-003 Mobilapp (iOS/Android)** – bilde av bilag, timeføring, reiseregning, godkjenning, lønnsslipp, dashboards.
- **GRU-004 Responsivt webgrensesnitt** – full funksjonalitet på nettbrett og telefon.
- **GRU-005 Flerfirma** – flere foretak i samme innlogging med egen kontoplan, brukere og rapportering.
- **GRU-006 Konsernstruktur** – mor/datter, eierandeler, elimineringer, konsernregnskap og konsernrapportering.
- **GRU-007 Flervaluta** – føring, fakturering og rapportering i flere valutaer med daglige kurser.
- **GRU-008 Flerspråklig grensesnitt** – norsk bokmål, nynorsk og engelsk, eventuelt flere språk.
- **GRU-009 Roller og rettigheter** – granulær tilgang per modul, funksjon, firma, avdeling og handling.
- **GRU-010 To-faktorautentisering (2FA)** – påkrevd for administratorer og valgfritt/påkrevd for alle.
- **GRU-011 SSO** – innlogging via Microsoft/Google/Entra ID eller annen identitetsleverandør.
- **GRU-012 Revisor- og byråtilgang** – lese- eller skrivetilgang uten å dele passord, med egne roller.
- **GRU-013 Klientoverbygg for byrå** – klientliste, status, oppgaver, frister og samlet rapportering på tvers av klienter.
- **GRU-014 Revisjonsspor (audit trail)** – hver endring logges med bruker, tidspunkt, før/etter-verdi og årsak.
- **GRU-015 Uforanderlig hendelseslogg** – logging som ikke kan slettes eller redigeres av bruker.
- **GRU-016 Nummerserier** – separate, ubrutte serier for bilag, fakturaer, kreditnotaer og interne dokumenter.
- **GRU-017 Periodelåsing** – låsing av måned/termin etter avslutning.
- **GRU-018 Årslåsing** – låsing av regnskapsåret etter årsavslutning.
- **GRU-019 Gjenåpning med logg** – kontrollert gjenåpning av låst periode, alltid sporet og begrunnet.
- **GRU-020 Import og eksport** – Excel/CSV, PDF, XML, SIE-4, SAF-T, JSON og egne filformater.
- **GRU-021 REST-API** – åpent, dokumentert API for kunder, leverandører, bilag, fakturaer, prosjekter og lønn.
- **GRU-022 GraphQL-API** – fleksibel spørring for ERP og integrasjonspartnere.
- **GRU-023 Webhooks og hendelser** – pushvarsel når faktura, bilag, betaling eller prosjekt endres.
- **GRU-024 Sandbox/testforetak** – eget testmiljø uten å påvirke produksjonsregnskapet.
- **GRU-025 App store / integrasjonsmarked** – godkjente tredjepartsintegrasjoner med én-klikks aktivering.
- **GRU-026 Databehandleravtale** – standard DPA med underdatabehandlere og dokumentert behandlingsgrunnlag.
- **GRU-027 Datalagring i Norge/EØS** – oppbevaring og sikkerhetskopi innenfor norsk/EØS-rett.
- **GRU-028 Backup og gjenoppretting** – dokumentert RPO/RTO, testet gjenoppretting og historikk.
- **GRU-029 Kryptering** – kryptering i transitt og i ro, nøkkelrotasjon og hemmelighetshåndtering.
- **GRU-030 Regelverksoppdatering** – automatisk oppdatering av satser, MVA-koder, kontoplaner og skjemaer.
- **GRU-031 Varsler** – e-post, SMS og push ved frister, godkjenninger, avvik og nye bilag.
- **GRU-032 Søk og filtrering** – fritekstsøk, perioder, beløp, kunde, leverandør, prosjekt og lagrede visninger.
- **GRU-033 Masseoperasjoner** – massebokføring, massetildeling, masseutsending og masseoppdatering.
- **GRU-034 Egendefinerte felt** – tilleggsfelt på kunde, leverandør, vare, prosjekt og bilag.
- **GRU-035 Rapporter og eksport** – alle lister kan eksporteres til Excel/CSV/PDF.
- **GRU-036 Dashboards** – tilpassbare grafer, nøkkeltall og trender per bruker/rolle.
- **GRU-037 Oppgave- og fristkalender** – egne og delte oppgaver, frister og påminnelser.
- **GRU-038 Dokumentarkiv** – sentralt arkiv med versjoner, metadata, søk og tilgangsstyring.
- **GRU-039 Elektronisk signering** – signering av årsoppgjør, avtaler, reiseregninger og godkjenninger.
- **GRU-040 AI-assistent** – språklig spørring mot egne data og forslag til handlinger.
- **GRU-041 Agent-/MCP-tilgang** – maskinlesbar tilgang for AI-verktøy med scoped tilgang og logging.
- **GRU-042 Tilgjengelighet (WCAG)** – tastaturnavigasjon, kontrast, skjermleser og universell utforming.
- **GRU-043 Offline-modus** – registrering av bilag, timer og utlegg uten nett, med synkronisering etterpå.
- **GRU-044 Skalerbarhet og ytelse** – håndtering av store datamengder, mange brukere og høyt transaksjonsvolum.
- **GRU-045 Automatisk lagring og utkast** – bilag, fakturaer og skjemaer lagres fortløpende.
- **GRU-046 Hendelsesbasert bokføring** – bokføring utløses av faktura, betaling, lønn, lager eller prosjekt.
- **GRU-047 Dataeksport ved bytte** – full eksport av regnskap, bilag og vedlegg i lesbart format.
- **GRU-048 Sletting og avvikling** – kontrollert avslutning av foretak med lovpålagt tilgjengelighet etter avvikling.

### 3.2 Oppsett, konfigurasjon og migrering (`OPP`)

- **OPP-001 Foretaksregistrering** – navn, organisasjonsnummer, adresse, underenheter og kontaktinfo.
- **OPP-002 MVA-registrering** – MVA-plikt, registreringsdato, terminer, blandet virksomhet og avgiftskoder.
- **OPP-003 Regnskapsår og perioder** – kalenderår eller avvikende regnskapsår, delperioder og terminer.
- **OPP-004 Kontoplan** – NS 4102 som standard, bransjetilpassede kontoplaner og egne konti.
- **OPP-005 Kontomapping** – kobling mot næringsspesifikasjon, SAF-T og skattemelding.
- **OPP-006 Kontoegenskaper** – kontotype, MVA-kode, avdeling, prosjekt, sperring og standardtekst.
- **OPP-007 Bankkontoer** – flere driftskonti, valutakonti, kassekreditt og sperrede klientmidler.
- **OPP-008 Brukere og roller** – invitasjon, rollevalg, ansattkobling og tilgangsperioder.
- **OPP-009 Godkjennere og attestanter** – godkjenningshierarki, beløpsgrenser, delegasjon og ferieavvikling.
- **OPP-010 Nummerserier og bilagstyper** – egne serier per bilagstype, avdeling eller foretak.
- **OPP-011 Fakturainnstillinger** – logo, farger, maler, betalingsbetingelser, KID og kontonummer.
- **OPP-012 Standardtekster** – fritekst, vilkår, purretekster og e-postmaler på flere språk.
- **OPP-013 Avdelinger og kostnadssteder** – hierarki, leder, budsjett og rapportering per enhet.
- **OPP-014 Prosjektstruktur** – prosjekttyper, aktiviteter, team, budsjett og faktureringsmodell.
- **OPP-015 Vareregister** – varenummer, enhet, pris, MVA, lagerkonto og innkjøpskonto.
- **OPP-016 Prislister og rabatter** – kundepriser, kampanjer, rabattmatriser og valuta.
- **OPP-017 Integrasjoner** – bank, Altinn/Skatteetaten, Vipps, kassesystem, nettbutikk, CRM og lønn.
- **OPP-018 Altinn 3-oppsett** – kobling mot Altinn 3 for MVA, skattemelding, a-melding og årsregnskap.
- **OPP-019 Åpningsbalanse** – innlesing av saldoer per kontodato og kontroll av balanse.
- **OPP-020 Migrering fra annet system** – import av kontoplan, saldoer, reskontro, bilag og vedlegg.
- **OPP-021 Importveiviser** – stegvis veiledning med validering, feilrapport og forhåndsvisning.
- **OPP-022 Historikk og arkiv** – tilgang til tidligere år, også etter systemskifte.
- **OPP-023 Maler for nye foretak** – standard oppsett for ENK, AS, holdingselskap, forening og prosjekt.
- **OPP-024 Klientmaler for byrå** – gjenbrukbare kontoplaner, regler, rapporter og oppgaveflyt.
- **OPP-025 Rollout og opplæring** – onboarding, sjekklister, kurs og sertifisering.
- **OPP-026 Varslingsinnstillinger** – hvem varsles om hva, på hvilken kanal og når.
- **OPP-027 Selskapsform** – ENK, AS, ASA, ANS/DA, NUF, stiftelse, forening, borettslag eller sameie.
- **OPP-028 Bransjevalg** – tilpasset kontoplan, MVA-regler, rapporter og moduler for valgt bransje.
- **OPP-029 Revisjonsplikt** – markering av revisjonsplikt/fritak og kobling til revisor.
- **OPP-030 Sperringer** – sperret konto, sperret kunde, kredittgrense og sperret periode.

### 3.3 Bokføring, bilag og løpende regnskap (`BOK`)

- **BOK-001 Manuell bilagsføring** – registrering av debet/kredit med dato, tekst, beløp og MVA.
- **BOK-002 Frie posteringer** – journalpostering uten kunde/leverandør, med valgfri bilagsreferanse.
- **BOK-003 Bilagsmaler** – gjenbrukbare maler for faste kostnader, husleie, strøm og lignende.
- **BOK-004 Gjentakende bilag** – automatisk generering etter intervall med forhåndsvisning og godkjenning.
- **BOK-005 Bilagsinnboks** – lasting av bilag via web, e-post, mobil, skanner eller integrasjon.
- **BOK-006 Mobil bildefangst** – ta bilde av kvittering og send direkte til innboksen.
- **BOK-007 OCR og dokumenttolkning** – automatisk utlesing av dato, beløp, MVA, leverandør og fakturanummer.
- **BOK-008 EHF-mottak** – mottak og tolkning av elektroniske fakturaer i EHF/Peppol-format.
- **BOK-009 Duplikatkontroll** – varsel når samme faktura eller kvittering registreres flere ganger.
- **BOK-010 Bilagsvalidering** – kontroll av påkrevde felt, dato, beløp, MVA og organisasjonsnummer.
- **BOK-011 Bilagsnummer og vedlegg** – hvert bilag får nummer og kobles til dokumentasjonen.
- **BOK-012 Automatisk kontering** – forslag til konto basert på leverandør, tekst, historikk og regler.
- **BOK-013 AI-kontering med læring** – modellen lærer av brukerens valg og forbedrer forslagene.
- **BOK-014 Automatisk MVA-kode** – MVA-kode foreslås ut fra vare, tjeneste, land og historikk.
- **BOK-015 Kunde- og leverandørreskontro** – separate reskontroer med åpne poster per part.
- **BOK-016 Åpne poster** – oversikt over ubetalte fakturaer, delbetalinger og kreditnotaer.
- **BOK-017 Matching av inn- og utbetalinger** – automatisk kobling mot faktura, KID eller beløp/dato.
- **BOK-018 Automatisk bankavstemming** – banktransaksjoner hentes og foreslås bokført.
- **BOK-019 Bankregler** – egne regler for gjentakende transaksjoner, gebyrer, renter og overføringer.
- **BOK-020 Kontantbilag og kasse** – kasseoppgjør, vekslepenger, kontantsalg og kassedifferanse.
- **BOK-021 Kasseavstemming** – avstemming av kasse mot kontantbeholdning og kassesystem.
- **BOK-022 Periodisering** – fordeling av kostnader og inntekter over riktig periode.
- **BOK-023 Forskuddsbetalte og opptjente poster** – automatiske periodiseringsserier med reversering.
- **BOK-024 Avsetninger** – avsetning for påløpte kostnader, feriepenger, garantier og tap.
- **BOK-025 Avskrivninger** – beregning og bokføring av regnskapsmessige avskrivninger.
- **BOK-026 Anleggsregister** – driftsmidler med anskaffelsesdato, kostpris, levetid og restverdi.
- **BOK-027 Skattemessige avskrivninger** – saldoavskrivning etter skatteloven, separat fra regnskapet.
- **BOK-028 Avskrivningsmetoder** – lineært, saldo, progressivt og egendefinert løp.
- **BOK-029 Varelager** – løpende lagerregnskap eller periodisk varetelling.
- **BOK-030 Varetelling** – telling, telling per lokasjon og justering mot bokført beholdning.
- **BOK-031 Lagerverdsettelse** – FIFO, veid gjennomsnitt, standardkost og laveste verdi.
- **BOK-032 Lagerendring** – automatisk bokføring av endring i varelager ved årsslutt.
- **BOK-033 Prosjekt, avdeling og objekt** – merking av bilag på flere dimensjoner samtidig.
- **BOK-034 Internfakturering** – fakturering mellom avdelinger eller selskaper i konsernet.
- **BOK-035 Valutabilag** – registrering i utenlandsk valuta med historisk kurs.
- **BOK-036 Kursdifferanser** – automatisk beregning og bokføring av valutagevinst/-tap.
- **BOK-037 Kreditnota** – korreksjon av salg med kobling til opprinnelig faktura.
- **BOK-038 Korrigeringsbilag** – retting av feil med sporbar kobling til originalbilaget.
- **BOK-039 Tilbakeføring** – reversering av feilpostering uten sletting.
- **BOK-040 Slettesperre** – bokførte bilag kan ikke slettes, bare korrigeres.
- **BOK-041 Regnskapsårslåsing** – avslutning som overfører saldoer til neste år og låser året.
- **BOK-042 Kontrolliste for uavstemte kontoer** – varsel om kontoer med saldo som ikke er avstemt.
- **BOK-043 Kontroll for manglende bilag** – liste over transaksjoner uten dokumentasjon.
- **BOK-044 MVA-avvikskontroll** – sammenligning av MVA-konto, MVA-melding og bilag.
- **BOK-045 Reskontroavvik** – kontroll av at reskontro stemmer med hovedbok.
- **BOK-046 Hovedbok** – alle posteringer per konto med drill-down til bilag.
- **BOK-047 Saldobalanse** – alle kontoer med inngående, bevegelse og utgående saldo.
- **BOK-048 Bilagsjournal** – kronologisk liste over alle bilag med nummer og referanse.
- **BOK-049 Transaksjonsdetaljer** – detaljert liste med alle dimensjoner og vedlegg.
- **BOK-050 Resultatregnskap** – inntekter, kostnader og resultat per periode og sammenligning.
- **BOK-051 Balanse** – eiendeler, egenkapital og gjeld per dato.
- **BOK-052 Kontantstrømoppstilling** – indirekte eller direkte metode, med avstemming mot bank.
- **BOK-053 Egenkapitaloppstilling** – endringer i egenkapitalen med utbytte, emisjon og resultat.
- **BOK-054 Noteopplysninger** – maler og beregninger for lovpålagte noter.
- **BOK-055 Konsern og eliminering** – eliminering av interne transaksjoner og mellomværender.
- **BOK-056 MVA-kompensasjon** – oppsett og rapportering for virksomheter med kompensasjonsrett.
- **BOK-057 Tilskudd og gaver** – sporing og bokføring av øremerkede midler.
- **BOK-058 Klientmidler** – separate konti og rapportering for klientmidler i byrå.
- **BOK-059 Stiftelser og foreninger** – tilpasset kontoplan, årsregnskap og rapportering.
- **BOK-060 Borettslag og sameier** – særskilt regnskap, vedlikeholdsfond og beboerfordringer.
- **BOK-061 Prosjektregnskap i hovedboken** – inntekter og kostnader samlet per prosjekt.
- **BOK-062 Attestasjon og internkontroll** – hvem har godkjent, kontrollert og bokført det enkelte bilaget.
- **BOK-063 Bilagsarkiv** – alle bilag og vedlegg lagret søkbart og tilgjengelig i oppbevaringstiden.
- **BOK-064 Søk i bilag** – søk på nummer, dato, tekst, part, beløp, prosjekt og MVA-kode.
- **BOK-065 Massebokføring** – bokføring av mange like bilag i én operasjon.
- **BOK-066 Import av bankfil** – manuell eller automatisk import av kontoutskrift i standardformat.
- **BOK-067 SIE-import og -eksport** – utveksling med årsoppgjør, revisjon og andre systemer.
- **BOK-068 Kontoplanvedlikehold** – opprette, endre og sperre kontoer uten å bryte historikken.
- **BOK-069 Dokumenterte rutiner** – systemet støtter beskrivelse av bokføringsrutiner og ansvar.
- **BOK-070 Systemdokumentasjon** – dokumentasjon av hvordan regnskapet er organisert og kontrollert.
- **BOK-071 Rapportering per avdeling** – resultat og balanse filtrert på avdeling/kostnadssted.
- **BOK-072 Rapportering per prosjekt** – lønnsomhet, påløpt og fakturert per prosjekt.
- **BOK-073 Rapportering per kunde/leverandør** – omsetning, kostnader og mellomværende per part.
- **BOK-074 Periodisert og kontantbasert visning** – se regnskapet både periodisert og kontantstrømbasert.
- **BOK-075 Låsing av enkeltbilag** – bilag kan låses etter godkjenning mens perioden er åpen.
- **BOK-076 Endringslogg per bilag** – full historikk over endringer, vedlegg og kommentarer.
- **BOK-077 Vedleggskrav** – systemet krever dokumentasjon før bilaget kan godkjennes.
- **BOK-078 Elektronisk faktura som bilag** – EHF lagres i opprinnelig format, ikke bare som PDF.
- **BOK-079 Oppbevaring i fem år** – regnskapsmateriale holdes tilgjengelig og lesbart i lovpålagt periode.
- **BOK-080 Tilgjengelighet ved avvikling** – bokførte opplysninger er tilgjengelige elektronisk i minst seks måneder etter avvikling.

### 3.4 Salg, fakturering og kundefordringer (`SAL`)

- **SAL-001 Kunderegister** – navn, organisasjonsnummer, adresse, kontaktpersoner, betalingsbetingelser og valuta.
- **SAL-002 Kredittgrense** – sperre eller varsel når kunden overskrider avtalt grense.
- **SAL-003 Kredittvurdering** – oppslag mot kredittopplysning før salg eller fakturering.
- **SAL-004 Produkt- og tjenestekatalog** – artikkelnummer, enhet, pris, MVA-kode og lagerkobling.
- **SAL-005 Prislister** – kundespesifikke priser, pris per valuta og gyldighetsperioder.
- **SAL-006 Rabattmatrise** – rabatter etter kunde, vare, antall, kampanje og sesong.
- **SAL-007 Tilbud** – opprettelse, versjonering, sending og oppfølging av tilbud.
- **SAL-008 Tilbudsgodkjenning** – kunden godkjenner digitalt, og ordre opprettes automatisk.
- **SAL-009 Ordre** – salgsordre med linjer, leveringsdato, lagerreservasjon og ordrebekreftelse.
- **SAL-010 Ordre til faktura** – hel eller delvis fakturering av ordre, med restordre og restbeløp.
- **SAL-011 Leveringsseddel og pakkseddel** – dokumentasjon av hva som er levert, før fakturering.
- **SAL-012 Enkeltfaktura** – manuell faktura med fritekst, varelinjer, MVA og betalingsbetingelser.
- **SAL-013 Samlefaktura** – flere ordrer eller prosjekter på samme faktura.
- **SAL-014 Abonnementsfaktura** – faste fakturaer etter intervall, med oppstart, pause og oppsigelse.
- **SAL-015 Fakturaplan** – delbetalinger, milepæler, a-konto og etterskuddsvis fakturering.
- **SAL-016 Forskuddsfaktura** – fakturering før levering, med avregning mot sluttfaktura.
- **SAL-017 Fakturamaler** – egne maler per kundegruppe, språk, bransje og selskap.
- **SAL-018 Fakturautseende** – logo, farger, fonter, topptekst, bunntekst og vedlegg.
- **SAL-019 Faktura på e-post** – sending som PDF med sporbar leveringsstatus.
- **SAL-020 EHF/Peppol-faktura** – sending i godkjent elektronisk format til bokføringspliktig kjøper.
- **SAL-021 eFaktura til nettbank** – sending til kundens nettbank via eFaktura-kanal.
- **SAL-022 Vipps-faktura** – sending og betaling via Vipps, med automatisk avstemming.
- **SAL-023 SMS-faktura** – sending av faktura eller betalingslenke på SMS.
- **SAL-024 Brevfaktura** – utskrift og postsending for kunder uten digital kanal.
- **SAL-025 Avtalegiro** – oppsett og trekk via AvtaleGiro med varsling.
- **SAL-026 KID-nummer** – generering av KID per faktura og automatisk matching av innbetaling.
- **SAL-027 OCR-linje** – maskinlesbar betalingsinformasjon på fakturaen.
- **SAL-028 Fakturanummerering** – ubrutt nummerserie per foretak og fakturatype.
- **SAL-029 Kreditnota** – kreditering av hel eller delvis faktura, med kobling til original.
- **SAL-030 Erstatningsfaktura** – ny faktura ved feil, med tydelig referanse til den opprinnelige.
- **SAL-031 Purring** – automatisk purring etter forfall, med gebyr og renteberegning.
- **SAL-032 Purregebyr og forsinkelsesrente** – beregning etter lovens satser og egne vilkår.
- **SAL-033 Inkasso** – overlevering til inkasso, med status og dokumentasjon.
- **SAL-034 Nedskrivning av tap** – avsetning og bokføring av konstaterte tap på kundefordringer.
- **SAL-035 Delbetaling** – registrering av flere innbetalinger mot samme faktura.
- **SAL-036 Overbetaling og avregning** – håndtering av overskudd, tilgodebeløp og kreditnota.
- **SAL-037 Innbetalingsvarsel** – varsel når betaling er mottatt, delvis mottatt eller avvist.
- **SAL-038 Automatisk bokføring av faktura** – fakturaen bokføres ved sending, med MVA og reskontro.
- **SAL-039 Automatisk bokføring av innbetaling** – innbetaling matches og bokføres uten manuelt arbeid.
- **SAL-040 Utestående fordringer** – liste over alle åpne kundefakturaer med forfall.
- **SAL-041 Aldersfordelt kundereskontro** – fordeling på forfalte intervaller og kunder.
- **SAL-042 Purrehistorikk** – hvem som er purret, når, på hvilken måte og med hvilket resultat.
- **SAL-043 Omsetningsrapport** – omsetning per kunde, produkt, selger, avdeling og periode.
- **SAL-044 Dekningsgrad per salg** – inntekt mot varekostnad og direkte kostnader.
- **SAL-045 Selger og provisjon** – kobling av salg til selger og beregning av provisjon.
- **SAL-046 Nettbutikkintegrasjon** – ordrer, lager og kunder synkroniseres med nettbutikken.
- **SAL-047 Markedsplassintegrasjon** – salg fra markedsplasser føres inn med riktig MVA og gebyr.
- **SAL-048 Kassesystem/POS** – salgstall, betalingsformer og kassedifferanse overføres til regnskapet.
- **SAL-049 Betalingsløsning** – Stripe, Vipps, Nets eller tilsvarende med automatisk avstemming.
- **SAL-050 Kundeportal** – kunden ser fakturaer, tilbud, ordrer og betalingsstatus selv.
- **SAL-051 Selvbetjent oppdatering** – kunden kan oppdatere adresse, kontaktinfo og betalingsmåte.
- **SAL-052 EHF-mottak og tolkning** – systemet tar imot og leser elektroniske fakturaer fra kunder.
- **SAL-053 Peppol-registrering** – oppslag og registrering av Peppol-ID/ELMA for kunde og selger.
- **SAL-054 Fakturahistorikk** – full historikk med versjoner, leveringsstatus og kvitteringer.
- **SAL-055 Kreditnota til EHF** – elektronisk kreditnota i samme standard som fakturaen.
- **SAL-056 Selvfakturering** – utstedelse av selvfaktura på vegne av kunde, med riktig ansvar og format.
- **SAL-057 Internfakturering** – fakturering mellom selskaper i konsern med elimineringsstøtte.
- **SAL-058 Faktura på flere språk** – engelsk og andre språk for utenlandske kunder.
- **SAL-059 Eksportfaktura** – nullsats, opprinnelsesland og dokumentasjon for eksport.
- **SAL-060 Rapportering av utestående per prosjekt** – se hva som er fakturert og hva som gjenstår.

### 3.5 Innkjøp, leverandørfaktura og betaling (`INN`)

- **INN-001 Leverandørregister** – navn, organisasjonsnummer, adresse, kontonummer, betalingsbetingelser og valuta.
- **INN-002 Leverandørkontakter** – flere kontaktpersoner, roller og kommunikasjonshistorikk.
- **INN-003 Innkjøpsordre** – bestilling med linjer, leveringsdato, pris og leveringsadresse.
- **INN-004 Bestillingsforslag** – forslag basert på lagerbeholdning, minstenivå og historisk forbruk.
- **INN-005 Varemottak** – registrering av mottatt vare mot bestilling og pakkseddel.
- **INN-006 Treveismatching** – bestilling, mottak og faktura må stemme før godkjenning.
- **INN-007 Leverandørfaktura manuelt** – registrering med bilag, MVA, prosjekt og avdeling.
- **INN-008 Leverandørfaktura via EHF** – automatisk mottak, tolkning og forslag til kontering.
- **INN-009 Leverandørfaktura via e-post** – videresending til systemets fakturaadresse.
- **INN-010 OCR på leverandørfaktura** – utlesing av fakturainformasjon og linjer.
- **INN-011 Bilagsgodkjenning** – godkjenningsflyt med attestant, beløpsgrense og delegering.
- **INN-012 Godkjenningshistorikk** – hvem godkjente, avviste eller returnerte, med kommentar og tidspunkt.
- **INN-013 Avvik i godkjenning** – varsel ved manglende bilag, feil MVA eller avvik fra bestilling.
- **INN-014 Betalingsforslag** – forslag til betaling basert på forfall, rabatt og prioritet.
- **INN-015 Betaling fra systemet** – betalingsfil eller direkte bankintegrasjon, med godkjenning.
- **INN-016 Dobbelt godkjenning av betaling** – krav om to godkjennere over beløpsgrense.
- **INN-017 Utenlandsbetaling** – SWIFT/IBAN, valutakurs, gebyr og mottakerland.
- **INN-018 Batchbetaling** – mange leverandører i én betaling med samlet kvittering.
- **INN-019 Hastbetaling** – ekspressbetaling utenom ordinær betalingskjøring.
- **INN-020 Leverandørreskontro** – åpne poster, delbetalinger, kreditnotaer og mellomværende.
- **INN-021 Kreditnota fra leverandør** – registrering og matching mot opprinnelig faktura.
- **INN-022 Purring fra leverandør** – registrering av purring og purregebyr.
- **INN-023 Innkjøpsrapport** – innkjøp per leverandør, vare, avdeling, prosjekt og periode.
- **INN-024 Leverandørytelse** – leveringstid, avvik, kvalitet og prisutvikling.
- **INN-025 Prisavvik** – sammenligning av avtalt pris, bestilt pris og fakturert pris.
- **INN-026 Innkjøpsavtaler** – avtalepriser, varighet, betingelser og oppfølging.
- **INN-027 Tilbudsforespørsel (RFQ)** – sende forespørsel, sammenligne tilbud og velge leverandør.
- **INN-028 Ansattutlegg** – ansatte registrerer utlegg med kvittering og formål.
- **INN-029 Reiseregning** – reise, diett, overnatting, transport og godtgjørelse etter statens satser.
- **INN-030 Kjøregodtgjørelse** – beregning etter statens satser, med eller uten passasjer.
- **INN-031 Kjørebok** – automatisk eller manuell kjørebok for firma- og privatkjøring.
- **INN-032 Godkjenning av utlegg** – leder godkjenner før utbetaling eller lønnskjøring.
- **INN-033 Utbetaling av utlegg** – via lønn, separat utbetaling eller kreditering.
- **INN-034 Innkjøpsforespørsel** – intern bestillingsflyt med budsjettkontroll.
- **INN-035 Leverandørkreditt** – kredittid, fakturagebyr og betalingsbetingelser.
- **INN-036 Forskuddsbetaling til leverandør** – registrering og avregning mot senere faktura.
- **INN-037 Bankgaranti og remburs** – dokumentasjon og oppfølging av sikkerhet.
- **INN-038 Klientmiddelbetaling** – betaling fra sperret klientkonto med dokumentasjon.
- **INN-039 Betalingsstatus** – sanntidsstatus for sendt, godkjent, utført og avvist betaling.
- **INN-040 Rapportering av leverandørgjeld** – aldersfordelt og per forfallsdato.

### 3.6 Bank, finans og likviditet (`BAN`)

- **BAN-001 Bankintegrasjon** – direkte kobling mot én eller flere norske banker.
- **BAN-002 Kontosaldo i sanntid** – saldo og tilgjengelig beløp hentes fra banken.
- **BAN-003 Kontoutskrift** – alle transaksjoner med dato, tekst, beløp og motpart.
- **BAN-004 Automatisk transaksjonsimport** – daglig eller etter intervall, uten manuell fil.
- **BAN-005 Manuell bankfil** – import av CSV, CAMT.053 eller annet standardformat.
- **BAN-006 Bankavstemming** – avstemming av bankkonto mot hovedbok og reskontro.
- **BAN-007 Uidentifiserte transaksjoner** – egen kø for transaksjoner som ikke er matchet.
- **BAN-008 Betalingsgodkjenning** – godkjenning i systemet før betaling sendes til bank.
- **BAN-009 Betalingsstatus** – sporbar status fra forslag til utført betaling.
- **BAN-010 Flere banker** – ulike banker og konti i samme foretak.
- **BAN-011 Valutakonto** – konto i utenlandsk valuta med kurs og omregning.
- **BAN-012 Kassekreditt** – saldo, rente og rapportering for kassekreditt.
- **BAN-013 Lån og avdrag** – låneoppsett, renter, avdrag og restgjeld.
- **BAN-014 Leasingavtaler** – betalinger, rente og forpliktelser, eventuelt IFRS 16.
- **BAN-015 Kontantstrømprognose** – forventet inn- og utbetaling per uke/måned.
- **BAN-016 Likviditetsbudsjett** – planlagt likviditet med scenario og avvik.
- **BAN-017 Rullerende prognose** – oppdatert prognose basert på faktiske tall.
- **BAN-018 Finansieringsbehov** – beregning av kapitalbehov og finansieringsgap.
- **BAN-019 Renteinntekter og -kostnader** – automatisk bokføring av renter og gebyrer.
- **BAN-020 Bankgebyr** – egne regler og konti for gebyrer per bank og transaksjonstype.
- **BAN-021 Innpåbetaling og avregning** – håndtering av betalingsanvisninger og refusjoner.
- **BAN-022 Purring og inkasso** – oppfølging av kundefordringer med bankstatus.
- **BAN-023 Factoring** – salg av fordringer med provisjon og regress.
- **BAN-024 Klientkonto** – sperret konto for klientmidler med egen rapportering.
- **BAN-025 MVA-oppgjør** – betaling og avstemming av MVA mot skattemelding.
- **BAN-026 Skattetrekk og arbeidsgiveravgift** – betaling og avstemming mot a-melding.
- **BAN-027 Pensjon og OTP** – betaling og avstemming mot pensjonsleverandør.
- **BAN-028 Feriepenger** – avsetning, utbetaling og avstemming av feriepenger.
- **BAN-029 Konsernkonto** – overføringer og mellomværender i konsern.
- **BAN-030 Likviditetsrapport** – saldo, bundne midler og fri likviditet per konto.
- **BAN-031 Bankavstemmingsrapport** – dokumentasjon av avstemmingen med dato og bruker.
- **BAN-032 Kontantbeholdning** – mynter, sedler og kontantbeholdning per kasse.

### 3.7 Lønn, HR og reise/utlegg (`LØN`)

- **LØN-001 Ansattregister** – personnummer, kontaktinfo, bankkonto, ansettelsesforhold og stilling.
- **LØN-002 Arbeidsforhold** – startdato, stillingsprosent, arbeidssted, tariffavtale og oppsigelse.
- **LØN-003 Lønnstrinn og lønnsopprykk** – historikk over lønn, tillegg og endringer.
- **LØN-004 Skattekort** – automatisk henting og oppdatering av skattekort og trekkgrunnlag.
- **LØN-005 Skattefradrag og trekk** – prosenttrekk, tabelltrekk, frikort og særfradrag.
- **LØN-006 Fagforening og trekk** – kontingenttrekk og rapportering til fagforening.
- **LØN-007 Fastlønn** – månedslønn med automatisk beregning av feriepenger og trekk.
- **LØN-008 Timelønn** – lønn basert på registrerte timer, med ulike satser.
- **LØN-009 Overtid** – beregning etter lov og tariff, med grunnlag og tillegg.
- **LØN-010 Tillegg** – kveld, natt, helg, helligdag, skift og andre tariffestede tillegg.
- **LØN-011 Bonus og provisjon** – engangsbeløp, salgsprovisjon og resultatbonus.
- **LØN-012 Feriepenger** – beregning, avsetning og utbetaling etter opptjeningsår.
- **LØN-013 Sykepenger** – beregning, refusjon og korrigering av sykepengegrunnlag.
- **LØN-014 Permisjon** – lønnet og ulønnet permisjon, foreldrepermisjon og velferdspermisjon.
- **LØN-015 Sluttlønn** – oppgjør ved fratredelse, med feriepenger og restferie.
- **LØN-016 Etterbetaling** – etterbetaling av lønn med korrekt periode og trekk.
- **LØN-017 Lønnskorreksjon** – retting av tidligere lønnskjøring med sporbarhet.
- **LØN-018 Skattetrekk** – beregning og rapportering av forskuddstrekk.
- **LØN-019 Arbeidsgiveravgift** – beregning etter sone og sats, med rapportering.
- **LØN-020 Arbeidsgiveravgiftssone** – riktig sone for virksomheten og den ansatte.
- **LØN-021 OTP og pensjon** – innskudd, prosentsats, leverandør og rapportering.
- **LØN-022 AFP og tariffestet pensjon** – beregning og rapportering for AFP-medlemmer.
- **LØN-023 FNO, hyre og lott** – særskilt lønn for sjøfolk og fiskere.
- **LØN-024 A-melding** – generering, validering og innsending til Skatteetaten.
- **LØN-025 A02-import** – import av arbeidsforhold og historikk fra tidligere lønnssystem.
- **LØN-026 Korrigert a-melding** – retting av tidligere innsendt a-melding.
- **LØN-027 Refusjon fra NAV** – sykepenger, foreldrepenger og andre refusjoner.
- **LØN-028 Lønnsslipp** – PDF/elektronisk slipp med spesifikasjon av lønn, trekk og feriepenger.
- **LØN-029 Ansattportal** – den ansatte ser lønnsslipper, skattekort, ferie og egne data.
- **LØN-030 Elektronisk signering** – signering av arbeidsavtale, lønnsslipp og reiseregning.
- **LØN-031 Timeføring for lønn** – timer overføres fra prosjekt/timeføring til lønnskjøring.
- **LØN-032 Fraværsregistrering** – sykdom, ferie, permisjon og annet fravær.
- **LØN-033 Ferie og feriepengegrunnlag** – feriedager, feriepenger og feriepengeavsetning.
- **LØN-034 Sykemelding og oppfølging** – sykmeldingsperioder, gradering og tiltak.
- **LØN-035 Reiseregning** – reise med bil, fly, tog, diett og overnatting.
- **LØN-036 Diett** – beregning etter statens satser, med eller uten overnatting.
- **LØN-037 Utlegg** – ansattes utlegg med kvittering, formål og godkjenning.
- **LØN-038 Kjørebok** – kjøring med firmabil, privatbil og passasjerer.
- **LØN-039 Lønnsjournal** – samlet oversikt per lønnskjøring med alle lønnsarter.
- **LØN-040 Arbeidsgiveravgiftsrapport** – grunnlag, sats, beløp og avstemming.
- **LØN-041 Feriepengeavsetning** – avsetning og rapport per ansatt og år.
- **LØN-042 Lønnsstatistikk** – lønn per stilling, kjønn, alder og avdeling.
- **LØN-043 Stillingsrapport** – bemanning, stillingsprosent og årsverk.
- **LØN-044 HR-dokumenter** – arbeidsavtaler, attester, vandel og personalmapper.
- **LØN-045 Personalhåndbok** – interne regler, godkjenning og versjonering.
- **LØN-046 HMS og avvik** – rapportering av hendelser, risikovurdering og tiltak.
- **LØN-047 Opplæring og kurs** – kursregister, sertifikater og påminnelser.
- **LØN-048 Vaktplan og bemanning** – planlegging av skift og ressurser.
- **LØN-049 Integrasjon med lønnsbyrå** – overlevering av grunnlag og tilbakeføring av lønn.
- **LØN-050 Personvern for ansatte** – tilgangsstyring, lagring og sletting av sensitive personopplysninger.

### 3.8 Prosjekt, tid og ressursstyring (`PRO`)

- **PRO-001 Prosjektopprettelse** – navn, kunde, prosjektleder, status og økonomisk ramme.
- **PRO-002 Prosjektkobling til kunde** – kunde, kontaktperson, adresse og faktureringsinformasjon.
- **PRO-003 Prosjektbudsjett** – budsjett per aktivitet, periode, ansatt og kostnadstype.
- **PRO-004 Aktiviteter** – arbeidspakker, faser og aktiviteter med egne budsjetter.
- **PRO-005 Milepæler** – datoer, leveranser og betingelser for fakturering.
- **PRO-006 Prosjektteam** – deltakere, roller, timepris og tilgang.
- **PRO-007 Timeføring på web** – timer per dag, prosjekt, aktivitet og kommentar.
- **PRO-008 Timeføring i mobil** – rask registrering, også uten nett, med synkronisering.
- **PRO-009 Timegodkjenning** – leder godkjenner eller returnerer timer før fakturering/lønn.
- **PRO-010 Fakturerbare og ikke-fakturerbare timer** – skille mellom kundearbeid og internt arbeid.
- **PRO-011 Overtid og tillegg i prosjekt** – timer med ulike satser og godkjenning.
- **PRO-012 Prosjektkostnader** – direkte kostnader, reise, utlegg og innkjøp på prosjekt.
- **PRO-013 Materialforbruk** – varer og materialer ført på prosjekt med lager- eller kostnadskonto.
- **PRO-014 Underleverandører** – eksterne ressurser, kostnad og viderefakturering.
- **PRO-015 Fakturagrunnlag** – automatisk samling av timer, kostnader og påslag.
- **PRO-016 Påslag og margin** – påslag per time, kostnad, prosjekt eller kunde.
- **PRO-017 Pris per rolle** – ulike timepriser for ulike roller og ansatte.
- **PRO-018 Takster og avtalt pris** – fastpris, enhetspris, regningsarbeid og takst.
- **PRO-019 Avregning** – avregning av forskudd, a-konto og sluttfaktura.
- **PRO-020 Prosjektregnskap** – inntekter, kostnader og resultat per prosjekt.
- **PRO-021 Prosjektlønnsomhet** – dekningsgrad, timefortjeneste og bidrag per prosjekt.
- **PRO-022 Budsjettavvik** – faktisk mot budsjett per linje og periode.
- **PRO-023 Prosjektprognose** – forventet sluttresultat og estimat til ferdigstillelse.
- **PRO-024 WIP og påløpte inntekter** – beregning av ufakturert arbeid og opptjent inntekt.
- **PRO-025 Ressursplanlegging** – hvem jobber når, på hvilket prosjekt og med hvilken kapasitet.
- **PRO-026 Kapasitetsplanlegging** – tilgjengelige timer mot planlagte timer.
- **PRO-027 Utnyttelsesgrad** – fakturerbar andel av arbeidstiden.
- **PRO-028 Prosjektrapporter** – status, fremdrift, økonomi og avvik for leder og kunde.
- **PRO-029 Bygg og anlegg** – prosjekt, faser, timer, materialer og underentreprenører.
- **PRO-030 Elektro og VVS** – bransjemodul med materiell, timer og serviceoppdrag.
- **PRO-031 Konsulent og rådgivning** – timer, roller, påslag og fakturering.
- **PRO-032 Landbruk** – produksjon, tilskudd og sesongbasert prosjektregnskap.
- **PRO-033 Interne prosjekter** – tid og kostnader på interne utviklings- og driftsprosjekter.
- **PRO-034 Timer til lønn** – overføring av godkjente timer til lønnsgrunnlag.
- **PRO-035 Prosjektportal** – kunden følger fremdrift, timer, dokumenter og fakturaer.
- **PRO-036 Prosjektdokumenter** – tegninger, avtaler, bilder og rapporter knyttet til prosjektet.
- **PRO-037 Milepælsfakturering** – automatisk faktura ved nådd milepæl.
- **PRO-038 Prosjektavslutning** – sluttoppgjør, lukking, erfaringsoverføring og arkivering.

### 3.9 Varelager, logistikk og produksjon (`VAR`)

- **VAR-001 Varemaster** – varenummer, navn, beskrivelse, enhet, pris og MVA-kode.
- **VAR-002 Varianter** – størrelse, farge, modell og andre egenskaper med eget varenummer.
- **VAR-003 Enheter** – stk, kg, meter, pakke og konvertering mellom enheter.
- **VAR-004 Strekkoder** – generering og skanning av strekkode/QR for vare og lokasjon.
- **VAR-005 Varebilder og dokumenter** – bilder, datablad og sikkerhetsinformasjon.
- **VAR-006 Lagerlokasjoner** – flere lager, soner, hyller og bin-lokasjoner.
- **VAR-007 Lagerbeholdning** – beholdning per vare, lokasjon og variant i sanntid.
- **VAR-008 Vareinn- og utgang** – mottak, uttak, salg, retur og intern forflytning.
- **VAR-009 Lageroverføring** – flytting mellom lokasjoner med sporbarhet.
- **VAR-010 Varetelling** – telling per lokasjon, med avvik og godkjenning.
- **VAR-011 Lagerjustering** – manuell korrigering med årsak og sporbarhet.
- **VAR-012 Restordre** – oversikt over varer som ikke kan leveres, med ny dato.
- **VAR-013 Levering** – plukking, pakking og leveringsbekreftelse.
- **VAR-014 Pakkseddel** – følgeseddel med varelinjer, antall og referanse.
- **VAR-015 Frakt og sporing** – fraktvalg, fraktbrev og sporingsnummer.
- **VAR-016 Retur** – retur av varer fra kunde, med lagerinn og kreditnota.
- **VAR-017 FIFO** – først inn, først ut, med lagverdi per parti.
- **VAR-018 Veid gjennomsnitt** – løpende gjennomsnittskost per vare.
- **VAR-019 Standardkost** – forhåndsdefinert kost med avviksanalyse.
- **VAR-020 Lagerverdi** – verdi per vare, lokasjon og regnskapskonto.
- **VAR-021 Svinn** – registrering og rapportering av svinn og kassasjon.
- **VAR-022 Ukurans** – nedskrivning av varer som ikke forventes solgt.
- **VAR-023 Kampanjer og tilbud** – midlertidige priser, pakker og rabatter.
- **VAR-024 Stykkliste (BOM)** – komponenter og mengder for et ferdigprodukt.
- **VAR-025 Arbeidsordre** – produksjonsordre med material- og timeforbruk.
- **VAR-026 Materialforbruk** – automatisk trekk av komponenter ved produksjon.
- **VAR-027 Ferdigvare** – innlegging av produserte varer på lager med kostnad.
- **VAR-028 Produksjonskostnad** – material, arbeid og indirekte kostnader per enhet.
- **VAR-029 Serienummer** – sporing av serienummer gjennom kjøp, lager og salg.
- **VAR-030 Batch og holdbarhet** – sporing av parti og utløpsdato, med FIFO/FEFO.
- **VAR-031 Lagerrapport** – beholdning, bevegelse og verdi per periode.
- **VAR-032 Dekningsanalyse** – hvor lenge beholdningen varer ved nåværende salg.
- **VAR-033 Innkjøpsbehov** – forslag basert på beholdning, salg og leveringstid.
- **VAR-034 Nettbutikklager** – synkronisering av beholdning og ordrer med nettbutikk.
- **VAR-035 POS-lager** – salg i kasse reduserer lager og bokfører varekostnad.
- **VAR-036 3PL og eksternt lager** – integrasjon mot ekstern lageroperatør.
- **VAR-037 Fraktintegrasjon** – Bring, PostNord, Posten og andre fraktleverandører.
- **VAR-038 Lager per prosjekt** – øremerket beholdning og uttak til prosjekt.
- **VAR-039 Vareuttak til eget bruk** – uttak av vare til internt bruk eller gave, med MVA.
- **VAR-040 Leverandørretur** – retur til leverandør med kreditnota og lagerutgang.

### 3.10 Rapportering, analyse og styring (`RAP`)

- **RAP-001 Resultatregnskap** – periodisert resultat med sammenligning mot budsjett og fjorår.
- **RAP-002 Balanse** – eiendeler, egenkapital og gjeld per dato.
- **RAP-003 Hovedbok** – alle posteringer per konto, med drill-down.
- **RAP-004 Saldobalanse** – saldoer per konto for valgt periode.
- **RAP-005 Reskontro** – kunde- og leverandørreskontro med åpne poster.
- **RAP-006 MVA-rapport** – MVA-grunnlag, satser, fradrag og skyldig/tilgode.
- **RAP-007 Bilagsjournal** – kronologisk journal med bilagsnummer og vedlegg.
- **RAP-008 Nøkkeltall** – omsetning, resultat, marginer og vekst.
- **RAP-009 Dekningsgrad** – dekningsbidrag i prosent av omsetning.
- **RAP-010 EBITDA og driftsresultat** – justert resultat før renter, skatt og avskrivninger.
- **RAP-011 Likviditetsgrad** – omløpsmidler mot kortsiktig gjeld.
- **RAP-012 Soliditet** – egenkapital i prosent av totalkapital.
- **RAP-013 Gjeldsgrad** – gjeld i forhold til egenkapital.
- **RAP-014 ROCE** – avkastning på sysselsatt kapital.
- **RAP-015 DSO** – gjennomsnittlig tid fra faktura til betaling.
- **RAP-016 DPO** – gjennomsnittlig tid fra leverandørfaktura til betaling.
- **RAP-017 DIO** – gjennomsnittlig lagertid.
- **RAP-018 Dashboards** – visuelle nøkkeltall og grafer per rolle og ansvar.
- **RAP-019 Driftsbudsjett** – budsjett per konto, avdeling, prosjekt og måned.
- **RAP-020 Likviditetsbudsjett** – planlagte inn- og utbetalinger per periode.
- **RAP-021 Prognose** – forventet resultat og balanse basert på faktiske tall.
- **RAP-022 Rullerende prognose** – oppdateres hver måned med nyeste data.
- **RAP-023 Sammenligning** – periode mot periode, avdeling mot avdeling og selskap mot selskap.
- **RAP-024 Drill-down** – fra nøkkeltall ned til bilag og vedlegg.
- **RAP-025 Egendefinerte rapporter** – velg kolonner, filter, gruppering og sortering.
- **RAP-026 Rapportbygger** – bygg rapporter uten utvikler, med lagring og deling.
- **RAP-027 Power BI** – direkte kobling eller eksport til Power BI.
- **RAP-028 Excel-eksport** – alle rapporter kan tas ut til Excel med formler og format.
- **RAP-029 API-rapportering** – hent data til eget analyseverktøy via API.
- **RAP-030 Konsernrapportering** – samlet rapportering med elimineringer og valutaomregning.
- **RAP-031 Segmentrapportering** – rapporter per forretningsområde, land eller kundegruppe.
- **RAP-032 Avviksvarsel** – varsel når budsjett, likviditet eller nøkkeltall avviker.
- **RAP-033 Budsjettkontroll** – sperre eller varsel ved kjøp utenfor budsjett.
- **RAP-034 KPI per rolle** – hver rolle ser de nøkkeltallene som er relevante.
- **RAP-035 Automatisk rapportutsending** – rapporter sendes på e-post/SMS etter plan.
- **RAP-036 Styre- og ledelsespakke** – ferdig rapportpakke med resultat, balanse, likviditet og kommentarer.
- **RAP-037 Revisjonsrapport** – rapport til revisor med saldoer, avstemminger og dokumentasjon.
- **RAP-038 Historisk sammenligning** – sammenlign flere år og perioder i samme visning.

### 3.11 Årsoppgjør, skatt og myndighetsrapportering (`ÅRS`)

- **ÅRS-001 Årsoppgjørsguide** – stegvis sjekkliste fra avstemming til innsending.
- **ÅRS-002 Avstemming av alle kontoer** – bank, reskontro, MVA, lønn, lager og mellomværender.
- **ÅRS-003 Periodisering ved årsslutt** – forskudd, opptjent, påløpt og avsatt.
- **ÅRS-004 Avskrivninger** – regnskapsmessige og skattemessige avskrivninger med avstemming.
- **ÅRS-005 Varelager ved årsslutt** – verdivurdering, telling og bokføring av lagerendring.
- **ÅRS-006 Pensjon og OTP** – avstemming av pensjonskostnad og innbetaling.
- **ÅRS-007 Skatteberegning** – beregning av skattekostnad og skyldig skatt.
- **ÅRS-008 Fremførbart underskudd** – sporing og bruk av underskudd over år.
- **ÅRS-009 Konsernbidrag** – beregning, dokumentasjon og bokføring.
- **ÅRS-010 Fritaksmetoden** – beregning og dokumentasjon av skattefrie utbytter.
- **ÅRS-011 Utbytte** – forslag, vedtak, utbetaling og skattetrekk.
- **ÅRS-012 Aksjekapital** – innbetaling, emisjon, kapitalnedsettelse og overkurs.
- **ÅRS-013 Aksjeeierbok** – eiere, aksjer, erverv, salg og pant.
- **ÅRS-014 Aksjonærregisteroppgave** – generering og innsending via sluttbrukersystem.
- **ÅRS-015 Skattemelding** – forhåndsutfylt skattemelding med kontroll og innsending.
- **ÅRS-016 Næringsspesifikasjon** – automatisk utfylling fra kontoplan og bilag.
- **ÅRS-017 Skattemelding for ENK** – næringsoppgave og personinntekt for enkeltpersonforetak.
- **ÅRS-018 Årsregnskap** – resultat, balanse, kontantstrøm og egenkapitaloppstilling.
- **ÅRS-019 Noter** – lovpålagte noter med beregninger og maler.
- **ÅRS-020 Styrets beretning** – mal og opplysninger om drift, risiko og hendelser.
- **ÅRS-021 Generalforsamling** – innkalling, protokoll og godkjenning av årsregnskapet.
- **ÅRS-022 Signering** – elektronisk signering av årsregnskap og skattemelding.
- **ÅRS-023 Regnskapsregisteret** – innsending av årsregnskap og kvittering.
- **ÅRS-024 Revisjon** – tilrettelegging, revisjonsspor og kommunikasjon med revisor.
- **ÅRS-025 Revisjonsberetning** – mottak, arkivering og publicering.
- **ÅRS-026 Attestasjon** – attestasjon av bærekraftsrapport eller annen lovpålagt attestasjon.
- **ÅRS-027 Bærekraftsrapportering** – ESG/CSRD-data for foretak som omfattes.
- **ÅRS-028 Stiftelser og foreninger** – årsregnskap og rapportering etter særregler.
- **ÅRS-029 Borettslag og sameier** – årsregnskap, vedlikeholdsplan og beboerrapportering.
- **ÅRS-030 NUF og utenlandsk selskap** – tilpasset rapportering og morselskapskobling.
- **ÅRS-031 ASA og børsnotert selskap** – utvidet rapportering og IFRS-støtte.
- **ÅRS-032 ANS og DA** – selskapsregnskap og deltakerrapportering.
- **ÅRS-033 Skatteoppgjør** – mottak og avstemming av skatteoppgjør og restskatt.
- **ÅRS-034 Restskatt og tilgode** – beregning, betaling og bokføring.
- **ÅRS-035 Dokumentasjon av årsoppgjøret** – alle beregninger, avstemminger og vurderinger samlet.
- **ÅRS-036 SAF-T-eksport** – eksport av hovedbok, kunder, leverandører, kontoplan og MVA-koder.
- **ÅRS-037 Frister og varsler** – påminnelser for aksjonærregister, skattemelding, generalforsamling og årsregnskap.
- **ÅRS-038 Arkivering** – årsregnskap, skattemelding og kvitteringer lagret i oppbevaringstiden.
- **ÅRS-039 Avslutning av selskap** – opphør, avvikling og sluttrapportering.
- **ÅRS-040 Virksomhetsoverdragelse** – dokumentasjon ved salg, kjøp eller fusjon.
- **ÅRS-041 Kontroll av årsregnskap** – balansekontroll, krysskontroll og sammenligning mot fjorår.
- **ÅRS-042 Revisjonsfritak** – kontroll av terskler for å kunne velge bort revisjon.

### 3.12 Merverdiavgift og avgiftsoppgjør (`MVA`)

- **MVA-001 MVA-satser** – 25 %, 15 %, 12 %, 11,11 % og 0 %, med riktig anvendelse.
- **MVA-002 MVA-koder** – egne koder koblet til sats, konto og SAF-T-standard.
- **MVA-003 MVA-kontoer** – utgående, inngående, oppgjør og justering.
- **MVA-004 MVA-melding** – automatisk utfylling fra bokføringen, med kontroll og signering.
- **MVA-005 Terminer** – to-måneders, månedlig eller årstermin etter registrering og omsetning.
- **MVA-006 Betaling av MVA** – betalingsgrunnlag, forfall og avstemming mot bank.
- **MVA-007 Inngående MVA** – fradrag for MVA på kjøp, med dokumentasjonskrav.
- **MVA-008 Utgående MVA** – beregning på salg, med riktig sats og grunnlag.
- **MVA-009 Fradragsrett** – kontroll av fradrag for ulike kostnadstyper og formål.
- **MVA-010 Blandet virksomhet** – fordeling av inngående MVA mellom avgiftspliktig og ikke-avgiftspliktig del.
- **MVA-011 Uttaksmva** – beregning ved uttak av varer og tjenester til eget bruk.
- **MVA-012 Omvendt avgiftsplikt** – kjøp av tjenester fra utlandet og bygge- og anleggsarbeid.
- **MVA-013 Byggeplass og omsetning av bygg** – særregler for bygg og anlegg.
- **MVA-014 EU-varekjøp** – innkjøp fra EU med MVA og innrapportering.
- **MVA-015 Import** – tollbehandling, importmva og fradrag.
- **MVA-016 Eksport** – nullsats og dokumentasjon av utførsel.
- **MVA-017 OSS og fjernsalg** – One Stop Shop for salg til forbrukere i EU.
- **MVA-018 Fjernlevering** – salg av varer til forbrukere i andre land.
- **MVA-019 MVA-kompensasjon** – for virksomheter med kompensasjonsrett.
- **MVA-020 Tilbakegående avgiftsoppgjør** – fradrag for MVA før registrering, inntil tre år.
- **MVA-021 Registreringsplikt** – varsel ved nær 50 000 kroner i avgiftspliktig omsetning.
- **MVA-022 MVA-avstemming** – kontroll av MVA-konto mot melding og bilag.
- **MVA-023 MVA-spesifikasjon** – spesifikasjon per kode, sats, kunde og leverandør.
- **MVA-024 SAF-T MVA-koder** – mapping mot Skatteetatens standardkoder.
- **MVA-025 MVA på e-faktura** – riktig MVA-grunnlag og -beløp i EHF/Peppol.
- **MVA-026 Nullsats og unntak** – skille mellom nullsats, fritak og omsetning utenfor loven.
- **MVA-027 Justering av inngående MVA** – justering ved endret bruk eller salg av driftsmiddel.
- **MVA-028 Utenlandske tjenester** – kjøp av skytjenester, konsulenttjenester og lisenser.
- **MVA-029 MVA-kalkulator** – beregning av MVA inklusive/eksklusive ved registrering.
- **MVA-030 MVA-rapport per periode** – grunnlag og beløp for kontroll og revisjon.

### 3.13 Automatisering, AI og datadeling (`AUT`)

- **AUT-001 OCR og IDP** – automatisk utlesing av strukturert data fra PDF, bilde og EHF.
- **AUT-002 Dokumenttolkning** – forstå fakturatype, linjer, MVA og betalingsbetingelser.
- **AUT-003 Kontoforslag** – forslag basert på historikk, leverandør og tekst.
- **AUT-004 MVA-forslag** – automatisk valg av MVA-kode og sats.
- **AUT-005 AI-assistent** – spør regnskapet i naturlig språk og få svar med kildehenvisning.
- **AUT-006 AI-bokføring** – bokfør med godkjenning, med full sporbarhet og mulighet for retting.
- **AUT-007 Regelbasert automatisering** – regler for kontering, MVA, avdeling og prosjekt.
- **AUT-008 AutoBokfør** – automatisk bokføring av gjentakende transaksjoner.
- **AUT-009 Gjentakende oppgaver** – planlagte jobber for faktura, purring, rapport og avstemming.
- **AUT-010 Duplikat- og avviksdeteksjon** – flagg for mulige duplikater, feil og mangler.
- **AUT-011 Anomalideteksjon** – varsel ved uvanlige beløp, konti eller tidspunkter.
- **AUT-012 Kontantstrømprediksjon** – forventet likviditet basert på historikk og åpne poster.
- **AUT-013 Kundeadferdsanalyse** – betalingsmønster, risiko og purrebehov.
- **AUT-014 Datavarehus** – samlet datalager for analyse på tvers av moduler.
- **AUT-015 API og webhooks** – hendelsesdrevet integrasjon med eksterne systemer.
- **AUT-016 MCP og agenttilgang** – scoped tilgang for AI-agenter, med logging og godkjenning.
- **AUT-017 Integrasjonsmarked** – ferdige koblinger mot bank, butikk, CRM, lønn og prosjekt.
- **AUT-018 Elektronisk dokumentflyt** – mottak, fordeling, godkjenning og arkivering.
- **AUT-019 e-signering** – signering av avtaler, årsoppgjør og godkjenninger.
- **AUT-020 Varsler og oppgaver** – automatisk oppgaveoppretting ved hendelser og frister.
- **AUT-021 Mobilitet** – bilde, timer, utlegg og godkjenning fra mobil.
- **AUT-022 Import av bank og kort** – transaksjoner og kortkjøp hentes automatisk.
- **AUT-023 Kortintegrasjon** – bedriftskort med kvitteringskobling og automatisk kontering.
- **AUT-024 Kvitteringsfangst** – kvittering kobles til korttransaksjon eller bilag.
- **AUT-025 Språkmodell for support** – hjelp i kontekst og svar på regnskapsspørsmål.

### 3.14 Bransje- og selskapsformspesifikke funksjoner (`BRA`)

- **BRA-001 Enkeltpersonforetak** – næringsoppgave, privatuttak, kjørebok og skattemelding.
- **BRA-002 Aksjeselskap** – aksjekapital, aksjeeierbok, utbytte, konsernbidrag og aksjonærregister.
- **BRA-003 Holdingstruktur** – morselskap, datterselskap, konsernregnskap og eliminering.
- **BRA-004 NUF** – utenlandsk selskap med norsk filial og rapportering.
- **BRA-005 ASA** – børsnotert selskap med utvidet rapportering.
- **BRA-006 ANS og DA** – deltakerlignet selskap med deltakerrapportering.
- **BRA-007 Stiftelse** – årsregnskap, formål og rapportering etter stiftelsesloven.
- **BRA-008 Forening og lag** – kontingent, medlemsregister og foreningsregnskap.
- **BRA-009 Borettslag og sameie** – beboerfordringer, vedlikeholdsfond og felleskostnader.
- **BRA-010 Bygg og anlegg** – prosjekt, faser, underentreprenører, timer og materialer.
- **BRA-011 Elektro** – serviceoppdrag, materiell, timer og dokumentasjon.
- **BRA-012 VVS** – rørlegger- og ventilasjonsarbeid med materiell og timer.
- **BRA-013 Landbruk** – produksjon, tilskudd, sesong og næringsspesifikasjon.
- **BRA-014 Fiske og sjøfart** – lott, hyre, FNO og særfradrag.
- **BRA-015 Transport og logistikk** – kjørebok, frakt, sporing og lønnsgrunnlag.
- **BRA-016 Restaurant og servering** – kasse, MVA-satser, vareforbruk og tips.
- **BRA-017 Handel og butikk** – POS, lager, strekkoder og svinn.
- **BRA-018 Nettbutikk** – ordrer, lager, frakt, retur og markedsplasser.
- **BRA-019 Konsulent og rådgivning** – timer, roller, påslag og prosjektlønnsomhet.
- **BRA-020 Eiendom og utleie** – leieforhold, kontrakter, avregning og vedlikehold.
- **BRA-021 Helse og omsorg** – pasient-/klientdata, oppgjør og personvern.
- **BRA-022 Undervisning og kurs** – kurs, deltakere, fakturering og oppfølging.
- **BRA-023 Frivillighet** – gaver, tilskudd, medlemmer og rapportering.
- **BRA-024 Offentlig sektor** – anbud, innkjøpsavtaler, MVA-kompensasjon og rapportering.
- **BRA-025 Prosjektbasert virksomhet** – WIP, milepæler, fremdrift og sluttfaktura.
- **BRA-026 Service og vedlikehold** – serviceordrer, avtaler og påminnelser.
- **BRA-027 Produksjon** – stykkliste, arbeidsordre, material og ferdigvare.
- **BRA-028 Engros** – prisavtaler, kvantumsrabatt, pall og leveringsbetingelser.
- **BRA-029 Import og eksport** – toll, opprinnelse, valuta og dokumentasjon.
- **BRA-030 Konsern og flerfirma** – felles kontoplan, konsernkonto og konsolidering.

### 3.15 Brukeropplevelse, samarbeid og support (`UX`)

- **UX-001 Onboarding** – veiledet oppstart med selskapsopplysninger, kontoplan og første bilag.
- **UX-002 Importveiviser** – stegvis migrering med validering og forhåndsvisning.
- **UX-003 Maler og sjekklister** – ferdige oppsett for selskapsform og bransje.
- **UX-004 Hjelp i kontekst** – hjelpetekst, artikler og video der brukeren står.
- **UX-005 Tooltips og feltforklaringer** – forklaring av konto, MVA-kode og felt.
- **UX-006 Opplæring og akademi** – kurs, webinarer og sertifisering.
- **UX-007 Support på chat** – sanntidshjelp i arbeidsflyten.
- **UX-008 Support på telefon og e-post** – bemannet støtte med svartidsmål.
- **UX-009 Gratis support** – inkludert i abonnementet, eventuelt med prioritet i høyere pakker.
- **UX-010 Kommentarer og @-omtaler** – diskusjon direkte på bilag, faktura og prosjekt.
- **UX-011 Oppgaver og tildeling** – delegering med status, frist og ansvarlig.
- **UX-012 Deling med regnskapsfører** – tilgang uten passorddeling og med sporbarhet.
- **UX-013 Revisor- og byråsamarbeid** – felles arbeidsflate, meldinger og oppgaveflyt.
- **UX-014 Mobilapper** – egne apper for bilag, tid, utlegg, godkjenning og lønnsslipp.
- **UX-015 Wearables** – støtte for klokke eller andre enheter der det er relevant.
- **UX-016 Tastatursnarveier** – hurtigtaster for hurtigregistrering og navigasjon.
- **UX-017 Hurtigregistrering** – bokfør med få felt og smarte standardverdier.
- **UX-018 Massehandlinger** – merk flere rader og utfør handling samlet.
- **UX-019 Globalt søk** – søk på tvers av kunder, leverandører, bilag, fakturaer og prosjekter.
- **UX-020 Personverninnstillinger** – samtykke, datadeling og eksport av egne data.
- **UX-021 Sletting og retting** – brukeren kan be om sletting der loven tillater det.
- **UX-022 Dataportabilitet** – eksport av egne data i maskinlesbart format.
- **UX-023 Tilgjengelighet** – WCAG, kontrast, skjermleser og tastaturnavigasjon.
- **UX-024 Språk** – norsk bokmål, nynorsk, engelsk og eventuelt samisk.
- **UX-025 Pakker og priser** – tydelig skille mellom hva som er inkludert og hva som koster ekstra.
- **UX-026 Modulvalg** – aktiver og deaktiver moduler uten å miste data.
- **UX-027 Bilagsgrenser** – forståelige grenser per pakke, med varsel før taket nås.
- **UX-028 Transaksjonskostnader** – kostnad per EHF, SMS, brev, KID eller betaling vises før sending.
- **UX-029 Bindingstid og oppsigelse** – vilkår, oppsigelsesfrist og tilbakebetaling.
- **UX-030 Prøveperiode** – reell test uten kredittkort der det er mulig.
- **UX-031 Brukeradministrasjon** – inviter, deaktiver og overfør brukere.
- **UX-032 Varslingsinnstillinger** – velg kanal og frekvens for hver varslingstype.
- **UX-033 Status og fremdrift** – se hva som gjenstår før årsoppgjør, MVA eller månedsavslutning.
- **UX-034 Feilhåndtering** – forståelige feilmeldinger med forslag til løsning.
- **UX-035 Endringshistorikk** – brukeren ser hva som er endret og av hvem.

### 3.16 Sikkerhet, personvern og compliance (`SIK`)

- **SIK-001 Bokføringsloven** – regnskapet føres i samsvar med grunnleggende bokføringsprinsipper.
- **SIK-002 Regnskapsloven** – årsregnskap og rapportering etter regnskapsplikt.
- **SIK-003 Merverdiavgiftsloven** – beregning, fradrag og rapportering av MVA.
- **SIK-004 Sporbarhet** – alle transaksjoner kan spores til bilag og bruker.
- **SIK-005 Fullstendighet** – alle transaksjoner skal bokføres, ingen perioder hoppes over.
- **SIK-006 Realitet** – det som bokføres skal ha skjedd og tilhøre virksomheten.
- **SIK-007 Dokumentasjon** – bilag og vedlegg oppfyller lovens krav.
- **SIK-008 Oppbevaring i fem år** – regnskapsmateriale oppbevares og er lesbart.
- **SIK-009 Oppbevaring i Norge** – materiale lagres i Norge eller etter unntak i EØS.
- **SIK-010 Elektronisk regnskapssystem** – klar for kravet om elektronisk bokføring fra 2030.
- **SIK-011 E-faktura i opprinnelig format** – elektronisk faktura arkiveres i strukturert format.
- **SIK-012 SAF-T** – systemet kan eksportere SAF-T Financial i gjeldende versjon.
- **SIK-013 Tilgangsstyring** – minste privilegium og rollebasert tilgang.
- **SIK-014 To-faktor** – 2FA for administratorer og sensitive handlinger.
- **SIK-015 Logging** – innlogging, endringer, eksport og API-kall logges.
- **SIK-016 Backup** – regelmessig sikkerhetskopi med testet gjenoppretting.
- **SIK-017 Beredskap** – plan for driftsavbrudd, datatap og gjenoppretting.
- **SIK-018 Kryptering** – data krypteres i transitt og i ro.
- **SIK-019 Databehandleravtale** – DPA med underdatabehandlere og formål.
- **SIK-020 GDPR** – behandling, lagring og sletting etter personopplysningsloven.
- **SIK-021 Personopplysninger** – egne regler for ansatte, kunder og sensitive data.
- **SIK-022 Taushetsplikt** – tilgang begrenset for regnskapsfører og ansatte.
- **SIK-023 Revisorloven** – støtte for revisjon, uavhengighet og dokumentasjon.
- **SIK-024 Revisjonsplikt** – kontroll av terskler og revisjonsfritak.
- **SIK-025 Hvitvaskingsloven** – kundekontroll og risikovurdering for regnskapsførere.
- **SIK-026 Kundekontroll** – identitetskontroll, reelle rettighetshavere og løpende oppfølging.
- **SIK-027 Regnskapsførerloven** – autorisasjon, oppdragsavtale og god regnskapsførerskikk.
- **SIK-028 Oppdragsavtale** – dokumentert ansvar, omfang og fullmakter.
- **SIK-029 Klientmidler** – sperret konto og dokumentert håndtering.
- **SIK-030 Kassasystemforskriften** – krav til kassasystem, logging og SAF-T Cash Register.
- **SIK-031 Reelle rettighetshavere** – registrering og oppdatering innen frister.
- **SIK-032 Altinn 3** – støtte for gjeldende Altinn-plattform og meldingsflyt.
- **SIK-033 Hendelseshåndtering** – rutine for sikkerhetsbrudd og varsling.
- **SIK-034 Leverandørkjedekontroll** – krav og oppfølging av underleverandører.
- **SIK-035 Testing** – regelmessig sikkerhetstesting og sårbarhetsovervåking.
- **SIK-036 Sertifiseringer** – ISO 27001, SOC 2 eller tilsvarende der det er relevant.
- **SIK-037 AI-ansvarlighet** – menneskelig godkjenning, forklarbarhet og sporbarhet for AI-forslag.
- **SIK-038 Dataminimering** – bare nødvendige personopplysninger samles inn.
- **SIK-039 Leverandørvurdering** – dokumentert vurdering av skyløsning og datalagring.
- **SIK-040 Avviksrapportering** – intern varsling og læring etter feil.

---

## 4. Systemmatrise på modulnivå

Matrisen er en forenklet oversikt på modulnivå, ikke en full funksjonssammenligning. Den er basert på leverandørenes offentlige produkt- og hjelpesider, oppdatert november 2026.

**Tegnforklaring:** `●` innebygd/standard · `○` tilleggsmodul eller høyere pakke · `◐` begrenset eller ikke fullverdig · `–` ikke dokumentert · `?` ikke bekreftet

| Funksjon | FIK | CON | TRI | POG | VEA | 24S | DUE | XLE | NXT | D365 |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Regnskap og bokføring | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| NS 4102-kontoplan | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| MVA-melding | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| Årsoppgjør/skattemelding | ○ | ○ | ○ | ◐ | ○ | ● | ● | ● | ● | ● |
| Faktura PDF/e-post | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| EHF/Peppol | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| eFaktura/KID | ○ | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| Purring og inkasso | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| Abonnementsfaktura | ● | ◐ | ● | ● | ● | ● | ◐ | ● | ● | ● |
| Tilbud og ordre | ● | ● | ● | ● | ● | ● | ◐ | ● | ● | ● |
| Bankintegrasjon | ○ | ○ | ● | ● | ● | ● | ● | ● | ● | ● |
| Automatisk bankavstemming | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| Bilagsinnboks/OCR | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| EHF-mottak | ◐ | ◐ | ● | ● | ◐ | ● | ● | ● | ● | ● |
| Leverandørgodkjenning | – | – | ● | ● | – | ● | ● | ● | ● | ● |
| Betaling fra systemet | ◐ | ◐ | ● | ● | ● | ● | ● | ● | ● | ● |
| Lønn og a-melding | ○ | ○ | ● | ● | – | ● | ● | ● | ● | ● |
| Timeføring | ○ | – | ● | ● | ○ | ● | ● | ● | ● | ● |
| Prosjektregnskap | ○ | ○ | ● | ● | ○ | ● | ● | ● | ● | ● |
| Reiseregning og utlegg | ○ | – | ● | ● | – | ● | ● | ● | ● | ● |
| Kjørebok | ○ | – | ○ | ● | – | ● | ◐ | ● | ● | ● |
| Varelager | ◐ | ◐ | ● | ◐ | ○ | ● | ● | ● | ● | ● |
| Lagerlokasjoner | – | – | ● | – | – | ● | ● | ● | ● | ● |
| Produksjon | – | – | – | – | – | ○ | ◐ | – | ● | ● |
| CRM | – | – | ● | ◐ | – | ● | ◐ | ◐ | ● | ● |
| API | ○ | ◐ | ● | ● | ● | ● | ◐ | ● | ● | ● |
| SAF-T | ◐ | ◐ | ● | ● | ● | ● | ● | ● | ● | ● |
| Konsern/flerfirma | – | – | ◐ | ◐ | – | ◐ | ● | ● | ● | ● |
| Budsjett | – | – | ● | ● | ○ | ● | ● | ● | ● | ● |
| Dashboards/BI | ● | ● | ● | ● | ○ | ● | ● | ● | ● | ● |
| Anleggsregister | ● | – | ● | ● | ● | ● | ● | ● | ● | ● |
| Byrå/klientoverbygg | ○ | ◐ | ● | ● | ● | ● | ● | ● | ● | ● |
| Mobilapp | ● | ● | ● | ● | ● | ● | ● | ● | ● | ● |
| Bransjemoduler | – | – | ● | ● | – | ◐ | ◐ | ● | ● | ● |
| AI/automatisering | ● | ● | ● | ● | ◐ | ● | ◐ | ◐ | ● | ● |

### 4.1 Typiske forskjeller som ikke vises i matrisen

- **Fiken** er enklest å komme i gang med, men bank, lønn, prosjekt, tid og KID er tilleggsmoduler. API er eget tillegg.
- **Conta** har sterkt fokus på mobil, AI-kontering og enkel bokføring; prosjekt og KID er knyttet til Smart-pakken.
- **Tripletex** er modulbasert og bredest blant småbedriftssystemene, med lager, CRM og bransjemoduler.
- **PowerOffice Go** har sterkest godkjennings- og betalingsflyt, og mange integrasjoner; årsoppgjør er delvis integrert/under utbygging.
- **Visma eAccounting** har avviklet lønn og er avhengig av bankintegrasjon i høyere pakke; årsoppgjør er egen modul.
- **24SevenOffice/Finago, Duett, Uni Economy/Unimicro, Xledger, Visma NXT og Dynamics** er først og fremst for mellomstore og større virksomheter, med dybde i lager, produksjon, konsern og rapportering.
- **Pris- og pakkestruktur** påvirker funksjonstilgang mer enn produktnavnet: bilagstak, transaksjonskostnader, bindingstid og modulvalg varierer.

---

## 5. Regelverk og nye krav som påvirker regnskapsprogrammet

### 5.1 Grunnreglene

Et norsk regnskapsprogram må bygge på disse rettskildene:

- **Bokføringsloven** (LOV-2004-11-19-73) – bokføringsplikt, grunnleggende prinsipper, dokumentasjon, oppbevaring og krav til regnskapssystem.
- **Bokføringsforskriften** (FOR-2004-12-01-1558) – detaljkravene til bilag, salgsdokument, nummerering, oppbevaring, SAF-T og elektronisk faktura.
- **Regnskapsloven** (LOV-1998-07-17-56) og **regnskapsforskriften** – årsregnskap, noter, konsern og bærekraft.
- **Merverdiavgiftsloven** (LOV-2009-06-19-58), **mva-forskriften** og **skatteforvaltningsloven/forskriften** – MVA, terminer, mva-melding og frister.
- **Aksjeloven** – aksjekapital, aksjeeierbok, generalforsamling, utbytte og årsregnskap.
- **Regnskapsførerloven** og **revisorloven** – autorisasjon, oppdragsavtale, taushetsplikt, uavhengighet og revisjon.
- **Personopplysningsloven/GDPR** – behandling av kunde-, ansatt- og personopplysninger.
- **Kassasystemforskriften** – krav til kassasystem, digital signatur og SAF-T Cash Register.
- **Hvitvaskingsloven** – kundekontroll og risikovurdering for regnskapsførere.
- **NRS 8** (god regnskapsskikk for små foretak) og **NBS 6** (bokføringsstandard for små virksomheter).

De grunnleggende bokføringsprinsippene i bokføringsloven § 4 er:

1. **Dokumentasjon** – alle transaksjoner skal ha tilstrekkelig dokumentasjon.
2. **Fullstendighet** – alle transaksjoner skal bokføres.
3. **Realitet** – det som bokføres skal ha skjedd og tilhøre virksomheten.
4. **Sporbarhet** – alle posteringer skal kunne følges til bilag og opprinnelig dokumentasjon.
5. **Ajourhold** – regnskapet skal være oppdatert og føres i riktig periode.
6. **Oppbevaring** – regnskapsmateriale skal oppbevares i fem år etter regnskapsårets slutt.
7. **System** – regnskapet skal føres i et ordnet og lukket system.

Krav til systemet i praksis:

- ubrutte nummerserier for bilag og salgsdokumenter;
- ingen sletting av bokførte bilag, bare retting med sporbarhet;
- tilgangsstyring, endringslogg og sikkerhetskopi;
- spesifikasjoner som saldobalanse, hovedbok, bilagsjournal, reskontro, MVA-spesifikasjon og SAF-T;
- oppbevaring i Norge (eller EØS etter nærmere vilkår), i lesbar og tilgjengelig form;
- e-faktura skal oppbevares i sitt opprinnelige, strukturerte format, ikke bare som PDF.

### 5.2 Tidslinje for nye krav

| Dato | Krav | Konsekvens for systemet |
|---|---|---|
| **1. juli 2026** | Deler av endringsloven om pliktig digital bokføring og e-fakturering trer i kraft | Systemet må forberede e-faktura, strukturert arkivering og digital bokføring |
| **Juni 2026** | Aksjonærregisteroppgaven leveres bare gjennom sluttbrukersystem | Systemet må kunne generere og sende oppgaven; Altinn og papir er ikke lenger mulig |
| **1. januar 2027** | Plikt til å utstede e-faktura til bokføringspliktige kjøpere som kan motta den (ELMA/Peppol) | EHF/Peppol BIS 3.0+ må være standard; PDF er ikke tilstrekkelig |
| **1. januar 2027** | Unntaket fra elektronisk tilgjengelighet for virksomheter under 5 mill. kr oppheves | Også små virksomheter må ha bokførte opplysninger elektronisk tilgjengelig |
| **1. januar 2027** | SAF-T Financial 1.40 blir eneste gyldige format | Eksport må støtte 1.40; 1.30 kan brukes ut 2026 |
| **1. januar 2028** | Kjøpers organisasjonsnummer skal alltid angis i salgsdokumentet | Fakturafeltet må være påkrevd for bokføringspliktige kunder |
| **1. januar 2028** | Salgsdokumentet skal alltid oversendes bokføringspliktig kjøper | Kan ikke lenger avtales bort |
| **1. januar 2030** | Plikt til å motta e-faktura fra bokføringspliktige | Systemet må ha mottak, tolkning og arkivering i strukturert format |
| **1. januar 2030** | Bokføring skal skje i et elektronisk regnskapssystem | Regneark og manuell bokføring utfases for bokføringspliktige |
| **Regnskapsåret 2027** | NBS 6-grensen for regnskapsføring i regneark reduseres fra 600 til 200 bilag | Systemet bør fange opp kunder som nærmer seg grensen |

### 5.3 E-faktura i detalj

- **Plikt til å utstede** fra 1. januar 2027 ved salg av varer og tjenester til andre bokføringspliktige.
- **Plikt til å motta** først fra 1. januar 2030. Fram til da gjelder utstedelsesplikten i praksis bare når kjøperen er registrert i ELMA/Peppol.
- **Godkjente standarder:** EHF Fakturering, Peppol BIS Billing, EHF Selvfakturering og Peppol BIS Self-Billing, alle i versjon 3.0 eller nyere.
- **Overgangsordning til 2030:** andre elektronisk strukturerte formater, som EDIFACT og E2B, kan brukes etter avtale med kjøper.
- **PDF er ikke e-faktura.** En PDF sendt på e-post oppfyller ikke kravet når kjøperen kan motta e-faktura.
- **Unntak:** bokføringspliktige med omsetning inntil 50 000 kroner, konkursbo og nærmere angitte finans- og forsikringsvirksomheter, på vilkår i bokføringsforskriften.
- **Fakturainnhold:** selger og kjøper med organisasjonsnummer, dato, fakturanummer, beskrivelse, leveringstid/sted, MVA-grunnlag og -beløp, forfallsdato og betalingsinformasjon.
- **Arkivering:** e-fakturaen skal lagres i opprinnelig format, ikke konverteres til PDF eller bilde.
- **ELMA/Peppol:** systemet bør slå opp kjøpers Peppol-ID automatisk og varsle når kjøperen ikke kan motta e-faktura.

### 5.4 SAF-T

- Kravet følger av **bokføringsforskriften § 7-8**. Filen leveres ikke periodisk, men på forespørsel fra Skatteetaten, typisk ved kontroll.
- **Versjoner:** 1.20 kan brukes for 2024 og tidligere, 1.30 for 2025–2026, og **1.40 er eneste gyldige format fra 1. januar 2027**.
- **Innhold:** header, masterfiles (kontoplan, kunder, leverandører, MVA-koder) og general ledger entries (hovedbokstransaksjoner).
- **Kontomapping:** fra 2025 er mapping mot næringsspesifikasjonen eneste tillatte alternativ; 2- og 4-sifret standard er ikke lenger nok.
- **MVA-koder:** interne MVA-koder må kobles mot Skatteetatens standard MVA-koder.
- **Unntak:** virksomheter med omsetning under 5 mill. kr var unntatt til og med 2026; unntaket oppheves fra 2027. Enkeltpersonforetak uten ansatte og med omsetning under 50 000 kr er fortsatt unntatt etter nærmere vilkår.
- **Kassasystem:** egne krav etter kassasystemforskriften og SAF-T Cash Register.

### 5.5 MVA og avgift

**Satser i 2026:**

| Sats | Gjelder |
|---|---|
| 25 % | Alminnelig sats for de fleste varer og tjenester |
| 15 % | Næringsmidler, vann og avløp |
| 12 % | Persontransport, overnatting, kringkasting, kino, idrett og fornøyelser |
| 11,11 % | Viltlevende marine ressurser (råfisk) |
| 0 % | Blant annet bøker, aviser, eksport og nye elbiler under beløpsgrensen |

- **Registrering:** normalt når avgiftspliktig omsetning overstiger 50 000 kroner i løpet av 12 måneder.
- **Terminer:** annenhver måned, med frist én måned og ti dager etter terminen. Virksomheter under 1 mill. kr kan søke om årstermin.
- **Mva-melding:** erstattet den gamle omsetningsoppgaven fra 2022, og leveres via Altinn med signering.
- **Fradrag:** inngående MVA på kjøp som brukes i avgiftspliktig virksomhet; blandet virksomhet krever fordeling.
- **Særregler:** uttaksmva, omvendt avgiftsplikt, bygge- og anleggsarbeid, EU-varekjøp, import/eksport, OSS og fjernlevering.
- **MVA-koder:** må være koblet til riktig konto, sats og SAF-T-standard.
- **Avstemming:** MVA-konto, mva-melding og bilag må stemme før innsending.

**MVA-frister 2026:** 10. april, 10. juni, 31. august, 12. oktober (10. oktober er lørdag), 10. desember, og 10. februar 2027 for siste termin.

### 5.6 Lønn og a-melding

- **A-melding** leveres innen den 5. i måneden etter lønnsutbetalingen, med forskyvning til neste virkedag ved helg/helligdag.
- **A02-import** brukes ved overgang fra annet lønnssystem.
- **Skattekort** hentes fra Skatteetaten; systemet må håndtere tabelltrekk, prosenttrekk og frikort.
- **Arbeidsgiveravgift** beregnes etter sone og sats; sone 1, 1a, 2, 3, 4 og 4a har ulike satser.
- **OTP** beregnes med minst 2 % av lønn mellom 1 og 12 G, i tillegg til eventuell tariffestet ordning.
- **Feriepenger** beregnes etter opptjeningsår, normalt 10,2 % (4 uker), 12 % (5 uker) og 12,5 % for ansatte over 60 år.
- **Refusjoner** fra NAV, sykepenger og foreldrepenger må kunne kobles til lønnskjøringen.
- **FNO, hyre og lott** gjelder sjøfolk og fiskere, med egne lønnsarter og rapportering.
- **Lønnsslipp** skal være tilgjengelig for den ansatte, og a-meldingen skal kunne korrigeres i ettertid.

### 5.7 Årsoppgjør og frister (kalenderår)

| Oppgave | Frist |
|---|---|
| Aksjonærregisteroppgaven | 31. januar (1. februar 2027 fordi 31. januar er søndag) |
| MVA-melding for november–desember | 10. februar året etter |
| Skattemelding for ENK og selskaper | 31. mai |
| Søknad om utsatt skattemelding | Innen ordinær frist; innvilget frist er typisk 30. juni |
| Ordinær generalforsamling | Innen 30. juni |
| Årsregnskap til Regnskapsregisteret | Innen 31. juli, og senest én måned etter godkjenning |
| Restskatt | Forfaller tre uker etter skatteoppgjøret |

- **Forsinkelsesgebyr** for årsregnskapet løper i inntil 26 uker og kan bli 52 rettsgebyr (69 940 kroner i 2026).
- **Revisjonsfritak** for AS: driftsinntekter under 7 mill. kr, balansesum under 27 mill. kr og maks 10 årsverk.
- **Aksjonærregisteroppgaven** skal fra juni 2026 leveres gjennom et sluttbrukersystem, ikke via Altinn eller papir.
- **Bærekraft:** Prop. 106 L (2025–2026) foreslår vesentlige forenklinger i regnskapslovens bærekraftsregler som følge av Omnibus I-direktivet, med en snevrere krets av rapporteringspliktige (salgsinntekter over 5 mrd. kr og over 1 000 ansatte) og unntak for regnskapsåret 2026 for enkelte foretak. Dette påvirker først og fremst store virksomheter, men systemene må kunne levere ESG-data på sikt.

### 5.8 Regnskapsfører, byrå og klientmidler

- **Regnskapsførerloven** krever autorisasjon, oppdragsavtale og god regnskapsførerskikk.
- **Hvitvaskingsloven** krever kundekontroll, identitetskontroll, kjennskap til reelle rettighetshavere og løpende oppfølging.
- **Klientmidler** skal holdes på sperret konto, skilles fra byråets egne midler og dokumenteres.
- **Taushetsplikt** og tilgangsstyring må være dokumentert, også ved bruk av underleverandører.
- **Revisjon** krever tilgang til regnskap, bilag, avstemminger og revisjonsspor uten å endre data.
- **Byråoverbygg** må kunne gi lese- og skrivetilgang per klient, med oppgaveflyt og tidsregistrering.

### 5.9 Andre endringer og watch-items

- **Altinn 2 → Altinn 3:** alle meldinger må etter hvert gå mot Altinn 3; systemet må følge Skatteetatens migrering.
- **Digital bokføring fra 2030:** kravet om elektronisk regnskapssystem gjør regneark uegnet for bokføringspliktige.
- **AI Act (EU):** kan få betydning for AI-funksjoner som kontoforslag, kredittvurdering og automatisert beslutningstaking; menneskelig godkjenning og forklarbarhet blir viktig.
- **NIS2 (EU):** kan bli relevant for regnskaps- og rådgivningsvirksomhet som leverandør til samfunnskritiske sektorer.
- **ViDA (EU):** EUs «VAT in the Digital Age»-pakke kan påvirke grensesnitt og rapportering for grenseoverskridende handel; Norge er ikke EU-medlem, men EØS-relevans må vurderes.
- **CSRD/ESG:** bærekraftsrapportering for store foretak, med datainnsamling fra verdikjeden.
- **Reelle rettighetshavere:** registrering og oppdatering innen 14 dager etter endring, med dagbøter ved manglende oppfyllelse.
- **E-signering:** forventes i økende grad for årsoppgjør, avtaler og godkjenninger.
- **Åpne API-er og MCP:** AI-agenter og integrasjonsplattformer blir en del av økosystemet; tilgang må være scoped, logget og godkjent.

---

## 6. Hva dette betyr for `Gratis_Regnskap`

Katalogen er bevisst bredere enn det et første versjon av et gratis regnskapsprogram bør bygge. En fornuftig prioritering:

### P0 – må være på plass før lansering

- Kontoplan (NS 4102), manuell bilagsføring, bilagsinnboks, vedlegg og ubrytelig bilagsnummer.
- Kunde- og leverandørreskontro, faktura med PDF/e-post, EHF/Peppol, kreditnota og purring.
- Bankimport og bankavstemming, MVA-koder, mva-melding og MVA-avstemming.
- Hovedbok, saldobalanse, resultat, balanse, bilagsjournal og reskontrorapporter.
- Roller, tilgangsstyring, revisjonsspor, periodelås og sikkerhetskopi.
- SAF-T-eksport og arkivering av e-faktura i opprinnelig format.
- Årsoppgjør for ENK og AS, skattemelding og aksjonærregisteroppgave.

### P1 – bør komme tidlig

- Lønn og a-melding, reiseregning/utlegg og kjørebok.
- Prosjekt, timeføring og prosjektregnskap.
- Abonnementsfaktura, tilbud/ordre og KID/eFaktura.
- Anleggsregister og avskrivninger, varelager og enkel lagerstyring.
- Budsjett, dashboards og nøkkeltall.
- API, webhooks og import/eksport til Excel/CSV/SIE-4.
- Byråtilgang og klientoverbygg.

### P2 – senere / avhengig av målgruppe

- Konsern, flerfirma og eliminering.
- Produksjon, lagerlokasjoner, strekkoder og 3PL.
- Bransjemoduler for bygg, elektro, VVS, landbruk og restaurant.
- CRM, kundeportal og avansert BI/Power BI.
- AI-assistent, prediksjon og automatisert bokføring.
- Bærekraftsrapportering og avansert revisjonsstøtte.

### Kritiske krav som ikke kan utsettes

1. **E-faktura fra 2027** – mangler dette, blir systemet uegnet for salg til næringslivet.
2. **SAF-T 1.40 fra 2027** – mangler dette, oppfyller ikke systemet bokføringsforskriften.
3. **Elektronisk regnskapssystem fra 2030** – hele arkitekturen må være elektronisk og sporbar.
4. **Aksjonærregisteroppgave via sluttbrukersystem** – kreves allerede fra juni 2026.
5. **Oppbevaring og arkivering** – bilag, e-faktura og årsregnskap må være tilgjengelig i fem år.
6. **Sikkerhet og personvern** – tilgangsstyring, logging, kryptering og databehandleravtale er grunnleggende tillitskrav.

---

## 7. Kilder

Leverandørenes egne sider og hjelpesentre:

- Fiken: <https://fiken.no/> og <https://hjelp.fiken.no/>
- Conta: <https://conta.no/regnskap> og <https://conta.no/hjelp/>
- Tripletex: <https://www.tripletex.no/> og <https://hjelp.tripletex.no/>
- PowerOffice Go: <https://www.poweroffice.no/> og <https://hjelpesenter.poweroffice.no/>
- Visma eAccounting: <https://www.eaccounting.no/funksjoner>
- 24SevenOffice/Finago: <https://24sevenoffice.com/no/produkter/regnskapsprogram>
- Duett: <https://duett.no/>
- Xledger: <https://xledger.com/no/>
- Visma Business NXT: <https://www.vismasoftware.no/erp/business-nxt>
- Microsoft Dynamics 365 Business Central: <https://www.microsoft.com/nb-no/dynamics-365/products/business-central>

Regelverk og myndigheter:

- Skatteetaten – forskrifter om digital bokføring og e-fakturering: <https://www.skatteetaten.no/rettskilder/type/uttalelser/uttalelser/forskrifter-til-lovendringer-om-digital-bokforing-og-e-fakturering/>
- Skatteetaten – plikt til å sende e-faktura fra 2027: <https://www.skatteetaten.no/bedrift-og-organisasjon/starte-og-drive/rutiner-regnskap-og-kassasystem/pliktig-efaktura/>
- Skatteetaten – SAF-T Regnskap: <https://www.skatteetaten.no/nn/bedrift-og-organisasjon/starte-og-drive/rutiner-regnskap-og-kassasystem/saf-t-regnskap/dokumentasjon/>
- Lovdata – forskrift om endring i bokføringsforskriften (FOR-2026-09-29-1933): <https://lovdata.no/dokument/SF/forskrift/2026-09-29-1933>
- Lovdata – endringslov om pliktig digital bokføring og e-fakturering: <https://lovdata.no/dokument/LTI/lov/2026-06-19-39>
- Regjeringen – Prop. 106 L (2025–2026) om forenklinger i regnskapsloven: <https://www.regjeringen.no/no/dokumenter/prop.-106-l-20252026/id3166344>
- Regnskap Norge og Revisorforeningen – faglige oppdateringer: <https://www.revisorforeningen.no/>
- Skatteetaten – mva-melding og terminer: <https://www.skatteetaten.no/bedrift-og-organisasjon/mva/>

> Sjekk alltid lovdata.no og skatteetaten.no for gjeldende versjon. Frister og satser fastsettes årlig, og overgangsregler kan endres.

<!-- END -->
