# MVP-kravspesifikasjon for Gratis_Regnskap

**Status:** utkast per 11. november 2026
**Basis:** [FUNKSJONSKART.md](FUNKSJONSKART.md), særlig P0-listen i kapittel 6.
**Målgruppe for dokumentet:** produkt, utvikling, design, testing og juridisk/compliance.

---

## 1. Formål

Dette dokumentet gjør P0-funksjonene fra funksjonskartet om til en prioritert og testbar MVP-kravspesifikasjon. Målet er at en utvikler, tester eller produktansvarlig skal kunne:

- se nøyaktig hva som må være på plass før lansering;
- vite hva som er launch-blocker og hva som kan vente;
- teste hvert krav mot konkrete akseptansekriterier;
- spore hvert krav tilbake til funksjonskartets ID-er.

Dokumentet er en kravspesifikasjon, ikke en teknisk arkitektur eller implementasjonsplan. Teknologivalg, datamodell og API-design kommer i egne dokumenter.

---

## 2. MVP-definisjon

MVP-en skal gjøre det mulig for et norsk enkeltpersonforetak eller aksjeselskap å:

1. opprette foretaket og komme i gang med riktig kontoplan og MVA-oppsett;
2. bokføre bilag med dokumentasjon, ubrytelig nummerering og fullt revisjonsspor;
3. følge opp kunder og leverandører med reskontro og fakturering;
4. avstemme banken og levere korrekt MVA;
5. hente ut lovpålagte rapporter og eksportere SAF-T;
6. avslutte året med årsregnskap, skattemelding og aksjonærregisteroppgave;
7. gjøre alt dette på en sikker, sporbar og personvernvennlig måte.

MVP-en er **ikke** et fullt ERP-system. Lønn, prosjekt, varelager, produksjon, CRM og avansert BI er bevisst utenfor.

### 2.1 Primære brukere

| Bruker | Typisk behov |
|---|---|
| Eier av ENK | Enkel bokføring, MVA, skattemelding og oversikt |
| Daglig leder i lite AS | Fakturering, bilag, bank, MVA og årsoppgjør |
| Regnskapsfører | Tilgang til klientens regnskap, kontroll, rapporter og eksport |
| Revisor | Lese- og revisjonstilgang uten å kunne endre data |

### 2.2 Antakelser for MVP

- Norsk regnskapsrett og norsk kontoplan (NS 4102) er standard.
- Kun NOK i MVP. Utenlandsk valuta er P1.
- Kun ENK og AS i MVP. NUF, ASA, ANS/DA, stiftelse og forening er P2.
- Ingen lønn, prosjekt, varelager eller produksjon i MVP.
- Ingen KID, eFaktura eller abonnementsfaktura i MVP; dette er P1.
- Nettskybasert webapplikasjon med responsivt grensesnitt. Native mobilapp er P1.
- EHF/Peppol og Altinn 3 bygges som egne adaptere der det er lovlig; sertifisert partner kan brukes for transport inntil sertifisering er på plass. PSD2 bruker lisensiert AISP-partner, med CAMT.053/CSV som fallback.
- MVP-en skal kunne brukes av en regnskapsfører på vegne av en klient, med sporbar tilgang.

---

## 3. Prioriteringsmodell

| Prioritet | Betydning | Konsekvens |
|---|---|---|
| **P0-A** | Kjerneflyt for privat beta | Må virke før første eksterne bruker slipper inn |
| **P0-B** | Launch-blockere for offentlig lansering | Må virke før markedsføring og betalte kunder |
| **P1** | Viktig, men ikke launch-blocker | Planlegges tidlig, kan lanseres etter MVP |
| **P2** | Senere / segmentavhengig | Ikke del av MVP |

P0-A og P0-B utgjør til sammen MVP-en. Skillet er laget for å kunne teste kjerneflyten tidlig uten å vente på tyngre integrasjoner som Altinn 3 og EHF-access point.

### 3.1 P0-A – kjerneflyt

1. Foretaksoppsett og kontoplan
2. Brukere, roller og tilgang
3. Bilag og bokføring
4. Bilagsinnboks og dokumentasjon
5. Kunde- og leverandørreskontro
6. Salgsfakturering med PDF/e-post
7. Bankimport og bankavstemming
8. MVA-beregning og MVA-avstemming
9. Rapporter og regnskapsoversikt

### 3.2 P0-B – launch-blockere

10. EHF/Peppol-utsending og arkivering i opprinnelig format
11. MVA-melding og innsending via Altinn 3
12. SAF-T 1.40-eksport
13. Årsoppgjør, skattemelding og aksjonærregisteroppgave
14. Sikkerhet, drift, personvern og releasekriterier

### 3.3 P1 og P2 i korte trekk

| Prioritet | Innhold |
|---|---|
| **P1** | Lønn og a-melding, reiseregning/utlegg, kjørebok, prosjekt og timeføring, abonnementsfaktura, tilbud/ordre, KID/eFaktura, anleggsregister, enkelt varelager, budsjett, dashboards, API/webhooks, byråoverbygg, import fra Excel/CSV/SIE-4 |
| **P2** | Konsern og flerfirma, produksjon, lagerlokasjoner, strekkoder, 3PL, bransjemoduler, CRM, kundeportal, Power BI, AI-assistent, bærekraftsrapportering, avansert revisjonsstøtte |

---

## 4. Kravoversikt

| ID | Krav | Prioritet | Avhengigheter | FUNKSJONSKART-referanse |
|---|---|---|---|---|
| MVP-01 | Foretaksoppsett og kontoplan | P0-A | – | OPP-001–006, OPP-019 |
| MVP-02 | Brukere, roller og tilgang | P0-A | MVP-01 | GRU-009–013, SIK-013–015 |
| MVP-03 | Bilag og bokføring | P0-A | MVP-01, MVP-02 | BOK-001–004, 011–014, 037–041, 046–051 |
| MVP-04 | Bilagsinnboks og dokumentasjon | P0-A | MVP-03 | BOK-005–010, 063–064, 077–078 |
| MVP-05 | Kunde- og leverandørreskontro | P0-A | MVP-01 | BOK-015–017, SAL-001–003, INN-001–002, 020–021 |
| MVP-06 | Salgsfakturering med PDF/e-post | P0-A | MVP-03, MVP-05 | SAL-012–018, 028–034, 038, 040, 054 |
| MVP-07 | Bankimport og bankavstemming | P0-A | MVP-03 | BAN-001–008, BOK-018–019 |
| MVP-08 | MVA-beregning og MVA-avstemming | P0-A | MVP-03 | MVA-001–008, 022–026, 030 |
| MVP-09 | Rapporter og regnskapsoversikt | P0-A | MVP-03 | BOK-046–054, RAP-001–007, 024, 028 |
| MVP-10 | EHF/Peppol og original arkivering | P0-B | MVP-06 | SAL-020, 028–029, 052–053, BOK-078, SIK-011 |
| MVP-11 | MVA-melding og Altinn 3 | P0-B | MVP-08 | MVA-004–006, 022–024, SIK-032 |
| MVP-12 | SAF-T 1.40 | P0-B | MVP-03, MVP-09 | ÅRS-036, SIK-012 |
| MVP-13 | Årsoppgjør, skatt og aksjonærregister | P0-B | MVP-09, MVP-11 | ÅRS-001–023, 033–037 |
| MVP-14 | Sikkerhet, drift og personvern | P0-B | MVP-01–MVP-13 | SIK-013–040, GRU-026–029 |
| MVP-15 | Onboarding og minimum migrering | P0-B | MVP-01 | OPP-019–024, UX-001–003 |

### 4.1 Slik leses akseptansekriteriene

Hvert krav har:

- **Krav:** hva systemet skal gjøre.
- **Akseptansekriterier:** konkrete, observerbare og testbare punkter.
- **Testbevis:** hva som skal dokumenteres i testen.

Akseptansekriteriene er skrevet som «skal»-utsagn. Der det er relevant, er de formulert som Gitt/Når/Så. Et krav er ikke ferdig før alle tilhørende akseptansekriterier er bestått i et testmiljø med realistiske data.

---

## 5. P0-A – kjerneflyt

### MVP-01 Foretaksoppsett og kontoplan

**Krav:** En ny bruker skal kunne opprette et ENK eller AS, få en gyldig NS 4102-kontoplan, sette opp MVA og legge inn åpningsbalanse uten manuell hjelp.

**Akseptansekriterier:**

- **AC-01.1 Opprette foretak:** Gitt en innlogget bruker, når brukeren velger ENK eller AS og oppgir navn, organisasjonsnummer, adresse og regnskapsår, så opprettes foretaket med status «aktiv» og vises i dashboardet. Ugyldig organisasjonsnummer avvises med en forståelig feilmelding, og samme organisasjonsnummer kan ikke opprettes to ganger.
- **AC-01.2 Kontoplan:** Et nytt foretak får NS 4102-kontoplanen automatisk. Brukeren kan legge til og endre kontoer med kontonummer, navn, kontotype og MVA-kode. Kontonummer er unikt, og en konto med posteringer kan ikke slettes.
- **AC-01.3 MVA-oppsett:** Brukeren kan velge MVA-plikt, terminlengde og standard MVA-kode. Systemet bruker valgt sats på nye bilag og viser en advarsel dersom MVA-plikt er valgt uten at MVA-koder er konfigurert.
- **AC-01.4 Åpningsbalanse:** Brukeren kan registrere saldoer per konto og importere dem fra CSV. Systemet viser sum debet, sum kredit og differanse, og lagring av åpningsbalanse krever at debet og kredit er like store.
- **AC-01.5 Bankkonto:** Brukeren kan registrere minst én bankkonto med kontonummer, navn og valuta NOK. Kontoen kan velges i bankavstemmingen.
- **AC-01.6 Klar-til-bokføring:** Dashboardet viser en sjekkliste med kontoplan, bankkonto, MVA og åpningsbalanse. Første bilag kan først posteres når kontoplan og regnskapsår finnes; manglende punkter vises med lenke til oppsettet.
- **AC-01.7 Sporbarhet:** Alle endringer i foretaksoppsett, kontoplan og åpningsbalanse logges med bruker, tidspunkt og før/etter-verdi.

**Testbevis:** Skjermbilde av opprettet ENK og AS, kontoplan med minst 20 kontoer, balansert åpningsbalanse, og logg som viser en kontoplanendring.

### MVP-02 Brukere, roller og tilgang

**Krav:** Systemet skal ha rollebasert tilgang med minste privilegium, to-faktor for administratorer og full sporbarhet på tilgangsendringer.

**Akseptansekriterier:**

- **AC-02.1 Invitasjon:** Administrator kan invitere bruker på e-post og velge rollen administrator, regnskapsfører eller leser. Invitasjonen er gyldig i 72 timer, og brukeren vises som «ventende» til den er akseptert.
- **AC-02.2 Minste privilegium:** En leser kan se og eksportere rapporter, men får «ikke tilgang» ved forsøk på å opprette, endre eller postere bilag. En regnskapsfører kan bokføre, men ikke administrere brukere eller slette foretaket.
- **AC-02.3 To-faktor:** Administratorer må aktivere to-faktor før første innlogging i produksjon. Systemet tilbyr recovery-koder, og 2FA kan ikke slås av uten ny bekreftelse.
- **AC-02.4 Økt:** En inaktiv økt logges ut etter 30 minutter, og utlogging ugyldiggjør økten umiddelbart. En utløpt økt gir 401 og sender brukeren til innlogging.
- **AC-02.5 Roller:** Endring av rolle krever administratorrettighet og logges med hvem, når, hvilken rolle og hvilket foretak.
- **AC-02.6 Deaktivering:** Administrator kan deaktivere en bruker. Brukeren mister tilgang umiddelbart, men historiske handlinger og revisjonsspor beholdes.
- **AC-02.7 Klienttilgang:** En regnskapsfører kan gis tilgang til én klient uten å få tilgang til andre klienter. Forsøk på å åpne en annen klients data gir 403 og logges.
- **AC-02.8 Innloggingsvern:** Etter fem feilede innloggingsforsøk sperres kontoen i 15 minutter, og hendelsen logges.

**Testbevis:** Testmatrise for alle tre roller, 2FA-oppsett, utløpt økt, deaktivert bruker og avvist kryssklienttilgang.

### MVP-03 Bilag og bokføring

**Krav:** Systemet skal kunne bokføre manuelle bilag med korrekt debet/kredit, MVA, dokumentasjon, ubrytelig nummerering og revisjonsspor.

**Akseptansekriterier:**

- **AC-03.1 Manuelt bilag:** Brukeren kan registrere dato, beskrivelse og minst to linjer med konto, debet/kredit og MVA-kode. Systemet beregner sum og viser differanse.
- **AC-03.2 Balansekrav:** Et bilag med ulik sum debet og kredit kan lagres som kladd, men ikke posteres. Feilmeldingen viser differansen.
- **AC-03.3 Nummerering:** Posterte bilag får et løpenummer per regnskapsår uten hull. Kladder bruker ikke nummer. To samtidige posteringer kan ikke få samme nummer.
- **AC-03.4 Uforanderlighet:** Et postert bilag kan ikke redigeres eller slettes. Rettelse skjer med tilbakeføring eller korrigeringsbilag, og originalbilaget blir liggende.
- **AC-03.5 Dokumentasjon:** Et bilag kan bare posteres med vedlegg, eller med valget «ingen ekstern dokumentasjon» og en skriftlig begrunnelse. Valget og begrunnelsen logges og vises i bilagsjournalen.
- **AC-03.6 MVA-beregning:** Systemet beregner MVA ut fra valgt kode og sats, posterer MVA på riktig konto og viser grunnlag, sats og beløp på bilaget.
- **AC-03.7 Periode:** Et bilag kan bare posteres i en åpen periode. Forsøk i låst periode avvises med melding om hvilken periode som er låst.
- **AC-03.8 Revisjonsspor:** Opprettelse, endring av kladd, postering, tilbakeføring og sletting av kladd logges med bruker, tidspunkt og før/etter-verdi.
- **AC-03.9 Søk:** Brukeren kan søke bilag på nummer, dato, tekst, beløp og konto, og få treff i løpet av to sekunder for 10 000 bilag.

**Testbevis:** Postert bilag med vedlegg, avvist ubalansert bilag, nummerserie uten hull, låst periode, tilbakeføring og full revisjonslogg.

### MVP-04 Bilagsinnboks og dokumentasjon

**Krav:** Systemet skal ta imot bilag via opplasting og e-post, tolke nøkkelfelt, oppdage duplikater og knytte originalen til riktig bilag.

**Akseptansekriterier:**

- **AC-04.1 Opplasting:** Brukeren kan laste opp PDF, JPG og PNG opptil 20 MB. Filen vises i innboksen med status «ny», og originalfilen lagres uendret.
- **AC-04.2 E-post:** Hvert foretak har en unik innboksadresse. En e-post med vedlegg oppretter et innboks-element innen to minutter, og avsender vises. Ukjent avsender flagges, men slettes ikke.
- **AC-04.3 OCR:** Systemet foreslår dato, beløp, MVA, organisasjonsnummer og fakturanummer. Feltene er redigerbare, og lav konfidens markeres tydelig.
- **AC-04.4 Duplikat:** Ved samme organisasjonsnummer, fakturanummer og beløp vises en duplikatadvarsel. Brukeren kan overstyre med begrunnelse, og overstyringen logges.
- **AC-04.5 Kobling:** Et innboks-element kan knyttes til et bilag. Vedlegg, filnavn, sjekksum og opplastingsdato vises på bilaget.
- **AC-04.6 Status:** Innboksen har statusene ny, under behandling, bokført og avvist, med filter på hver status.
- **AC-04.7 Arkiv:** Alle filer kan åpnes og lastes ned i minst fem år, også etter at bilaget er postert.

**Testbevis:** Opplastet PDF, e-post med vedlegg, OCR-felt, duplikatvarsel, kobling til bilag og nedlasting av originalfil.

### MVP-05 Kunde- og leverandørreskontro

**Krav:** Systemet skal holde separat kunde- og leverandørreskontro som alltid stemmer med hovedboken.

**Akseptansekriterier:**

- **AC-05.1 Parter:** Brukeren kan opprette og endre kunde og leverandør med navn, organisasjonsnummer, adresse, e-post og betalingsbetingelser. Ugyldig organisasjonsnummer avvises.
- **AC-05.2 Åpne poster:** En postert kundefaktura gir en åpen kundepost, og en postert leverandørfaktura gir en åpen leverandørpost. Poster viser beløp, forfall, utestående og valuta NOK.
- **AC-05.3 Delbetaling:** En innbetaling kan matches helt eller delvis mot en faktura. Restbeløpet blir stående som åpen post.
- **AC-05.4 Kreditnota:** En kreditnota reduserer åpen post og MVA, kan ikke overstige originalbeløpet, og refererer til originalfakturaen.
- **AC-05.5 Aldersfordeling:** Rapporten viser 0–30, 31–60, 61–90 og over 90 dager, med sum per kunde og per alderstrinn.
- **AC-05.6 Avstemming:** Systemet viser sum kundereskontro og sum leverandørreskontro mot tilhørende hovedbokskontoer. Differansen skal være null før periodelås.
- **AC-05.7 Sletting:** En part med posteringer kan ikke slettes, men kan deaktiveres. Deaktiverte parter vises ikke i nye bilag, men beholdes i historikken.
- **AC-05.8 Leverandørfaktura:** Brukeren kan registrere leverandørfaktura med dato, forfall, kostnadskonto, MVA og vedlegg, og postere den til leverandørreskontroen.

**Testbevis:** Kunde- og leverandørfaktura, delbetaling, kreditnota, aldersfordeling og avstemming mot hovedbok med null differanse.

### MVP-06 Salgsfakturering med PDF/e-post

**Krav:** Systemet skal kunne lage, sende og bokføre salgsfakturaer med korrekt innhold, nummerering og oppfølging.

**Akseptansekriterier:**

- **AC-06.1 Faktura:** Brukeren kan opprette en faktura med kunde, fakturadato, forfallsdato, minst én varelinje, antall, pris og MVA-kode. Systemet beregner linjesum, MVA og totalbeløp.
- **AC-06.2 Nummerering:** Hver faktura får et løpenummer per regnskapsår uten hull. Kreditnotaer har egen serie, og nummer tildeles først ved sending.
- **AC-06.3 Innhold:** PDF-en inneholder selger, kjøper, organisasjonsnumre, fakturadato, fakturanummer, beskrivelse, MVA-grunnlag og -beløp, forfallsdato og bankkontonummer.
- **AC-06.4 Sending:** Brukeren kan sende fakturaen på e-post med PDF som vedlegg. Status vises som sendt eller feilet, og mislykket sending kan prøves på nytt uten å lage nytt fakturanummer.
- **AC-06.5 Bokføring:** En sendt faktura bokføres automatisk mot kundefordring, salgsinntekt og utgående MVA. En kladd bokføres ikke.
- **AC-06.6 Kreditnota:** En kreditnota refererer til originalfakturaen, reverserer MVA og reduserer kundefordringen. Den kan ikke overstige originalbeløpet.
- **AC-06.7 Purring:** Brukeren kan sende purring manuelt eller planlegge den etter forfall. Purregebyr og forsinkelsesrente er konfigurerbart, og purringen logges på fakturaen.
- **AC-06.8 Organisasjonsnummer:** Ved salg til bokføringspliktig kunde er kjøpers organisasjonsnummer påkrevd. Mangler det, kan fakturaen ikke sendes.
- **AC-06.9 Revisjonsspor:** Opprettelse, sending, bokføring, kreditnota og purring logges med bruker og tidspunkt.

**Testbevis:** Sendt PDF-faktura, e-poststatus, automatisk bokføring, kreditnota, purring og avvist faktura uten kjøpers organisasjonsnummer.

### MVP-07 Bankimport og bankavstemming

**Krav:** Systemet skal importere banktransaksjoner, matche dem mot bilag og reskontro, og dokumentere avstemmingen.

**Akseptansekriterier:**

- **AC-07.1 Import:** Brukeren kan importere CAMT.053 og CSV for en valgt bankkonto. Importen viser antall transaksjoner, periode og eventuelle feil, og samme fil kan ikke importeres to ganger uten advarsel.
- **AC-07.2 Automatisk matching:** Systemet foreslår match på beløp, dato og referanse. Forslag med høy sikkerhet kan godkjennes enkeltvis eller i bulk.
- **AC-07.3 Manuell matching:** Brukeren kan matche en transaksjon mot bilag, kundefaktura eller leverandørfaktura, også delvis. Umatchede transaksjoner havner i egen kø.
- **AC-07.4 Bankregler:** Brukeren kan lage regler for gjentakende transaksjoner, for eksempel gebyrer, renter og overføringer. Regelen foreslår konto og MVA-kode.
- **AC-07.5 Avstemming:** Systemet viser kontoutskriftens saldo, bokført saldo og differanse. Avstemmingen kan låses med bruker og tidspunkt når differansen er null.
- **AC-07.6 Uidentifisert:** Transaksjoner som ikke er matchet, vises i egen kø med beløp, dato, tekst og mulighet for å opprette bilag direkte.
- **AC-07.7 Revisjonsspor:** Import, matching, regelbruk og låsing av avstemming logges.

**Testbevis:** Importert CAMT.053, automatisk og manuell match, delvis match, bankregel, låst avstemming med null differanse og uidentifisert kø.

### MVP-08 MVA-beregning og MVA-avstemming

**Krav:** Systemet skal beregne, bokføre og avstemme MVA for alle relevante satser og koder.

**Akseptansekriterier:**

- **AC-08.1 Satser:** Systemet støtter 25 %, 15 %, 12 %, 11,11 % og 0 %, og hver kode er koblet til riktig konto og SAF-T-kode.
- **AC-08.2 Bilag:** Når en MVA-kode er valgt, beregnes MVA automatisk. Mangler MVA-kode på en linje som krever det, vises feil og bilaget kan ikke posteres.
- **AC-08.3 MVA-rapport:** Rapporten viser grunnlag, utgående MVA, inngående MVA og å betale/til gode per termin, med drill-down til bilag.
- **AC-08.4 Avstemming:** Systemet sammenligner MVA-kontoen med MVA-rapporten og viser differanse. Differansen må være forklart eller null før MVA-melding kan sendes.
- **AC-08.5 Utkast:** Brukeren kan lagre et MVA-utkast, åpne det igjen og se hvilke bilag som inngår. Utkastet er låst for endring når det er sendt.
- **AC-08.6 Korrigering:** Feil i tidligere termin kan rettes med korrigeringsbilag, og korrigeringen vises separat i rapporten.
- **AC-08.7 Revisjonsspor:** Endringer i MVA-koder, MVA-utkast og innsending logges.

**Testbevis:** Bilag med alle satser, MVA-rapport, avstemming mot konto, lagret utkast og korrigeringsbilag.

### MVP-09 Rapporter og regnskapsoversikt

**Krav:** Systemet skal levere de lovpålagte og vanligste regnskapsrapportene med filtrering, drill-down og eksport.

**Akseptansekriterier:**

- **AC-09.1 Rapporter:** Systemet har saldobalanse, hovedbok, resultatregnskap, balanse, bilagsjournal, kundereskontro, leverandørreskontro, aldersfordeling og MVA-rapport.
- **AC-09.2 Filtrering:** Alle rapporter kan filtreres på regnskapsår, periode, konto og part. Datointervallet er inkluderende i begge ender.
- **AC-09.3 Drill-down:** Et tall i resultat, balanse eller saldobalanse kan åpnes til hovedbok og videre til bilag og vedlegg.
- **AC-09.4 Konsistens:** Sum debet er lik sum kredit i hovedboken, og balansen går i null. Resultatregnskapet stemmer med endring i egenkapitalen for perioden.
- **AC-09.5 Eksport:** Hver rapport kan eksporteres til CSV og PDF. Eksporten inneholder samme tall og kolonner som skjermvisningen.
- **AC-09.6 Ytelse:** En saldobalanse for 10 000 bilag vises innen fem sekunder, og eksporten fullføres innen 30 sekunder.
- **AC-09.7 Tilgang:** Leser kan se og eksportere rapporter, men ikke endre bilag eller rapportgrunnlag.

**Testbevis:** Alle rapporter med testdata, drill-down til bilag, CSV/PDF-eksport, balansekontroll og ytelsesmåling.

---

## 6. P0-B – launch-blockere

### MVP-10 EHF/Peppol og original arkivering

**Krav:** Systemet skal utstede, sende og arkivere elektroniske fakturaer i godkjent format til bokføringspliktige kjøpere som kan motta dem.

**Akseptansekriterier:**

- **AC-10.1 Format:** Systemet genererer EHF Fakturering eller Peppol BIS Billing 3.0 for salgsfakturaer til bokføringspliktige kjøpere. XML-en valideres mot gjeldende XSD og forretningsregler før sending.
- **AC-10.2 Kjøperoppslag:** Systemet slår opp kjøper i ELMA/Peppol. Er kjøper registrert, tilbys EHF som standardkanal. Er kjøper ikke registrert, kan fakturaen sendes som PDF, og systemet forklarer hvorfor.
- **AC-10.3 Påkrevde felt:** Kjøpers organisasjonsnummer, fakturanummer, dato, MVA-grunnlag, MVA-beløp, valuta, betalingsbetingelser og bankkontoopplysninger er påkrevd og valideres før sending.
- **AC-10.4 Sending:** Fakturaen sendes via godkjent access point. Status vises som sendt, levert, avvist eller feilet, og en feilet sending kan prøves på nytt uten å lage nytt fakturanummer.
- **AC-10.5 Original arkivering:** Den opprinnelige XML-filen lagres byte-identisk med sjekksum, sammen med kvittering for sending. Den kan lastes ned i minst fem år og er ikke konvertert til PDF eller bilde.
- **AC-10.6 Kreditnota:** Kreditnota kan sendes i samme elektroniske format, refererer til originalfakturaen og valideres på samme måte.
- **AC-10.7 Feilhåndtering:** Valideringsfeil vises med feltnavn og regel. En faktura med valideringsfeil kan ikke sendes delvis eller arkiveres som sendt.
- **AC-10.8 Revisjonsspor:** Generering, validering, sending, mottak av kvittering og nedlasting logges med bruker og tidspunkt.

**Testbevis:** Valid EHF XML for B2B-faktura og kreditnota, ELMA-oppslag for Peppol-registrert og ikke-registrert kjøper, sendt testfaktura, arkivert original med sjekksum og feilet validering.

### MVP-11 MVA-melding og Altinn 3

**Krav:** Systemet skal generere, validere, signere og sende mva-melding for riktig termin via Altinn 3, og lagre kvitteringen.

**Akseptansekriterier:**

- **AC-11.1 Grunnlag:** Mva-meldingen bygges fra et låst MVA-utkast for valgt termin, med grunnlag, utgående MVA, inngående MVA og å betale/til gode.
- **AC-11.2 Påkrevde felt:** Alle påkrevde felt for terminen er utfylt, og summer stemmer med MVA-rapporten og MVA-kontoen.
- **AC-11.3 Validering:** Innsending blokkeres dersom det er uforklarte differanser, manglende organisasjonsnummer eller ugyldige koder. Feilene vises med konkret felt og beløp.
- **AC-11.4 Signering:** Brukeren kan signere med BankID/Altinn slik Skatteetaten krever. Signeringen er knyttet til riktig foretak, termin og innsending.
- **AC-11.5 Innsending:** Meldingen sendes til Altinn 3, og systemet lagrer kvittering med tidspunkt, status og referanse. Gjentatt innsending av samme melding er idempotent.
- **AC-11.6 Status:** Brukeren ser om meldingen er sendt, mottatt, avvist eller feilet, og kan laste ned kvittering og innsendt innhold.
- **AC-11.7 Korreksjon:** En sendt melding kan ikke endres. Korreksjon skjer i ny melding eller korrigeringsbilag, med tydelig referanse til originalen.
- **AC-11.8 Revisjonsspor:** Generering, validering, signering, innsending og kvittering logges.

**Testbevis:** Mva-melding for testtermin, blokkert innsending ved differanse, signert testinnsending, kvittering og korrigert melding.

### MVP-12 SAF-T 1.40

**Krav:** Systemet skal eksportere regnskapsdata i SAF-T Financial versjon 1.40 for valgt periode, i et format som validerer mot Skatteetatens skjema.

**Akseptansekriterier:**

- **AC-12.1 Format:** Eksporten bruker SAF-T Financial 1.40 og inneholder header, masterfiles og general ledger entries.
- **AC-12.2 Innhold:** Filen inneholder kontoplan, kunder, leverandører, MVA-koder og alle hovedbokstransaksjoner i perioden.
- **AC-12.3 Mapping:** Hver konto er mappet til næringsspesifikasjonen, og hver MVA-kode er mappet til Skatteetatens standardkode. Manglende mapping gir en eksplisitt feilliste.
- **AC-12.4 Validering:** Filen validerer mot gjeldende XSD og Skatteetatens forretningsregler før den gjøres tilgjengelig for nedlasting.
- **AC-12.5 Konsistens:** Sum debet og kredit i filen stemmer med hovedboken, og saldoer per konto stemmer med saldobalansen.
- **AC-12.6 Ytelse:** Eksport for 10 000 bilag fullføres innen 60 sekunder og gir en fil som kan lastes ned på nytt uten å endre innholdet.
- **AC-12.7 Tilgang:** Eksport krever regnskapsfører- eller administratorrolle, og handlingen logges med bruker, periode og tidspunkt.

**Testbevis:** Validert SAF-T 1.40-fil, mappingrapport, avvik ved manglende mapping, saldokontroll og ny nedlasting med samme sjekksum.

### MVP-13 Årsoppgjør, skattemelding og aksjonærregister

**Krav:** Systemet skal støtte årsoppgjør for ENK og AS, generere årsregnskap, skattemelding med næringsspesifikasjon og aksjonærregisteroppgave, og sende det som skal sendes via Altinn 3 eller sluttbrukersystem.

**Akseptansekriterier:**

- **AC-13.1 Årsoppgjørsliste:** Systemet viser en sjekkliste med periodelås, MVA levert, reskontro avstemt, bank avstemt, varelager, avskrivninger, pensjon og skatt. Punkter som ikke er relevante, kan markeres som «ikke aktuelt» med begrunnelse.
- **AC-13.2 Avslutning:** Brukeren kan postere avslutningsbilag for avskrivninger, periodisering, skatt og disponering av resultat. Årets resultat overføres til egenkapitalen, og balansen går i null.
- **AC-13.3 Årsregnskap:** Systemet genererer resultatregnskap, balanse, kontantstrøm og egenkapitaloppstilling for ENK eller AS, med grunnleggende noter. PDF-en er lesbar og tallene stemmer med hovedboken.
- **AC-13.4 Skattemelding:** Systemet genererer skattemelding med næringsspesifikasjon for ENK eller AS, med alle påkrevde felt og validering før innsending.
- **AC-13.5 Aksjonærregister:** For AS genererer systemet aksjonærregisteroppgave med aksjeeiere, aksjer, erverv, salg og utbytte. Oppgaven kan sendes via sluttbrukersystem.
- **AC-13.6 Innsending:** Skattemelding og årsregnskap kan signeres og sendes via Altinn 3. Kvittering, tidspunkt og status lagres og kan lastes ned.
- **AC-13.7 ENK og AS:** Systemet håndterer forskjellene mellom ENK og AS, blant annet næringsoppgave, personinntekt, aksjekapital, utbytte og aksjonærregister.
- **AC-13.8 Arkivering:** Årsregnskap, skattemelding, aksjonærregisteroppgave og kvitteringer arkiveres i minst fem år og kan lastes ned av autoriserte brukere.
- **AC-13.9 Revisjonsspor:** Beregninger, endringer, signering og innsending logges med bruker og tidspunkt.

**Testbevis:** Fullført årsoppgjør for én ENK og én AS med testdata, balansert årsregnskap, validert skattemelding, aksjonærregisteroppgave, signert testinnsending og arkiverte kvitteringer.

### MVP-14 Sikkerhet, drift og personvern

**Krav:** Systemet skal beskytte regnskapsdata med sterk tilgangskontroll, kryptering, sikkerhetskopi, hendelseshåndtering og dokumentert personvern.

**Akseptansekriterier:**

- **AC-14.1 Kryptering:** All trafikk bruker TLS 1.2 eller nyere, og data lagres kryptert med AES-256 eller tilsvarende. Nøkler roteres og lagres separat fra data.
- **AC-14.2 Sikkerhetskopi:** Data sikkerhetskopieres daglig. Gjenoppretting er testet kvartalsvis, med RPO på maksimalt 24 timer og RTO på maksimalt 4 timer.
- **AC-14.3 Isolasjon:** En kunde kan ikke lese eller endre en annen kundes data, heller ikke via direkte URL, API eller ID-manipulasjon. Testen dokumenterer 403/404 for alle forsøk.
- **AC-14.4 Revisjonslogg:** Revisjonsloggen er uforanderlig, kan ikke slettes av bruker og oppbevares i minst fem år. Administratorhandlinger, eksport og innlogging logges.
- **AC-14.5 Databehandleravtale:** Det finnes en signerbar DPA med formål, varighet, underdatabehandlere og sletting. Listen over underdatabehandlere er tilgjengelig for kunden.
- **AC-14.6 Lagringssted:** Regnskapsdata og sikkerhetskopi lagres i Norge eller EØS, og overføring til tredjeland skjer bare med gyldig grunnlag og dokumentasjon.
- **AC-14.7 GDPR-rettigheter:** Kunden kan eksportere egne data og be om sletting. Forespørsel besvares innen 30 dager, og lovpålagt oppbevaring dokumenteres som unntak.
- **AC-14.8 Tilgangsreview:** Alle brukere og roller gjennomgås minst hvert kvartal. Ubrukte kontoer deaktiveres, og gjennomgangen dokumenteres.
- **AC-14.9 Sårbarheter:** Avhengigheter skannes ved hver utrulling. Ved lansering finnes ingen kjente kritiske eller høye sårbarheter, og en ekstern penetrasjonstest er gjennomført.
- **AC-14.10 Hendelser:** Det finnes en hendelsesplan med ansvar, kontaktpunkter og varsling. Brudd på personopplysningssikkerheten varsles innen 72 timer der GDPR krever det.
- **AC-14.11 Tilgjengelighet:** Tjenesten har en månedlig tilgjengelighet på minst 99,5 %, med statussside, overvåking og varsling ved avvik.
- **AC-14.12 Applikasjonssikkerhet:** OWASP Top 10 er gjennomgått, innlogging har hastighetsbegrensning, og feilmeldinger viser ikke stack traces eller sensitive data.
- **AC-14.13 Endringshåndtering:** Hver utrulling er versjonert, kan rulles tilbake og krever godkjent test. Produksjonsdata brukes ikke i test uten godkjenning og anonymisering.
- **AC-14.14 Dokumentasjon:** Personvernerklæring, sikkerhetsdokumentasjon og brukervilkår er publisert og versjonert før lansering.

**Testbevis:** Krypteringskonfigurasjon, gjenopprettingstest, isolasjonstest mellom to kunder, revisjonslogg, DPA, tilgangsreview, penetrasjonstest og hendelsesøvelse.

### MVP-15 Onboarding og minimum migrering

**Krav:** En ny bruker skal kunne komme i gang uten konsulenthjelp, og en eksisterende virksomhet skal kunne flytte inn kontoplan, parter og åpningsbalanse fra CSV.

**Akseptansekriterier:**

- **AC-15.1 Onboarding:** En veiviser guider gjennom foretak, kontoplan, bank, MVA og åpningsbalanse. Fremdrift lagres, og brukeren kan fortsette senere.
- **AC-15.2 CSV-maler:** Systemet tilbyr nedlastbare maler for kontoplan, kunder, leverandører og åpningsbalanse, med feltbeskrivelse og eksempelrad.
- **AC-15.3 Import:** Import av 1 000 rader fullføres innen 60 sekunder. Hver rad valideres, og feil vises med radnummer, felt og årsak.
- **AC-15.4 Delvis import:** Systemet importerer ikke delvis uten at brukeren bekrefter. Ved avbrudd kan hele importen rulles tilbake.
- **AC-15.5 Åpningsbalanse:** Importert åpningsbalanse må balansere før den kan aktiveres. Differansen vises med beløp og konto.
- **AC-15.6 Hjelp:** Hvert steg har konteksthjelp og en lenke til relevant dokumentasjon. Feilmeldinger forklarer hva brukeren skal gjøre.
- **AC-15.7 Sporbarhet:** Import, rollback og aktivering av åpningsbalanse logges med bruker, filnavn, sjekksum og tidspunkt.

**Testbevis:** Gjennomført onboarding fra tom konto, CSV-import med feil, vellykket import, rollback og aktivert åpningsbalanse.

---

## 7. Ikke-funksjonelle krav (NFR)

| ID | Krav | Akseptansekriterium |
|---|---|---|
| NFR-01 | Ytelse | 95 % av sidesvar er under 2 sekunder ved 100 samtidige brukere. Rapport for 10 000 bilag vises innen 5 sekunder. |
| NFR-02 | Tilgjengelighet | Månedlig oppetid på minst 99,5 %, målt fra ekstern overvåking. Planlagt vedlikehold varsles minst 48 timer i forveien. |
| NFR-03 | Skalerbarhet | Systemet håndterer 1 000 foretak, 100 samtidige brukere og 100 000 bilag uten at NFR-01 brytes. |
| NFR-04 | Sikkerhet | OWASP ASVS nivå 2 som mål. Ingen kritiske eller høye funn ved lansering. |
| NFR-05 | Personvern | GDPR-krav, dataminimering, DPA og dokumentert behandlingsprotokoll. |
| NFR-06 | Tilgjengelighet | WCAG 2.1 AA for kjerneflyten: pålogging, bilag, faktura, rapporter og innstillinger. |
| NFR-07 | Nettlesere | Siste to hovedversjoner av Chrome, Edge, Firefox og Safari. |
| NFR-08 | Språk og format | Norsk bokmål som standard, engelsk som valg. Dato DD.MM.ÅÅÅÅ, beløp i NOK med norsk tusenskille. |
| NFR-09 | Revisjonsspor | Alle endringer logges i minst fem år, med bruker, tidspunkt, objekt og før/etter-verdi. |
| NFR-10 | Backup og DR | RPO 24 timer og RTO 4 timer. Gjenoppretting testes kvartalsvis. |
| NFR-11 | Overvåking | Logger, metrikker og alarmer for feilrate, responstid, kø og sikkerhetshendelser. |
| NFR-12 | Feilhåndtering | Brukervennlig melding, korrelasjons-ID og ingen sensitive data i logg eller skjerm. |
| NFR-13 | Dataportabilitet | Full eksport av regnskap, bilag og vedlegg i CSV/JSON/PDF innen 30 dager etter forespørsel. |
| NFR-14 | Dokumentasjon | Brukerveiledning, oppstartsguide, DPA, sikkerhetsdokumentasjon og endringslogg er tilgjengelig. |
| NFR-15 | Support | Kritiske feil besvares innen 4 timer i arbeidstid, andre henvendelser innen én virkedag. |
| NFR-16 | Regelverksoppdatering | Endringer i satser, skjemaer og krav vurderes og implementeres innen 30 dager etter at de er publisert. |

---

## 8. Releasekriterier for MVP

MVP-en kan lanseres når alle punktene under er oppfylt og dokumentert:

1. **Alle P0-A og P0-B akseptansekriterier er bestått** i testmiljø med realistiske data.
2. **UAT er gjennomført** med minst fem pilotkunder: to ENK og tre AS, over minst én full MVA-termin. Pilotkundene har signert aksept.
3. **Ingen åpne P0-feil.** P1-feil er dokumentert med workaround og plan.
4. **Sikkerhet:** penetrasjonstest uten kritiske eller høye funn, tilgangsreview gjennomført, DPA og personvern klar.
5. **Compliance:** EHF-faktura er validert, mva-melding er testet mot Altinn 3, SAF-T 1.40 validerer, og årsoppgjør er testet for både ENK og AS.
6. **Drift:** backup og gjenoppretting er testet, overvåking og alarmer er på, og statussside er klar.
7. **Ytelse og tilgjengelighet:** NFR-01 til NFR-03 er målt og bestått i lasttest.
8. **Tilgjengelighet:** WCAG 2.1 AA er kontrollert for kjerneflyten.
9. **Dokumentasjon og support:** brukerveiledning, oppstartsguide, hjelpesenter og supportrutine er på plass.
10. **Juridisk gjennomgang:** fakturainnhold, MVA, årsregnskap og personvern er gjennomgått av fagperson.
11. **Go/no-go:** produkt, utvikling, sikkerhet, support og juridisk har godkjent lansering skriftlig.

---

## 9. P1 og P2 – hva som bevisst er utenfor MVP

### 9.1 P1 – bør komme tidlig etter lansering

| Krav | Begrunnelse | Avhengighet |
|---|---|---|
| Lønn og a-melding | Mange kunder forventer det, men det er et eget fagområde med høg risiko | Egen lønnsmodul og Altinn 3 |
| Reiseregning og utlegg | Naturlig forlengelse av bilagsflyten | Lønn eller separat utbetaling |
| Kjørebok | Ofte etterspurt av ENK og ansatte | Bilag og kjøretøyregister |
| Prosjekt og timeføring | Viktig for konsulenter og håndverkere | Faktura og rapporter |
| Abonnementsfaktura | Gjentakende inntekt | Fakturaplan |
| Tilbud og ordre | Salgsflyt før faktura | Kunde og produkt |
| KID og eFaktura | Vanlig betalingsmåte i Norge | Bankintegrasjon |
| Anleggsregister | Automatiske avskrivninger | Årsoppgjør |
| Enkelt varelager | For handel og håndverk | Bilag og rapporter |
| Budsjett og dashboards | Styring for større kunder | Rapporter |
| API og webhooks | Integrasjoner og økosystem | Stabil datamodell |
| Byråoverbygg | Salg til regnskapsførere | Roller og klienttilgang |
| Mobilapp | Bildefangst og godkjenning | Responsiv web først |
| Flerfirma | Kunder med flere selskaper | Konsern og roller |
| Utenlandsk valuta | Internasjonale kunder | Kurs og omregning |

### 9.2 P2 – senere eller segmentavhengig

- Konsern og eliminering, flerfirma og konsernkonto.
- Produksjon, stykkliste, arbeidsordre og ferdigvare.
- Lagerlokasjoner, strekkoder, batch/serienummer og 3PL.
- Bransjemoduler for bygg, elektro, VVS, landbruk, restaurant og helse.
- CRM, kundeportal og avansert BI/Power BI.
- AI-assistent, prediksjon og automatisert bokføring.
- Bærekraftsrapportering og avansert revisjonsstøtte.
- NUF, ASA, ANS/DA, stiftelse, forening og borettslag.

---

## 10. Eksplisitt utenfor MVP

Følgende skal ikke bygges i MVP, og skal avvises eller parkeres dersom det dukker opp i backloggen:

- lønn, a-melding, feriepenger, OTP og arbeidsgiveravgift;
- prosjekt, timeføring, ressursplanlegging og prosjektregnskap;
- varelager, lagerlokasjoner, produksjon og strekkoder;
- kassesystem, POS, nettbutikk og markedsplasser;
- CRM, tilbud, ordre og kundeportal;
- abonnementsfaktura, KID, eFaktura og avtalegiro;
- konsern, flerfirma og eliminering;
- utenlandsk valuta og kursgevinst/tap;
- anleggsregister med automatiske avskrivninger (manuelle avskrivningsbilag er tillatt);
- budsjett, prognose og dashboards utover standardrapporter;
- API, webhooks og offentlig integrasjonsmarked;
- native mobilapp;
- AI-assistent og automatisk kontering uten menneskelig godkjenning;
- bærekraftsrapportering (ESG/CSRD);
- revisjonsverktøy og avansert byråoverbygg.

---

## 11. Risiko og tiltak

| Risiko | Sannsynlighet | Konsekvens | Tiltak |
|---|---|---|---|
| EHF/Peppol-access point blir forsinket eller ikke godkjent | Middels | Høy | Velg leverandør tidlig, test i Peppol-testmiljø, ha PDF-fallback for kunder som ikke kan motta EHF |
| Altinn 3-integrasjon blir forsinket | Middels | Høy | Bygg mot testmiljø tidlig, avklar signeringsflyt og kvitteringer, ha manuell eksport som midlertidig nødløsning |
| SAF-T 1.40-skjema endres | Lav | Middels | Versjoner eksporten, valider mot XSD i CI, følg Skatteetatens endringslogg |
| OCR-feil gir feil kontering | Høy | Middels | Vis konfidens, krev menneskelig godkjenning, logg alle overstyringer |
| Juridisk feiltolkning av MVA eller skatt | Middels | Høy | Juridisk gjennomgang, konservative standardvalg, tydelig ansvarsfraskrivelse |
| Scope creep før lansering | Høy | Høy | Låst MVP-omfang, endringskontroll og P1/P2-liste |
| Sikkerhetsbrudd eller datalekkasje | Lav | Svært høy | Penetrasjonstest, minste privilegium, kryptering, overvåking og hendelsesplan |
| Migrering fra andre systemer feiler | Middels | Middels | CSV-validering, rollback, prøveimport og tydelig feilrapport |
| Gratis AI-modeller gir ustabile forslag | Middels | Middels | AI er ikke i kritisk P0-flyt; deterministiske regler og menneskelig godkjenning |
| Bankintegrasjon dekker ikke alle banker | Middels | Middels | Start med CAMT.053/CSV, prioriter PSD2 etter lansering |
| Ytelse ved mange bilag | Lav | Middels | Lasttest med 100 000 bilag, indeksering og paginering |
| Supportkapasitet ved lansering | Middels | Middels | Hjelpesenter, onboarding og tydelige svartidsmål |

---

## 12. Åpne spørsmål

> **Status 11.11.2026:** Spørsmål 1–5 er avklart og ført inn i [PLAN.md](PLAN.md) §3.4. Gjenstående spørsmål er nummerert 6–16 nedenfor, og må avklares før P0-B.

**Besvarte spørsmål 11.11.2026:**

| # | Spørsmål | Svar |
|---|---|---|
| 1 | ENK, AS eller begge? | Begge |
| 2 | EHF-access point? | Bygg eget der det er lovlig; partner for transport inntil sertifisering |
| 3 | Altinn 3? | Bygg eget som sluttbrukersystem |
| 4 | Filimport eller PSD2? | PSD2 via lisensiert AISP-partner; filimport som fallback |
| 5 | Datalagring? | PostgreSQL 16+ managed i EU/Norge; hostingleverandør avklares i ADR-003 |

**Gjenstår før P0-B:**

6. Hostingleverandør og datalagringssted.
7. BankID direkte eller via Altinn-redirect.
8. Hvor mye av årsoppgjøret skal automatiseres.
9. Kalenderår eller også avvikende regnskapsår.
10. KID i P0 eller P1.
11. Utenlandsk valuta i MVP eller P1.
12. Hvem kvalitetssikrer MVA- og skatteberegninger.
13. Hvor lenge data beholdes etter fem år.
14. Gratisversjonens begrensninger.
15. Supportmodell og språk.
16. Prøveforetak med eksempeldata.

---

## 13. Sporbarhet mot FUNKSJONSKART.md

| MVP-krav | FUNKSJONSKART-ID-er | Verifiseres av |
|---|---|---|
| MVP-01 | OPP-001–006, OPP-019 | AC-01.1–01.7 |
| MVP-02 | GRU-009–013, SIK-013–015 | AC-02.1–02.8 |
| MVP-03 | BOK-001–004, 011–014, 037–041, 046–051 | AC-03.1–03.9 |
| MVP-04 | BOK-005–010, 063–064, 077–078 | AC-04.1–04.7 |
| MVP-05 | BOK-015–017, SAL-001–003, INN-001–002, 020–021 | AC-05.1–05.8 |
| MVP-06 | SAL-012–018, 028–034, 038, 040, 054 | AC-06.1–06.9 |
| MVP-07 | BAN-001–008, BOK-018–019 | AC-07.1–07.7 |
| MVP-08 | MVA-001–008, 022–026, 030 | AC-08.1–08.7 |
| MVP-09 | BOK-046–054, RAP-001–007, 024, 028 | AC-09.1–09.7 |
| MVP-10 | SAL-020, 028–029, 052–053, BOK-078, SIK-011 | AC-10.1–10.8 |
| MVP-11 | MVA-004–006, 022–024, SIK-032 | AC-11.1–11.8 |
| MVP-12 | ÅRS-036, SIK-012 | AC-12.1–12.7 |
| MVP-13 | ÅRS-001–023, 033–037 | AC-13.1–13.9 |
| MVP-14 | SIK-013–040, GRU-026–029 | AC-14.1–14.14, NFR-01–16 |
| MVP-15 | OPP-019–024, UX-001–003 | AC-15.1–15.7 |

---

## 14. Definisjon av ferdig

En P0-historie er ferdig når:

- akseptansekriteriene er verifisert i testmiljø og dokumentert med skjermbilde, logg eller testrapport;
- koden er gjennomgått av minst én annen utvikler;
- automatiske tester dekker kjerneflyten og feiltilfellene;
- feilhåndtering, tomtilstand og tilgangskontroll er testet;
- revisjonsspor og logging er verifisert;
- ytelse og tilgjengelighet er kontrollert mot NFR-01 og NFR-06;
- dokumentasjon og hjelpetekst er oppdatert;
- ingen hemmeligheter, testdata eller personopplysninger er lagt i kildekode eller logger;
- overvåking og alarmer er på plass der det er relevant;
- produktansvarlig har godkjent resultatet.

---

## 15. Endringslogg

| Versjon | Dato | Endring |
|---|---|---|
| 0.1 | 11.11.2026 | Første utkast med P0-A, P0-B, akseptansekriterier, NFR, releasekriterier, P1/P2, risiko og sporbarhet |

<!-- END -->
