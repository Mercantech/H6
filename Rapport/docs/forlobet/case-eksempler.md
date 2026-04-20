# Case-eksempler (inspiration til egen case)

Nedenfor finder du **fire fiktive casebeskrivelser** skrevet i samme struktur, som I typisk bruger til svendeprøven: baggrund, **Formål**, **Mål**, funktionsliste og **Brugerroller**. De er tænkt som **inspiration** — ikke som officielle krav fra Mercantec.

!!! warning "Disclaimer"

    **Fiktive kunder og krav.** Teksterne er eksempler til undervisning. De udgør ikke finansiel, juridisk eller sikkerhedsmæssig rådgivning. Ved integrationer (GitHub, markedsdata osv.) skal I følge leverandørens vilkår, håndtere **API-nøgler** sikkert og overholde **persondatalovgivning**. Cases med **CV, ansøgning og chat** (fx FindEnElev) kræver særligt fokus på **samtykke**, **sikker filopbevaring** og **sletning** — dokumentér jeres valg i produktrapporten.

    **Omfang:** Forløbet er ca. **25 arbejdsdage** med aflevering omkring **dag 20**. Hver case har en **MVP-afgrænsning** — prioriter et gennemgående kerne-flow frem for at nå «alt».

---

## KodeLab – træningsplatform for programmeringsopgaver

**Skrevet af:** [Elevnavne – eksempel]

**KodeLab A/S** vil tilbyde en webplatform, hvor brugere kan **øve sig på programmeringsopgaver** i ét eller flere sprog (fx **C#**, men platformen skal kunne udvides til andre sprog). Virksomheden mangler i dag ét samlet sted, hvor opgaver, afleveringer og fremdrift hænger sammen — og hvor mere øvede brugere kan koble deres **GitHub-konto** for at synkronisere eller dokumentere deres arbejde.

### Formål

At udvikle en **brugervenlig** platform, hvor man kan løse opgaver trin for trin, se sin **historik** og — hvor det er muligt — få **automatisk feedback**. Systemet skal understøtte **brugeroprettelse** og **OAuth-login via GitHub** (enten som primært login eller som tilkobling til en eksisterende konto — jeres valg skal dokumenteres). Der skal være **integration mod GitHub** i begrænset omfang i første version (fx oprettelse/listing af **gist**, visning af **ét linket repo** eller **seneste commit** på et valgt repo).

### Mål

At levere en **første produktionsklar iteration (MVP)** inden for et **kort forløb** (~20 arbejdsdage til kerneleverance), som demonstrerer: sikker brugerhåndtering, opgaveflow, lagring af **tidligere kodeforsøg** (kode, tidspunkt, status), og mindst **én konkret GitHub-funktion** plus **GitHub OAuth**. Løsningen skal være **nem at udvide** med flere opgaver, sprog og testtyper.

Systemet skal indeholde funktioner som:

- **Opgavekatalog** med beskrivelse, **startkode** og evt. hints.
- **Afprøvning / aflevering** af løsning (automatisk test hvor muligt; ellers tydelig manuel eller simplificeret validering — beskriv i rapporten).
- **Historik** over tidligere forsøg pr. bruger og pr. opgave.
- **Brugeroprettelse**, login og profil.
- **OAuth mod GitHub** og **API-integration** mod GitHub i aftalt, afgrænset scope.
- **Instruktør-/admin-del** til at oprette og vedligeholde opgaver (minimum: opret/redigér/slet i MVP).

### MVP (~20 dage) — afgrænsning

Vælg **ét sprog** til at gå i dybden først. **Én** GitHub-feature i MVP (ikke fuld «GitHub-klon»). Auto-test kan være **få tests** eller midlertidig manuel godkendelse — vigtigst er et **sammenhængende flow** og dokumentation af begrænsninger.

### Brugerroller

**Bruger**

- Oprette konto og logge ind (inkl. OAuth via GitHub efter valgt model).
- Løse opgaver, aflevere og se **egen historik**.
- Koble eller bruge GitHub-integration inden for det understøttede omfang.

**Instruktør**

- Oprette, redigere og deaktivere **opgaver** og tilhørende materiale.
- Se oversigt over afleveringer (valgfrit: kun aggregeret i MVP).

**Administrator** *(kan slås sammen med Instruktør i en meget lille MVP)*

- Håndtere brugere med ekstra rettigheder (instruktører).
- Overvåge systemindstillinger for GitHub-app / nøgler (kun på konceptniveau i case — implementér sikkert i praksis).

---

## PorteføljePulse – investeringsoversigt

**Skrevet af:** [Elevnavne – eksempel]

**PorteføljePulse** er en fiktiv virksomhed, der vil bygge en **app eller webapp**, så privatpersoner kan **overvåge en samlet portefølje** bestående af **aktier**, **kryptovaluta** og **metaller/mineraler** (eller tilsvarende råvarer). Brugeren registrerer selv sine positioner (fx købspris og antal); systemet henter **aktuelle kurser** fra **eksterne API’er** og viser værdi, udvikling og enkel oversigt.

### Formål

At udvikle en sikker løsning med **brugeroprettelse**, **egen portefølje** og **pålidelige eksterne kald** til prisdata. Systemet skal håndtere **rate limits** og **fejl** fra tredjeparter (fx caching, timeout, brugervenlig fejlbesked). Det skal være tydeligt i dokumentationen, at løsningen **ikke** er finansiel rådgivning og **ikke** udfører handel.

### Mål

At levere en **MVP** hvor brugeren kan se en **samlet oversigt** over registrerede aktiver fordelt på mindst **tre kategorier** (aktie, crypto, metal/mineral), med kurser fra **mindst tre typer datakilder** (kan være tre forskellige endpoints/leverandører). Løsningen skal kunne **udvides** med flere aktivtyper og notifikationer.

Systemet skal indeholde funktioner som:

- **Brugeroprettelse**, login og **flere porteføljer** eller gruppering af positioner (vælg en simpel model).
- **CRUD på positioner** (symbol/ID, antal, købspris, valuta, aktivtype).
- **Eksterne REST-kald** til priser for aktier, crypto og metaller/mineraler — med **cache** eller anden strategi mod overforbrug.
- **Dashboard**: samlet værdi, gevinst/tab siden køb (eller simpel afvigelse — definer i case).
- **Valgfrit:** simpel **alarm** (fx «under grænse») eller daglig snapshot til historik — kun hvis tiden rækker; ellers beskriv som fase 2.

### MVP (~20 dage) — afgrænsning

Gå **dybt på én aktivtype** og **lettere** på de to andre (fx manuel opdateringsknap eller færre felter), hvis nødvendigt. Ingen integration til **broker** eller **rigtig handel**. Dokumentér valg af API’er og begrænsninger (gratis nøgler, forsinkelse i data).

### Brugerroller

**Bruger**

- Administrere egen konto og **egne positioner**.
- Se dashboard og opdaterede kurser inden for systemets understøttede typer.

**Administrator** *(valgfri i MVP)*

- Vedligeholde globale indstillinger (fx standardvaluta, cache-tid).
- Eventuelt indlæse **demo-bruger** eller testdata til demonstration.

---

## DepotQR – udlån af udstyr (CRUD med twist)

**Skrevet af:** [Elevnavne – eksempel]

**DepotQR** leverer et system til et **værksted**, **makerspace** eller **undervisningssted**, hvor udstyr og værktøj **udlånes** og skal **spores**. Kernen er velkendt **CRUD** på udstyr og brugere — med et **twist**: hvert udlån knyttes til en **QR-kode** (eller unikt id), som scannes eller indtastes ved **udlevering** og **tilbagelevering**, så systemet automatisk fører **log med tidspunkt og bruger**.

### Formål

At gøre udlån **sporbart** og reducere manuelle lister. Systemet skal forhindre **dobbeltudlån** af samme genstand (forretningsregel). Brugergrænsefladen skal være enkel for den, der låner, og for **depotvagten**.

### Mål

At levere en **MVP** med komplet flow: registrere udstyr, oprette brugere, **udlåne** og **aflevere** med QR/id, samt vise **«hvem har hvad nu»** og **historik**. Løsningen skal være klar til udvidelse (fx påmindelser om forsinkede udlån).

Systemet skal indeholde funktioner som:

- **CRUD:** Udstyr (navn, kategori, status, **unikt QR/id**), brugere, samt **udlånstransaktioner**.
- **Scan/indtast** ved ud- og indlevering, der opdaterer status og **tidsstempler**.
- **Regel:** Kan ikke udlåne genstand, der allerede er **ude**.
- **Oversigt:** Aktive udlån og filter/søgning.
- **Historik:** Afsluttede udlån (hvem, hvad, hvornår).
- **Valgfrit:** Email eller intern påmindelse om forfald — fase 2 hvis tiden er knap.

### MVP (~20 dage) — afgrænsning

**QR** kan være et **genereret id** vist på skærm (udskrift er ikke et krav i casen). Fokusér på **korrekt domænelogik** og tydelig **datamodel** i rapporten.

### Brugerroller

**Låner**

- Se tilgængeligt udstyr (og evt. egen historik).
- Gennemføre udlån/tilbagelevering inden for depotets regler (selvbetjening eller via vagt — beskriv).

**Depotvagt / Administrator**

- Vedligeholde udstyr og brugere.
- Håndtere undtagelser (fx force-return i MVP kan udelades — dokumentér i stedet manuel proces).

---

## FindEnElev – platform for lærepladssøgende og virksomheder

**Skrevet af:** [Elevnavne – eksempel]

**FindEnElev** er en fiktiv **matchningsplatform** for **erhvervsuddannelse**: **elever uden læreplads** kan oprette en **offentlig profil** (online CV) og blive fundet af virksomheder; **virksomheder** (eller **elever med læreplads** som taler på vegne af en arbejdsplads) kan oprette sig for at **søge og rekruttere** nye elever. Målet er at samle **profil**, **dokumenter** og **første kontakt** ét sted — uden at erstatte formelle ansøgningsportaler hos uddannelsesinstitutioner, hvis I vælger at nævne det i jeres afgrænsning.

### Formål

At udvikle en **tryg og brugervenlig** webapp, hvor brugere kan oprette **to typer konti** (lærepladssøgende vs. rekrutterende part), vedligeholde en **profil med filer** (billede, CV, ansøgning, evt. andre bilag), **søge og filtrere** i modpartens profiler, og etablere **kontakt via chat**. Login skal understøtte mindst **OAuth via GitHub** samt **mindst én yderligere metode** (fx **e-mail + adgangskode**, **«Log ind med Google»** eller **«Log ind med Microsoft»** — vælg og dokumentér). Persondata og dokumenter skal behandles **hensigtsmæssigt** (krypteret lagring, adgangsstyring, mulighed for sletning — beskriv i rapporten).

### Mål

At levere en **MVP** hvor en lærepladssøgende kan **oprette profil**, **uploade materialer** og være synlig i en **søgbar oversigt**; en rekrutterende bruger kan **oprette virksomhedsprofil**, **gennemse kandidater** og **starte en samtale**. **Chat** skal fungere **real-time eller nær real-time** (fx polling i MVP er acceptabelt, hvis det begrænses og dokumenteres). Systemet skal kunne **udvides** med notifikationer, bedre matching og moderation.

Systemet skal indeholde funktioner som:

- **Registrering og roller:** Opret konto som **Lærepladssøgende** eller som **Rekrutterende** (virksomhed / «elev med læreplads» med tilknytning til arbejdsplads — vælg en tydelig datamodel).
- **Profil (lærepladssøgende):** Navn, kontakt (efter jeres privatløsning — fx kun gennem platform i MVP), **uddannelse/retning**, **kompetencer/nøgleord**, **kort præsentationstekst**, synlighed (offentlig / kun loggede brugere).
- **Profil (rekrutterende):** Virksomhedsnavn, beskrivelse, branche, geografisk område, evt. link til website.
- **Filupload:** Profilbillede (valideret type/størrelse), **CV** (fx PDF), **ansøgning/generel brev** og evt. **yderligere bilag**; liste over uploadede filer med mulighed for **download/sletning** for ejeren.
- **Søgning og filtre:** Fx uddannelse, område, nøgleord; oversigt med kortvisning af kandidater eller virksomheder.
- **Chat:** **1:1-tråde** mellem brugere der har «matchet» eller **anmodet om kontakt** (vælg en regel — fx kun chat efter accept af kontaktanmodning i MVP).
- **Login:** **GitHub OAuth** + **anden provider eller e-mail/login** som minimum.
- **Valgfrit (fase 2 eller hvis tid):** **E-mailnotifikation** ved ny besked; **rapportér bruger**; **admin-godkendelse** af virksomhedsprofiler; **read receipts**; integration til ekstern kalender.

### MVP (~20 dage) — afgrænsning

Prioritér **ét stærkt flow**: opret profil → upload → find modpart → chat. **Chat** kan i første omgang være **simpel** (kort beskedliste, manuel opdatering eller begrænset WebSocket). **Én** ekstra login-metode ud over GitHub er nok. Afgræns **filtyper og størrelse** skarpt. Dokumentér **GDPR-overvejelser** (formål, opbevaring, sletning) selv om I ikke implementerer fuld compliance i undervisnings-MVP.

### Brugerroller

**Lærepladssøgende**

- Oprette og redigere **egen profil** og **filer**.
- Søge i rekrutterende profiler og **starte/besvare chat** efter jeres kontaktregler.
- Logge ind med **GitHub** og/eller **anden valgt metode**.

**Rekrutterende** (virksomhed / elev med læreplads)

- Oprette og vedligeholde **virksomheds- eller arbejdspladsprofil**.
- Søge og filtrere **kandidater**, se profiler (inden for synlighedsregler) og **chatte**.
- Samme login-muligheder som øvrige brugere.

**Administrator** *(kan være minimal i MVP)*

- **Deaktivere** profiler eller brugere ved misbrug (simpel liste).
- Eventuelt se **aggregerede** statistikker (antal brugere, antal aktive samtaler) — uden at overvåge indhold, medmindre I eksplicit beskriver moderation.

---

## Sådan bruger I eksemplerne

- Brug strukturen (**Formål**, **Mål**, funktioner, **roller**) som skabelon til **jeres egen** case.
- Tilpas omfang til **jeres** team og **jeres** teknologistak.
- Aflevér **case** som en del af opgaven — se [Overblik](overblik.md) under *Hvad skal du aflevere?*
