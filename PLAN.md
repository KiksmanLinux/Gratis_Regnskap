# Prosjektplan for Gratis_Regnskap

**Status:** aktiv plan per 11. november 2026
**Repo:** `KiksmanLinux/Gratis_Regnskap`
**Arbeidsbranch:** `freebuff/0b66a0297a7969a654825796`
**Basisdokumenter:** [FUNKSJONSKART.md](FUNKSJONSKART.md), [MVP-KRAVSPESIFIKASJON.md](MVP-KRAVSPESIFIKASJON.md)

---

## 1. Sammendrag

`Gratis_Regnskap` skal bli et gratis, norsk regnskapsprogram for enkeltpersonforetak og små og mellomstore aksjeselskaper. Det skal dekke den daglige regnskapsflyten fra bilag til årsregnskap, være visuelt gjenkjennelig for brukere av Fiken, Conta, Tripletex, PowerOffice Go og Visma eAccounting, og være bygget for norske krav til sporbarhet, MVA, e-faktura og SAF-T.

Arbeidet så langt har gitt:

- **658 unike funksjoner** kartlagt på tvers av **16 domener**.
- **Systemmatrise for 10 systemer** og oversikt over lønn-, årsoppgjør- og bransjesystemer.
- **Regelverkstidslinje** for 2026–2030, med e-faktura, SAF-T 1.40, digital bokføring og aksjonærregister.
- **15 MVP-krav** med **122 unike akseptansekriterier**, delt i P0-A (kjerneflyt) og P0-B (launch-blockere).
- En tydelig avgrensning: lønn, prosjekt, varelager og produksjon er ikke MVP.

Planen under er skrevet for at jeg skal kunne gjennomføre prosjektet i små, verifiserbare steg uten å miste retning, og for at du skal kunne se nøyaktig hva som er gjort, hva som gjenstår og hvilke beslutninger som må tas.

### 1.1 Arbeidsform

Hver iterasjon følger samme mønster:

1. Les planen og de relevante kravene.
2. Implementer den minste sammenhengende delen som gir verdi.
3. Skriv eller oppdater tester.
4. Kjør typecheck, lint, tester og bygg.
5. Verifiser akseptansekriteriene manuelt der det er nødvendig.
6. Oppdater planen med status, avvik og neste steg.
7. Commit og push til GitHub.

Jeg bygger ikke flere moduler samtidig. Hver fase har en eksplisitt exit-port, og jeg går ikke videre før porten er bestått eller avviket er dokumentert.

---

## 2. Mål og suksesskriterier

### 2.1 Produktmål

- Et ENK eller AS skal kunne opprette foretaket og bokføre første bilag innen 30 minutter.
- Brukeren skal kunne fakturere, registrere kvitteringer, avstemme banken, levere MVA og hente rapporter uten konsulenthjelp.
- Brukeren skal kunne avslutte året med årsregnskap, skattemelding og aksjonærregisteroppgave.
- Programmet skal føles enklere enn dagens systemer, ikke fattigere. Det skal skjule kompleksitet, ikke fjerne den.

### 2.2 Compliance-mål

- E-faktura i EHF/Peppol BIS 3.0+ fra 1. januar 2027.
- SAF-T Financial 1.40 fra 1. januar 2027.
- Kjøpers organisasjonsnummer på salgsdokument fra 1. januar 2028.
- Mottak av e-faktura og elektronisk regnskapssystem fra 1. januar 2030.
- Uforanderlig revisjonsspor, ubrytelig nummerering, periodelås og fem års oppbevaring.
- Personvern, databehandleravtale, tilgangsstyring og hendelseshåndtering etter GDPR.

### 2.3 Tekniske mål

| Mål | Suksesskriterium |
|---|---|
| Ytelse | 95 % av sidesvar under 2 sekunder ved 100 samtidige brukere |
| Rapporter | 10 000 bilag visualisert innen 5 sekunder |
| Oppetid | Minst 99,5 % per måned |
| Sikkerhet | Ingen kritiske eller høye funn ved lansering |
| Isolasjon | En kunde kan ikke se eller endre en annen kundes data |
| Backup | RPO 24 timer, RTO 4 timer, testet kvartalsvis |
| Tilgjengelighet | WCAG 2.1 AA for kjerneflyten |
| Dataportabilitet | Full eksport av regnskap, bilag og vedlegg |

### 2.4 Kommersielle mål

- Kjernefunksjonaliteten skal være gratis.
- Det skal ikke være bilagstak eller brukertak i gratisversjonen.
- Kostnader for EHF, SMS, brev og eventuelle betalingstjenester skal være transparente og viderefaktureres uten skjult påslag.
- Betalte tillegg skal være ærlige og modulære, ikke nødvendige for å føre et lovlig regnskap.

---

## 3. Målgruppe og omfang

### 3.1 Primærmålgruppe

- **Enkeltpersonforetak** innen konsulent, håndverk, kreativ virksomhet, transport, utleie og netthandel.
- **Små og mellomstore AS** med 1–20 ansatte, uten komplekst konsern, produksjon eller lager i første versjon.
- **Regnskapsførere** som fører regnskap for flere små klienter, som sekundærmålgruppe fra P1.

### 3.2 MVP-omfang

| Innenfor MVP | Utenfor MVP |
|---|---|
| ENK og AS | NUF, ASA, ANS/DA, stiftelse, forening, borettslag |
| NOK | Utenlandsk valuta |
| Kontoplan, bilag, reskontro | Lønn og a-melding |
| Salgsfaktura, PDF, e-post, EHF | Prosjekt, timeføring, ressursplanlegging |
| Kunde- og leverandørreskontro | Varelager, produksjon, strekkoder |
| Bankimport og avstemming | Kassesystem, POS, nettbutikk |
| MVA og mva-melding | Abonnement, KID, eFaktura, avtalegiro |
| Rapporter og SAF-T | CRM, tilbud, ordre, kundeportal |
| Årsoppgjør, skatt, aksjonærregister | Konsern, flerfirma, eliminering |
| Roller, revisjonsspor, sikkerhet | API, webhooks, mobilapp, AI-assistent |

### 3.3 Produktprinsipper

1. **Compliance først.** Et trekk som bryter bokføringsreglene, skal ikke bygges, uansett hvor praktisk det virker.
2. **Uforanderlighet.** Posterte data endres ikke. Rettelser skjer med nye bilag og full sporbarhet.
3. **Enkelhet skjuler kompleksitet.** Brukeren skal se få valg, men systemet skal håndtere MVA, perioder, valuta og regler korrekt.
4. **Norsk først.** Språk, kontoplan, datoformat, beløpsformat, MVA og arbeidsflyt skal føles norsk.
5. **Tillit.** Hver handling skal kunne spores, forklares og reverseres på en kontrollert måte.
6. **Åpne data.** Brukeren eier dataene sine og kan eksportere dem når som helst.
7. **Ingen skjulte kostnader.** Gratis betyr gratis kjerne, ikke gratis med skjulte transaksjonsgebyr.

---

## 4. Funnregister

Dette er de viktigste funnene fra kartleggingen. Det komplette funksjonsregisteret med alle 658 ID-er ligger i [FUNKSJONSKART.md](FUNKSJONSKART.md). Planen under viser hvordan alle domener og funn er ivaretatt.

### 4.1 Markedet

| Segment | Systemer | Typisk styrke |
|---|---|---|
| Småbedrift | Fiken, Conta, Tripletex, PowerOffice Go, Visma eAccounting | Rask oppstart, fakturering, bank, MVA |
| Mellomstore/ERP | 24SevenOffice/Finago, Duett, Uni Economy/Unimicro, Xledger | Moduler, lager, prosjekt, konsern |
| Større ERP | Visma Net, Visma Business NXT, Dynamics 365 Business Central | Kompleksitet, logistikk, produksjon, konsern |
| Lønn/HR | Visma Lønn, Huldt & Lillevik, PowerOffice Lønn, Tripletex Lønn, Fiken Lønn | A-melding, feriepenger, OTP, HR |
| Årsoppgjør/skatt | Visma Finale, Sticos, Talla, Aspia, Aider | Skattemelding, noter, revisjon |
| Bransje | Proresult, SmartDok, Telaris, Front Systems, Susoft | Bygg, logistikk, retail, prosjekt |

**Funn:**

- De fem småbedriftssystemene er de viktigste referansene for brukeropplevelse og funksjonsnivå.
- Alle har dashboard, venstremeny, hurtigoppretting, fakturering, bilagsinnboks, bank, MVA, rapporter og årsoppgjør.
- Fiken vinner på enkelhet og én pris; Conta på mobil og AI; Tripletex på moduler; PowerOffice Go på godkjenning og betaling; Visma på merkevare og økosystem.
- Forretningsmodellene varierer sterkt: bilagstak, modulpris, transaksjonskostnader, bindingstid og supportnivå.
- Det finnes et åpent rom for et gratis alternativ uten bilagstak, med tydelig compliance og ærlig prismodell.

### 4.2 Funksjonsfunn

| Domene | Antall | MVP-rolle |
|---|---:|---|
| Bokføring og bilag (`BOK`) | 80 | P0 |
| Salg og fakturering (`SAL`) | 60 | P0 |
| Lønn og HR (`LØN`) | 50 | P1 |
| Plattform (`GRU`) | 48 | P0, delvis P1 |
| Årsoppgjør og skatt (`ÅRS`) | 42 | P0 |
| Innkjøp og betaling (`INN`) | 40 | P0, delvis P1 |
| Varelager og logistikk (`VAR`) | 40 | P1/P2 |
| Sikkerhet og compliance (`SIK`) | 40 | P0 |
| Prosjekt og tid (`PRO`) | 38 | P1 |
| Rapportering og analyse (`RAP`) | 38 | P0, delvis P1 |
| Brukeropplevelse (`UX`) | 35 | P0 |
| Bank og finans (`BAN`) | 32 | P0 |
| Oppsett og migrering (`OPP`) | 30 | P0 |
| MVA (`MVA`) | 30 | P0 |
| Bransje og selskapsform (`BRA`) | 30 | P1/P2 |
| Automatisering og AI (`AUT`) | 25 | P1/P2 |

**Funn:**

- **Table stakes:** dashboard, faktura, bilagsinnboks, bankavstemming, MVA, rapporter, kontakter, søk, roller og årsoppgjør.
- **Skjult kompleksitet:** revisjonsspor, ubrytelig nummerering, periodelås, MVA-mapping, SAF-T, EHF, oppbevaring og tilgangsstyring.
- **Differensiatorer:** mobil bildefangst, AI-kontering, godkjenningsflyt, prosjektlønnsomhet, lager og bransjemoduler.
- **Norske forventninger:** norsk språk, NS 4102, MVA-koder, KID, EHF, Vipps, bankintegrasjon og årsoppgjør.
- **Viktig avgrensning:** et gratis kjerneprodukt må velge bort lønn, prosjekt og lager i første versjon for ikke å bli halvferdig.

### 4.3 Regelverksfunn

| Dato | Krav |
|---|---|
| 1. juli 2026 | Deler av endringsloven om pliktig digital bokføring og e-fakturering trer i kraft |
| Juni 2026 | Aksjonærregisteroppgaven leveres bare via sluttbrukersystem |
| 1. januar 2027 | Plikt til å utstede e-faktura til bokføringspliktige som kan motta den |
| 1. januar 2027 | Unntaket for elektronisk tilgjengelighet under 5 mill. kr oppheves |
| 1. januar 2027 | SAF-T Financial 1.40 blir eneste gyldige format |
| 1. januar 2028 | Kjøpers organisasjonsnummer skal alltid stå på salgsdokumentet |
| 1. januar 2028 | Salgsdokumentet skal alltid sendes bokføringspliktig kjøper |
| 1. januar 2030 | Plikt til å motta e-faktura |
| 1. januar 2030 | Bokføring skal skje i et elektronisk regnskapssystem |
| Regnskapsåret 2027 | NBS 6-grensen for regneark reduseres fra 600 til 200 bilag |

**Funn:**

- E-faktura og SAF-T er de to kravene som hardest påvirker arkitekturen.
- MVA-satsene er 25 %, 15 %, 12 %, 11,11 % og 0 %.
- Mva-melding leveres normalt annenhver måned, med frist én måned og ti dager etter terminen.
- A-melding leveres innen den 5. i måneden etter lønnsutbetaling.
- Skattemelding har frist 31. mai, generalforsamling 30. juni og årsregnskap 31. juli.
- Aksjonærregisteroppgaven har frist 31. januar, og fra juni 2026 kreves sluttbrukersystem.
- Revisjonsfritak for AS: under 7 mill. kr i driftsinntekter, under 27 mill. kr i balansesum og maks 10 årsverk.
- Bærekraftsreglene foreslås strammet inn vesentlig gjennom Prop. 106 L (2025–2026), men rammer først og fremst store foretak.

### 4.4 Tekniske funn

- Regnskapet må bygges som et **dobbel bokholderi** med invarianten sum debet = sum kredit per bilag.
- Posterte bilag må være **uforanderlige**, og retting må skje med tilbakeføring eller korrigeringsbilag.
- Bilagsnummer og fakturanummer må være **ubrutte serier per regnskapsår**.
- Alle tabeller må ha **tenant-id**, og tilgang må håndheves på serveren, ikke i grensesnittet.
- **Revisjonsloggen** må være append-only og inneholde bruker, tidspunkt, objekt og før/etter-verdi.
- **Vedlegg** må lagres med sjekksum og kunne hentes i fem år.
- **EHF** må lagres i opprinnelig XML-format, ikke bare som PDF.
- **SAF-T** må valideres mot XSD og mappes mot næringsspesifikasjon og standard MVA-koder.
- **Bankimport** bør starte med CAMT.053 og CSV; PSD2 kan komme senere.
- **Altinn 3**, **EHF-access point** og **BankID** er eksterne avhengigheter som må avklares tidlig.
- **PDF-generering**, **OCR** og **XML-validering** må ha testbare adaptere, slik at leverandørvalg ikke låser kjernen.

### 4.5 UX- og kommersielle funn

- Norske brukere forventer en rolig, lys og ryddig SaaS-løsning med venstremeny, dashboard, hurtigknapp for «Ny», globalt søk og tydelige frister.
- Fakturering, bilagsinnboks og bankavstemming er de tre hyppigste arbeidsflytene og må være maksimalt korte.
- Mobil brukes særlig til kvitteringsbilde, godkjenning og oversikt, ikke til full bokføring.
- Onboarding er en konkurransefordel: mange gir opp før første faktura.
- Hjelp i kontekst, norske feilmeldinger og enkel språkbruk er viktigere enn avanserte innstillinger.
- Gratismodellen må tåle kostnader til EHF, e-post, lagring og support uten å bli ulønnsom.

### 4.6 Risikoer og åpne spørsmål

**Topprisikoer:**

1. EHF/Peppol-access point blir forsinket eller ikke godkjent.
2. Altinn 3-integrasjon og signeringsflyt blir forsinket.
3. Juridisk feiltolkning av MVA, skatt eller årsoppgjør.
4. Scope creep før lansering.
5. Sikkerhetsbrudd eller datalekkasje.
6. OCR-feil gir feil kontering.
7. Migrering fra andre systemer feiler.
8. Supportkapasitet ved lansering.

**Åpne spørsmål som må avklares før P0-B:**

1. ENK, AS eller begge fra dag én?
2. Kjøpe eller bygge EHF-access point?
3. Kjøpe eller bygge Altinn 3-integrasjon?
4. Filimport eller PSD2 for bank?
5. Hvor skal data lagres?
6. BankID i egen løsning eller via Altinn?
7. Hvor mye av årsoppgjøret skal automatiseres?
8. Kalenderår eller også avvikende regnskapsår?
9. KID i P0 eller P1?
10. Utenlandsk valuta i MVP eller P1?
11. Hvem kvalitetssikrer MVA- og skatteberegninger?
12. Hvor lenge skal data beholdes etter fem år?
13. Skal gratisversjonen ha begrensninger?
14. Hvilken supportmodell og språk ved lansering?
15. Skal det finnes et prøveforetak med eksempeldata?

---

## 5. Teknisk plan

### 5.1 Tekniske prinsipper

1. **Serveren er sannheten.** Alle beløp, MVA-beregninger, nummereringer og tilgangskontroller avgjøres på serveren. Grensesnittet er aldri autoritativt.
2. **Transaksjoner før alt.** Bilag, nummerering, reskontro og revisjonslogg skrives i én databasetransaksjon.
3. **Uforanderlighet.** Posterte data oppdateres ikke. Rettelser er nye rader med referanse til originalen.
4. **All data er org-scoped.** Hver spørring filtrerer på organisasjons-ID, og tilgang sjekkes før data returneres.
5. **Adapters for eksterne tjenester.** Bank, EHF, Altinn, OCR, e-post og BankID ligger bak egne grensesnitt, slik at leverandørvalg kan endres.
6. **Idempotens.** Import, sending, betaling og innsending kan kjøres på nytt uten å duplisere data.
7. **Testbarhet.** Forretningsregler ligger i rene domenefunksjoner, ikke i React-komponenter eller databasequeries.
8. **Observerbarhet.** Hver viktig handling har korrelasjons-ID, strukturert logg og metrikk.

### 5.2 Anbefalt stack

| Lag | Valg | Begrunnelse |
|---|---|---|
| Frontend | Next.js App Router, React, TypeScript | Moderne, utbredt, god støtte for server rendering og skjemaer |
| Styling | Tailwind CSS + eget designsystem | Rask utvikling og konsistent visuelt uttrykk |
| Komponenter | Egne primitiver, eventuelt Radix/shadcn som utgangspunkt | Tilgjengelighet og kontroll uten å låse designet |
| Skjema | React Hook Form + Zod | Typesikker validering på klient og server |
| Database | Postgres som anbefalt produksjonsdatabase; D1/SQLite kan brukes i tidlig prototype | Regnskap krever transaksjoner, constraints og rapportering |
| ORM | Drizzle | Typer, migreringer og støtte for både Postgres og SQLite |
| Auth | Egen sesjonsbasert auth med e-post/passord, TOTP og recovery-koder; BankID som egen adapter senere | Kontroll på 2FA og sporbarhet |
| Filer | S3-kompatibel lagring eller R2 | Vedlegg, PDF og eksportfiler |
| PDF | Server-side PDF-adapter, valgt etter spike | Faktura og årsregnskap må være deterministisk |
| Jobber | Jobbtabell + sikret cron-endepunkt | Purring, påminnelser, OCR og rapportgenerering |
| E-post | Transaksjonsleverandør bak adapter | Faktura, invitasjoner og varsler |
| Testing | Vitest, Playwright, axe | Enhet, E2E og tilgjengelighet |
| CI | GitHub Actions | Typecheck, lint, test, bygg og XML-validering |
| Hosting | Norge/EØS, container eller serverless | Personvern og datalagringskrav |

**ADR-001:** Databasevalg tas i Fase 0. Kravet er ACID-transaksjoner, foreign keys, unike constraints, gode rapporteringsmuligheter og enkel migrering. Postgres er foreløpig anbefaling fordi regnskapsdata har strenge konsistenskrav.

**ADR-002:** PDF-generering tas i Fase 0. Kravet er norsk tegnsett, logo, tabeller, sidebryting, deterministisk output og testbare filer.

### 5.3 Modulære grenser

| Modul | Ansvar | Avhengigheter |
|---|---|---|
| `identity` | Brukere, sesjoner, 2FA, invitasjoner | Ingen |
| `organizations` | Foretak, medlemskap, roller, innstillinger | identity |
| `ledger` | Kontoplan, bilag, posteringer, nummerserier, perioder | organizations |
| `documents` | Vedlegg, bilagsinnboks, OCR, arkiv | ledger, organizations |
| `contacts` | Kunder og leverandører | organizations |
| `invoicing` | Faktura, kreditnota, purring, PDF | ledger, contacts, documents |
| `banking` | Bankkontoer, import, matching, avstemming | ledger, invoicing |
| `vat` | MVA-koder, beregning, rapport, avstemming | ledger |
| `reporting` | Hovedbok, saldobalanse, resultat, balanse, eksport | ledger |
| `yearend` | Avslutning, årsregnskap, skatt, aksjonærregister | ledger, reporting, vat |
| `integrations` | EHF, Altinn, bank, OCR, e-post, BankID | Alle relevante |
| `audit` | Append-only revisjonslogg | Alle |
| `notifications` | Varsler, oppgaver og frister | Alle |

Regelen er at en modul bare eksponerer tjenester og typer, ikke interne databasetabeller. `ledger` er kjernen, og ingen andre moduler skriver direkte til bilagstabellene.

### 5.4 Datamodell

**Kjernentiteter:**

- `organizations` – organisasjonsnummer, navn, selskapsform, adresse, MVA-status, regnskapsår.
- `users`, `memberships`, `sessions`, `roles` – identitet og tilgang.
- `fiscal_years`, `periods` – regnskapsår og låsbare perioder.
- `accounts` – kontonummer, navn, type, MVA-kode, aktiv/inaktiv.
- `vat_codes` – sats, konto, SAF-T-kode, gyldighetsperiode.
- `number_sequences` – serie per foretak, år og dokumenttype.
- `vouchers`, `voucher_lines` – bilag og posteringer.
- `attachments` – fil, sjekksum, type, opplasting, kobling.
- `customers`, `suppliers` – parter og betalingsbetingelser.
- `invoices`, `invoice_lines`, `invoice_events` – salgsfaktura og livsløp.
- `payments`, `payment_allocations` – inn- og utbetalinger og fordeling.
- `bank_accounts`, `bank_statements`, `bank_transactions`, `reconciliations` – bank og avstemming.
- `tax_returns`, `tax_return_lines` – MVA og skatt.
- `annual_accounts`, `shareholder_entries` – årsoppgjør og aksjonærregister.
- `audit_events` – append-only revisjonsspor.
- `integration_connections`, `jobs` – integrasjoner og bakgrunnsjobber.

**Ufravikelige invarianter:**

- Sum debet = sum kredit per bilag, alltid.
- Et bilag har minst to linjer og tilhører ett foretak og ett regnskapsår.
- Posterte bilag kan ikke endres eller slettes.
- Nummerserier tildeles i en databasetransaksjon og har ingen hull.
- Alle beløp lagres som heltall i øre, aldri flyttall.
- Alle datoer lagres som ISO-dato, og vises som DD.MM.ÅÅÅÅ.
- MVA beregnes alltid på serveren ut fra kode og sats.
- Alle tabeller har `organization_id`, og alle spørringer er scopet.
- Sletting er bare tillatt for kladder og ikke-postert materiale.
- Revisjonsloggen er append-only og kan ikke slettes av bruker.

### 5.5 Integrasjonsstrategi

| Integrasjon | MVP-strategi | Senere |
|---|---|---|
| Bank | CAMT.053 og CSV-import, manuell og automatisk matching | PSD2 og direktesaldo |
| EHF/Peppol | Bygg UBL/EHF XML, valider med golden files, send via access point-adapter | Flere dokumenttyper og selvfakturering |
| Altinn 3 | Adapter for mva-melding, skattemelding og årsregnskap | Utvidet meldingsflyt og status |
| BankID | Signeringsadapter, først via Altinn-redirect | Direkte BankID-integrasjon |
| OCR | Leverandøradapter med konfidens og manuell kontroll | Egen modell eller bedre tolkning |
| E-post | Transaksjonsadapter for faktura og invitasjoner | Innboks og automatisk svarkobling |
| Lagring | S3-kompatibel eller R2 | Livssyklus og arkivtier |

**Viktig:** EHF-access point, Altinn 3 og BankID er eksterne avhengigheter. De kan ikke «kodes ferdig» i sandkassen uten avtaler, testmiljø og sertifisering. Planen legger derfor opp til adaptere, testdobler og tydelige blokkere i Fase 0.

### 5.6 Sikkerhet og compliance i arkitekturen

- Tilgangskontroll håndheves i serverlaget med en eksplisitt autorisasjonsmatrise per rolle og handling.
- Alle muterende handlinger krever CSRF-beskyttelse eller same-origin-sjekk.
- Sesjoner er korte, roterbare og kan tilbakekalles.
- Passord, tokens og hemmeligheter lagres aldri i klartekst eller i repoet.
- Vedlegg scannes for skadelig innhold og serveres med riktig Content-Type.
- Revisjonsloggen dekker innlogging, bilag, faktura, betaling, eksport, rolleendring og innstillinger.
- Produksjonsdata brukes ikke i utvikling uten anonymisering.
- Databehandleravtale, personvernerklæring og underdatabehandlere er dokumentert.

### 5.7 Teststrategi

| Nivå | Hva testes | Verktøy |
|---|---|---|
| Enhet | MVA, bilagsbalanse, nummerserier, matching, formatering | Vitest |
| Property-based | Tilfeldige bilag balanserer, nummer er unike, ingen negative restbeløp | Vitest + fast-check |
| Integrasjon | Database, transaksjoner, constraints, lagring, e-post | Vitest + testdatabase |
| Kontrakt | EHF XML og SAF-T XML mot golden files og XSD | XML-validator i CI |
| E2E | Onboarding, bilag, faktura, bank, MVA, rapporter, årsoppgjør | Playwright |
| Sikkerhet | Autorisasjonsmatrise, tenant-isolasjon, filopplasting | Playwright + API-tester |
| Ytelse | 10 000 og 100 000 bilag | Lasttest |
| Tilgjengelighet | Kjerneflyt med tastatur og skjermleser | axe + manuell test |

Testdata skal være realistiske, men syntetiske. Pilotkunder brukes bare i UAT med samtykke og egen avtale.

---

## 6. UI/UX-plan

### 6.1 Visuell retning

Målet er at programmet skal kjennes umiddelbart gjenkjennelig for en norsk regnskapsbruker, uten å kopiere noen annens design.

| Element | Retning |
|---|---|
| Helhet | Rolig, lys, profesjonell norsk SaaS |
| Bakgrunn | Lys grå/hvit, hvite kort med subtil kant |
| Primærfarge | Dyp blå eller dempet teal/grønn for handlinger og aktiv tilstand |
| Varsler | Amber for frister, rød for feil, grønn for fullført |
| Typografi | Inter eller tilsvarende, 14–16 px basis, tydelig hierarki |
| Layout | Venstremeny, toppbar med foretaksvelger, globalt søk og «Ny»-knapp |
| Tetthet | Kompakt, men luftig nok for regnskapstabeller |
| Radius | 8–12 px på kort, 6–8 px på knapper |
| Ikoner | Enkle linjeikoner, norske fagtermer |

**Referanser:** Fikens enkelhet, Tripletex’ modulnavigasjon, PowerOffice Go sitt dashboard, Visma sin profesjonalitet og Conta sin onboarding. Vi låner prinsipper, ikke merkevare eller eksakt layout.

### 6.2 Navigasjonskart

- **Dashboard** – likviditet, kundefordringer, MVA, resultat, oppgaver og siste bilag.
- **Salg** – fakturaer, kunder, kreditnotaer og purringer.
- **Innkjøp** – bilagsinnboks, leverandørfakturaer og leverandører.
- **Bank** – kontoer, import, matching og avstemming.
- **Regnskap** – bilag, hovedbok, saldobalanse, MVA og rapporter.
- **Årsoppgjør** – sjekkliste, avslutning, årsregnskap, skatt og aksjonærregister.
- **Innstillinger** – foretak, brukere, roller, kontoplan, MVA, integrasjoner og revisjonslogg.

Hurtigknappen «Ny» gir alltid: nytt bilag, ny faktura, ny kunde, ny leverandør og last opp bilag.

### 6.3 Skjermer i MVP

| Skjerm | Formål | Nøkkelkomponenter |
|---|---|---|
| Logg inn | Sikker tilgang | E-post, passord, 2FA, glemt passord |
| Onboarding | Kom i gang | Stegviser, selskapsform, kontoplan, bank, MVA, åpningsbalanse |
| Dashboard | Oversikt | KPI-kort, kontantstrøm, MVA-status, oppgaver, siste bilag |
| Bilagsliste | Finn og filtrer | Tabell, periode, status, søk, massehandlinger |
| Bilagsdetalj | Se og rette | Linjer, MVA, vedlegg, revisjonsspor, tilbakeføring |
| Bilagsinnboks | Ta imot dokumenter | Opplasting, e-post, OCR, duplikat, kobling |
| Fakturaliste | Følg opp salg | Status, forfall, utestående, purring |
| Faktura | Lag og send | Kunde, linjer, MVA, PDF, e-post, EHF |
| Kunder | Administrer parter | Kontaktinfo, org.nr, betingelser, åpne poster |
| Leverandører | Administrer parter | Kontaktinfo, betingelser, åpne poster |
| Bank | Avstem | Import, transaksjoner, forslag, differanse |
| MVA | Lever og kontroller | Termin, grunnlag, satser, avstemming, utkast |
| Rapporter | Analyser | Saldobalanse, hovedbok, resultat, balanse, eksport |
| Årsoppgjør | Avslutt året | Sjekkliste, avslutningsbilag, årsregnskap, skatt |
| Innstillinger | Konfigurer | Foretak, brukere, kontoplan, MVA, integrasjoner |
| Revisjonslogg | Kontroller | Filter, aktør, tidspunkt, objekt, før/etter |

### 6.4 Komponentbibliotek

- `AppShell` med sidemeny, toppbar og brødsmuler.
- `DataTable` med sortering, filtrering, paginering og tomtilstand.
- `MoneyInput` med norsk format, øre og valutamerking.
- `AccountPicker` med søk på kontonummer og navn.
- `VatPicker` med sats, kode og forklaring.
- `PeriodPicker` og `DateRange` med regnskapsår og terminer.
- `StatusBadge` for kladd, postert, sendt, betalt, forfalt og avvist.
- `KpiCard`, `Chart`, `EmptyState`, `ConfirmDialog` og `FileDropzone`.
- `AuditTrail` som viser hvem, hva, når og før/etter.
- `OnboardingChecklist` med fremdrift og neste steg.

### 6.5 Mobil og responsivitet

- Mobil først for kvitteringsbilde, godkjenning og dashboard.
- Tabeller blir kort på små skjermer, med de viktigste kolonnene synlige.
- Faktura og bilag kan opprettes på nettbrett, men full redigering er primært desktop.
- Alle berøringsmål er minst 44 × 44 px.

### 6.6 Tilgjengelighet og språk

- WCAG 2.1 AA for kjerneflyten.
- Tastaturnavigasjon, fokusmarkering, skjermleseretiketter og feiloppsummering.
- Norsk bokmål som standard, engelsk som valg.
- Dato DD.MM.ÅÅÅÅ, beløp med norsk tusenskille og komma, valuta NOK.
- Feilmeldinger skal si hva som er galt, hvor det er galt og hva brukeren kan gjøre.

### 6.7 Designmilepæler

1. Design tokens, typografi, farger og spacing.
2. AppShell og navigasjon.
3. Dashboard, bilagsliste og bilagsdetalj.
4. Faktura, kunde og bilagsinnboks.
5. Bank, MVA og rapporter.
6. Årsoppgjør, innstillinger og revisjonslogg.
7. Responsiv og tilgjengelighetsgjennomgang.

---

## 7. Gjennomføringsplan

### 7.1 Faser og porter

| Fase | Innhold | Estimat | Exit-port |
|---|---|---|---|
| **Fase 0** | Grunnmur: stack, CI, database, auth, design system, audit | 2–3 uker | App kjører, bruker kan opprette foretak, CI er grønn |
| **Fase 1** | P0-A: kjerneflyt fra kontoplan til rapporter | 8–10 uker | Privat beta med to pilotkunder og én MVA-termin |
| **Fase 2** | P0-B: EHF, Altinn, SAF-T, årsoppgjør, sikkerhet, onboarding | 7–9 uker | Offentlig lansering med alle releasekriterier oppfylt |
| **Fase 3** | P1: lønn, prosjekt, KID, abonnement, anlegg, varelager, API, byrå | 10–14 uker | Betalte tillegg og byråbruk |
| **Fase 4** | P2: konsern, produksjon, bransjer, CRM, AI, ESG | Løpende | Segmenterte tillegg |

Estimatene er relative og skal kalibreres etter Fase 0. De er ikke løfter om dato, men planleggingsforutsetninger.

### 7.2 Milepæler

| Milepæl | Bevis |
|---|---|
| **M0 – Grunnmur** | Repo, CI, migreringer, auth, foretak og tom dashboard |
| **M1 – Første bilag** | Bruker kan opprette foretak, føre bilag med vedlegg og se saldobalanse |
| **M2 – Første faktura** | Faktura kan lages, sendes som PDF, bokføres og purres |
| **M3 – Første avstemming** | Bankfil kan importeres, matches og låses |
| **M4 – Første MVA** | MVA kan beregnes, avstemmes og leveres |
| **M5 – Privat beta** | To pilotkunder har ført én MVA-termin |
| **M6 – Første EHF** | EHF-faktura er validert og sendt i testmiljø |
| **M7 – Første SAF-T** | SAF-T 1.40 validerer og stemmer med hovedboken |
| **M8 – Første årsoppgjør** | ENK og AS er avsluttet med årsregnskap og skattemelding |
| **M9 – Offentlig lansering** | Alle releasekriterier er oppfylt |

### 7.3 Fase 0 – grunnmur

**Mål:** et trygt skjelett som alle senere moduler bygger på.

- [ ] **0.1 Avklare målgruppe og de 15 åpne spørsmålene** i MVP-dokumentet, med prioritet på de seks kritiske.
- [ ] **0.2 ADR-001 Database:** velg Postgres eller D1/SQLite, med ACID, constraints og migreringer.
- [ ] **0.3 ADR-002 PDF:** velg PDF-adapter og test norsk tegnsett, tabeller og sidebryting.
- [ ] **0.4 ADR-003 Hosting:** velg Norge/EØS-drift, miljøer og hemmelighetshåndtering.
- [ ] **0.5 ADR-004 Auth:** velg sesjonsløsning, passordpolicy, TOTP og recovery-koder.
- [ ] **0.6 Scaffold:** Next.js, TypeScript, Tailwind, mapper, lint, format og testoppsett.
- [ ] **0.7 CI:** typecheck, lint, enhetstester, bygg og senere XML-validering.
- [ ] **0.8 Database:** migreringer, seed for NS 4102 og MVA-koder, testdatabase.
- [ ] **0.9 Designsystem:** tokens, typografi, farger, spacing, AppShell og ikoner.
- [ ] **0.10 Auth og foretak:** innlogging, opprett foretak, medlemskap og roller.
- [ ] **0.11 Audit:** append-only hendelseslogg og korrelasjons-ID.
- [ ] **0.12 Miljøer:** dev, staging og prod, med egne hemmeligheter og backup.
- [ ] **0.13 Backlog:** epics, issues, labels og mal for akseptansekriterier.

**Exit-port:** En ny bruker kan logge inn, opprette et ENK, invitere en leser, se tom dashboard, og alle handlinger havner i revisjonsloggen. CI er grønn, og en ny database kan migreres fra bunnen av med én kommando.

### 7.4 Fase 1 – P0-A

**Mål:** en komplett, lovlig regnskapsflyt for ENK og AS uten EHF, Altinn og årsoppgjør.

- [ ] **1.1 Foretaksoppsett:** selskapsform, kontoplan, MVA, bankkonto og åpningsbalanse (MVP-01).
- [ ] **1.2 Bilagsmotor:** bilag, linjer, MVA, nummerserier, uforanderlighet og periodelås (MVP-03).
- [ ] **1.3 Bilagsinnboks:** opplasting, e-post, OCR, duplikat og vedlegg (MVP-04).
- [ ] **1.4 Reskontro:** kunder, leverandører, åpne poster, delbetaling og aldersfordeling (MVP-05).
- [ ] **1.5 Fakturering:** PDF, e-post, kreditnota og purring (MVP-06).
- [ ] **1.6 Bank:** CAMT.053/CSV, matching, bankregler og avstemming (MVP-07).
- [ ] **1.7 MVA:** koder, beregning, rapport og avstemming (MVP-08).
- [ ] **1.8 Rapporter:** saldobalanse, hovedbok, resultat, balanse, journal og eksport (MVP-09).
- [ ] **1.9 Roller og revisjon:** autorisasjonsmatrise, revisjonslogg og gjenåpning (MVP-02, MVP-10).
- [ ] **1.10 Kvalitet:** E2E-tester, ytelsestest og tilgjengelighet for kjerneflyten.
- [ ] **1.11 Pilot:** to pilotkunder fører én MVA-termin og gir skriftlig tilbakemelding.

**Exit-port:** En pilotkunde kan bokføre, fakturere, avstemme banken, levere MVA og hente rapporter uten manuell hjelp. Alle P0-A-kriterier er bestått.

### 7.5 Fase 2 – P0-B

**Mål:** oppfylle launch-blockerne og tåle offentlig trafikk.

- [ ] **2.1 EHF/Peppol:** XML-generering, validering, access point, status og original arkivering (MVP-10).
- [ ] **2.2 Altinn 3:** mva-melding, signering, innsending og kvittering (MVP-11).
- [ ] **2.3 SAF-T 1.40:** eksport, mapping, XSD-validering og saldokontroll (MVP-12).
- [ ] **2.4 Årsoppgjør:** ENK og AS, årsregnskap, skattemelding og aksjonærregister (MVP-13).
- [ ] **2.5 Sikkerhet:** trusselmodell, penetrasjonstest, DPA, personvern og hendelsesplan (MVP-14).
- [ ] **2.6 Onboarding:** veiviser, CSV-import og feilrapport (MVP-15).
- [ ] **2.7 Ytelse og tilgjengelighet:** lasttest, WCAG 2.1 AA og nettlesermatrise.
- [ ] **2.8 UAT og release:** fem pilotkunder, go/no-go og lanseringssjekkliste.

**Exit-port:** Alle releasekriteriene i MVP-dokumentet er oppfylt, og en ekstern bruker kan opprette foretak, fakturere med EHF, levere MVA og avslutte året uten assistanse.

### 7.6 Fase 3 – P1

Rekkefølgen er valgt ut fra kundeverdi, teknisk gjenbruk og risiko:

1. **KID og eFaktura** – bygger på bank og faktura.
2. **Abonnementsfaktura, tilbud og ordre** – bygger på faktura og kunde.
3. **Anleggsregister** – bygger på bilag og årsoppgjør.
4. **Enkelt varelager** – bygger på bilag og rapporter.
5. **Prosjekt og timeføring** – bygger på faktura, lønn og rapporter.
6. **Reiseregning, utlegg og kjørebok** – bygger på bilag og eventuelt lønn.
7. **Lønn og a-melding** – eget fagområde, høy risiko, tas etter at kjerne og prosjekt er stabilt.
8. **Budsjett og dashboards** – bygger på rapporter.
9. **API og webhooks** – bygger på stabil datamodell.
10. **Byråoverbygg** – bygger på roller, klienttilgang og rapporter.
11. **Mobilapp** – bygger på responsiv web og API.
12. **Flerfirma** – bygger på foretak og roller.
13. **Utenlandsk valuta** – bygger på bilag, faktura og bank.

Hvert P1-tema får egen kravspesifikasjon og akseptansekriterier før det bygges.

### 7.7 Fase 4 – P2

P2 bygges bare når det finnes kunder eller partnerskap som rettferdiggjør det:

- konsern, eliminering og konsernkonto;
- produksjon, stykkliste og arbeidsordre;
- lagerlokasjoner, strekkoder, batch og 3PL;
- bransjemoduler for bygg, elektro, VVS, landbruk, restaurant og helse;
- CRM, kundeportal og Power BI;
- AI-assistent, prediksjon og automatisert bokføring;
- bærekraftsrapportering og avansert revisjonsstøtte;
- NUF, ASA, ANS/DA, stiftelse, forening og borettslag.

### 7.8 Sprintplan (foreløpig)

| Sprint | Fokus | Viktigste leveranse |
|---|---|---|
| S0 | Beslutninger og scaffold | ADR-er, repo, CI, miljøer |
| S1 | Auth, foretak, roller | Innlogging, 2FA, invitasjon, org |
| S2 | Kontoplan og perioder | NS 4102, MVA-koder, åpningsbalanse |
| S3 | Bilagsmotor | Bilag, linjer, nummer, MVA, låsing |
| S4 | Dokumenter | Opplasting, e-post, OCR, vedlegg |
| S5 | Reskontro | Kunder, leverandører, åpne poster |
| S6 | Fakturering | PDF, e-post, kreditnota, purring |
| S7 | Bank | Import, matching, avstemming |
| S8 | MVA og rapporter | MVA-rapport, saldobalanse, hovedbok |
| S9 | Hardening og beta | Sikkerhet, E2E, ytelse, P0-A-port |
| S10 | EHF | XML, validering, access point, arkiv |
| S11 | Altinn 3 | Mva-melding, signering, kvittering |
| S12 | SAF-T | 1.40, mapping, validering |
| S13 | Årsoppgjør | ENK, AS, skatt, aksjonærregister |
| S14 | UAT og release | Pilot, pen test, go/no-go |
| S15 | Lansering | Produksjon, overvåking, support |

Sprintene er to uker. Etter hver sprint: demo, retrospektiv, oppdatert plan og justert neste sprint.

---

## 8. Arbeidsmåte for meg

Dette er den operative planen jeg følger i hver økt.

### 8.1 Før jeg skriver kode

1. Les `PLAN.md`, `MVP-KRAVSPESIFIKASJON.md` og relevant del av `FUNKSJONSKART.md`.
2. Finn neste åpne oppgave i riktig fase. Ikke hopp til P1 eller P2.
3. Skriv en kort plan i oppgaven: hva som skal endres, hvilke akseptansekriterier som dekkes, og hvordan det testes.
4. Sjekk om endringen krever en ADR, ny avhengighet eller ekstern avtale.

### 8.2 Mens jeg bygger

1. Gjør den minste sammenhengende endringen som oppfyller kravet.
2. Hold domenelogikk i rene funksjoner og databaseaccess i repositories.
3. Legg til tester for både happy path og feiltilfeller.
4. Unngå å duplisere forretningsregler i React, API og database.
5. Oppdater dokumentasjonen samtidig som koden.

### 8.3 Før jeg sier at noe er ferdig

1. Kjør typecheck, lint, tester og bygg.
2. Verifiser akseptansekriteriene mot testdata.
3. Sjekk tilgangskontroll og tenant-isolasjon.
4. Sjekk at revisjonslogg og feilhåndtering er på plass.
5. Sjekk at ingen hemmeligheter eller personopplysninger er committet.
6. Oppdater `PLAN.md` med status og neste steg.
7. Commit og push med en beskrivende melding.

### 8.4 Når jeg er blokkert

- Dokumenter blokkeren i planen med hva som mangler, hvem som eier den, og hva som kan gjøres i mellomtiden.
- Velg den minste trygge fallbacken, for eksempel filimport i stedet for PSD2 eller XML-generering med testadapter i stedet for produksjons-access point.
- Spør bare når svaret er nødvendig for å komme videre, og still ett konkret spørsmål om gangen.

### 8.5 Kvalitetsregler

- Aldri skriv en test som bare bekrefter at koden gjør det den gjør. Test forretningsregelen.
- Aldri svekk en test eller legg inn en suppression for å få grønt.
- Aldri slett eller skjul en feil. Rapporter den.
- Aldri commit hemmeligheter, tokens eller produksjonsdata.
- Aldri bygg en funksjon som bryter bokføringsreglene, selv om den er praktisk.
- Aldri si at noe er testet når det bare er kompilert.

### 8.6 Verktøykommandoer

Når prosjektet er scaffoldet, skal disse kommandoene være standard:

```bash
npm run typecheck
npm run lint
npm test
npm run build
npm run test:e2e
```

Hver kommando skal ha egen exit-status i CI, og feil skal aldri skjules gjennom pipe til `head` eller `tail`.

---

## 9. Backlog og issue-struktur

### 9.1 Epics

- `EPIC-00` Grunnmur
- `EPIC-01` Foretak og kontoplan
- `EPIC-02` Bilag og bokføring
- `EPIC-03` Bilagsinnboks
- `EPIC-04` Reskontro
- `EPIC-05` Fakturering
- `EPIC-06` Bank
- `EPIC-07` MVA
- `EPIC-08` Rapporter
- `EPIC-09` Sikkerhet og revisjon
- `EPIC-10` EHF og arkivering
- `EPIC-11` Altinn 3
- `EPIC-12` SAF-T
- `EPIC-13` Årsoppgjør
- `EPIC-14` Onboarding
- `EPIC-15` Lansering

### 9.2 Labels

- Prioritet: `p0-a`, `p0-b`, `p1`, `p2`.
- Område: `area:ledger`, `area:invoicing`, `area:bank`, `area:vat`, `area:reports`, `area:auth`, `area:design`, `area:infra`.
- Type: `type:feature`, `type:bug`, `type:spike`, `type:docs`, `type:security`.
- Status: `blocked`, `needs-decision`, `ready`, `in-progress`, `review`.

### 9.3 Issue-mal

Hver issue skal inneholde:

- kontekst og hvorfor;
- hvilke MVP-krav og akseptansekriterier den dekker;
- hvordan den testes;
- avhengigheter og risiko;
- om den krever ADR eller ekstern avtale.

### 9.4 Commit- og branchkonvensjon

- Branch: `feat/<kort-navn>`, `fix/<kort-navn>`, `docs/<kort-navn>`.
- Commit: `feat(ledger): add voucher numbering` eller `fix(vat): correct 12 % rounding`.
- Hver commit skal være mulig å forstå uten resten av grenen.

---

## 10. Lansering og drift

### 10.1 Statusboard

| Område | Status | Bevis |
|---|---|---|
| Marked og systemer | Ferdig kartlagt | `FUNKSJONSKART.md` kapittel 1 og 4 |
| Funksjonskatalog | Ferdig, 658 ID-er | `FUNKSJONSKART.md` kapittel 3 |
| Regelverk og tidslinje | Ferdig per november 2026 | `FUNKSJONSKART.md` kapittel 5 |
| MVP-krav | Ferdig, 15 krav og 122 akseptansekriterier | `MVP-KRAVSPESIFIKASJON.md` |
| Prosjektplan | Denne filen | `PLAN.md` |
| Teknisk arkitektur | Retning valgt, ADR-er gjenstår | Kapittel 5 og 11 |
| Designsretning | Valgt, skjermer planlagt | Kapittel 6 |
| Kode | Ikke startet | – |
| Integrasjoner | Blokkert på beslutninger og avtaler | Kapittel 5.5 og 11 |
| Test og lansering | Planlagt | Kapittel 7 og 8 |

### 10.2 Miljøer

- **Lokal utvikling:** testdatabase, testlagring og test-e-post. Ingen produksjonsdata.
- **Staging:** produksjonslik konfigurasjon, egne hemmeligheter og egne testbrukere.
- **Produksjon:** Norge/EØS, kryptert, overvåket og med begrenset tilgang.
- **Sandbox for integrasjoner:** Peppol-testmiljø, Altinn-testmiljø og banktestfiler.

### 10.3 Backup og gjenoppretting

- Daglig full sikkerhetskopi og kontinuerlig logg der databasen støtter det.
- RPO 24 timer, RTO 4 timer.
- Gjenoppretting testes kvartalsvis og dokumenteres med dato, ansvarlig og resultat.
- Vedlegg og eksportfiler sikkerhetskopieres sammen med databasen.
- Sletting og oppbevaring følger lovpålagt femårsperiode og dokumentert legal hold.

### 10.4 Overvåking

- Feilrate, responstid, databasetid, kølengde og jobbfeiler.
- Varsel ved 5xx, innloggingsfeil, mislykket EHF/Altinn og manglende cron-jobb.
- Revisjonslogg for administratorhandlinger og eksport.
- Statussside og intern hendelseskanal.

### 10.5 Support

- Hjelpesenter med artikler for onboarding, bilag, faktura, bank, MVA og årsoppgjør.
- E-postsupport med svartidsmål: kritiske feil innen 4 timer i arbeidstid, andre innen én virkedag.
- In-app hjelp og kontekstuelle lenker.
- Support skal ikke ha tilgang til kundedata uten samtykke og tidsbegrenset tilgang.

### 10.6 Migrering og onboarding

- CSV-maler for kontoplan, kunder, leverandører og åpningsbalanse.
- Validering per rad, feilrapport og rollback.
- Sjekkliste for å komme i gang, med fremdrift og neste steg.
- Senere: import fra SIE-4, Fiken, Tripletex og Visma eAccounting.

### 10.7 Kostnadsmodell

- Kjernefunksjonalitet er gratis.
- EHF, SMS, brev og eventuelle betalingstjenester viderefaktureres til selvkost uten skjult påslag.
- Lagring og OCR har interne kostnader som må overvåkes per kunde.
- Eventuelle betalte tillegg skal være modulære og ikke nødvendige for et lovlig regnskap.
- Misbruk og gratisversjon skal begrenses med rimelige vilkår, ikke med skjulte bilagstak.

### 10.8 Juridisk

- Personvernerklæring, brukervilkår og databehandleravtale.
- Tydelig ansvarsfraskrivelse for skattemessige vurderinger, uten å fraskrive seg ansvar for systemets beregninger.
- Avtale om oppbevaring, eksport og sletting.
- Gjennomgang av fakturainnhold, MVA og årsoppgjør med norsk regnskapsfaglig kompetanse.
- Vurdering av regnskapsførerloven dersom vi tilbyr byråfunksjoner.

### 10.9 Lanseringssjekkliste

- [ ] Alle P0-A og P0-B akseptansekriterier bestått.
- [ ] Fem pilotkunder har signert UAT.
- [ ] Penetrasjonstest uten kritiske eller høye funn.
- [ ] EHF, Altinn 3, SAF-T 1.40 og årsoppgjør testet.
- [ ] Backup og gjenoppretting testet.
- [ ] Overvåking, alarmer og statussside klare.
- [ ] Support og hjelpesenter klare.
- [ ] Personvern, vilkår og DPA publisert.
- [ ] Ytelse, WCAG 2.1 AA og nettlesermatrise bestått.
- [ ] Go/no-go signert av produkt, teknisk, sikkerhet og juridisk.

### 10.10 Etter lansering

Følg med på:

- aktivering: andel som oppretter foretak og posterer første bilag;
- tid til første faktura;
- andel banktransaksjoner som matches automatisk;
- andel MVA-meldinger levert innen frist;
- feilrate og supportvolum;
- kundetilfredshet og videre bruk;
- kostnad per kunde for OCR, lagring og e-post.

---

## 11. Beslutningslogg

| ADR | Tema | Foreløpig beslutning | Status | Frist |
|---|---|---|---|---|
| ADR-001 | Database | Postgres anbefalt; D1/SQLite som alternativ | Åpen | Fase 0 |
| ADR-002 | PDF | Egen server-side PDF-adapter | Åpen | Fase 0 |
| ADR-003 | Hosting | Norge/EØS, container eller serverless | Åpen | Fase 0 |
| ADR-004 | Auth | Egen sesjon, e-post/passord, TOTP og recovery | Foreslått | Fase 0 |
| ADR-005 | EHF | Kjøpe access point, bygge XML selv | Åpen | Før S10 |
| ADR-006 | Altinn 3 | Kjøpe eller bygge integrasjon | Åpen | Før S11 |
| ADR-007 | Bank | Filimport først, PSD2 senere | Foreslått | Fase 1 |
| ADR-008 | OCR | Leverandøradapter med konfidens | Foreslått | Fase 1 |
| ADR-009 | UI | Next.js, Tailwind og eget designsystem | Foreslått | Fase 0 |
| ADR-010 | Forretningsmodell | Gratis kjerne, transparent viderefakturering | Foreslått | Før lansering |
| ADR-011 | Oppbevaring | Fem år, deretter sletting med legal hold | Foreslått | Før lansering |
| ADR-012 | Signering | Altinn-redirect først, BankID direkte senere | Foreslått | Før S11 |

---

## 12. Neste ti handlinger

1. [x] Kartlegge marked, funksjoner og regelverk.
2. [x] Skrive MVP-krav med akseptansekriterier.
3. [x] Skrive denne prosjektplanen.
4. [ ] Pushe dokumentene til GitHub.
5. [ ] Avklare de seks kritiske spørsmålene med deg.
6. [ ] Skrive ADR-001 til ADR-004.
7. [ ] Scaffolde Next.js-prosjektet med CI.
8. [ ] Lage databaseskjema, migreringer og seed for NS 4102.
9. [ ] Bygge auth, foretak, roller og AppShell.
10. [ ] Bygge første vertikale snitt: opprett foretak → før bilag → se saldobalanse.

---

## 13. Vedlegg

### 13.1 Filindeks

| Fil | Innhold |
|---|---|
| [README.md](README.md) | Kort prosjektbeskrivelse og lenker |
| [FUNKSJONSKART.md](FUNKSJONSKART.md) | 658 funksjoner, systemmatrise, regelverk og kilder |
| [MVP-KRAVSPESIFIKASJON.md](MVP-KRAVSPESIFIKASJON.md) | 15 P0-krav med 122 akseptansekriterier |
| [PLAN.md](PLAN.md) | Denne planen: funn, arkitektur, faser og arbeidsmåte |

### 13.2 Dokumentkart

| Spørsmål | Dokument |
|---|---|
| Hvilke funksjoner finnes i markedet? | `FUNKSJONSKART.md` kapittel 3 |
| Hvilke systemer er vanligst? | `FUNKSJONSKART.md` kapittel 1 og 4 |
| Hva krever loven, og når? | `FUNKSJONSKART.md` kapittel 5 |
| Hva må MVP-en inneholde? | `MVP-KRAVSPESIFIKASJON.md` |
| Hvordan vet vi at et krav er oppfylt? | `MVP-KRAVSPESIFIKASJON.md` akseptansekriterier |
| Hva bygger vi først? | `PLAN.md` kapittel 7 |
| Hvordan jobber jeg? | `PLAN.md` kapittel 8 |
| Hvilke beslutninger mangler? | `PLAN.md` kapittel 11 |

### 13.3 Ordliste

- **Bilag:** dokumentasjon av en regnskapstransaksjon.
- **Postering:** debet- eller kreditlinje i et bilag.
- **Reskontro:** oversikt over kundefordringer eller leverandørgjeld.
- **Avstemming:** kontroll av at to datasett stemmer, for eksempel bank mot hovedbok.
- **Periodelås:** sperre for endringer i en avsluttet periode.
- **MVA:** merverdiavgift.
- **Mva-melding:** periodisk rapportering av MVA til Skatteetaten.
- **A-melding:** månedlig rapportering av lønn og trekk.
- **SAF-T:** standardisert XML-format for regnskapsdata.
- **EHF:** norsk elektronisk fakturaformat basert på Peppol.
- **Peppol:** europeisk nettverk og standard for elektroniske dokumenter.
- **ELMA:** register over virksomheter som kan motta elektroniske dokumenter.
- **Altinn 3:** Skatteetatens og offentlig sektors meldingsplattform.
- **Aksjonærregisteroppgave:** rapportering av aksjeeiere og aksjetransaksjoner.
- **Årsregnskap:** resultat, balanse, kontantstrøm, egenkapital og noter.
- **Næringsspesifikasjon:** skjema som spesifiserer næringsinntekter og -kostnader.
- **NS 4102:** norsk standard kontoplan.
- **NBS 6:** bokføringsstandard for små virksomheter.
- **Tenant:** et isolert kundeforetak i en flerbrukerløsning.
- **Audit trail:** sporbar logg over hvem som gjorde hva og når.

### 13.4 Endringslogg

| Versjon | Dato | Endring |
|---|---|---|
| 0.1 | 11.11.2026 | Første prosjektplan med funnregister, arkitektur, UI-retning, faser, arbeidsmåte og beslutningslogg |

<!-- END -->
