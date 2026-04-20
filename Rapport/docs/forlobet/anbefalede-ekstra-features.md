# Anbefalede ekstra features

Her er **frivillige** temaer, der ofte **løfter indtrykket** af jeres produkt og dokumentation ved aflevering — især under delkarakteren **projekt / dokumentation**. Det er **ikke** en tjekliste I skal nå alt på; vælg det, der passer til jeres case, stack og de **~20 arbejdsdage** frem mod aflevering.

!!! note "Ikke officielle krav"

    Listen er **vejledende** og udarbejdet til undervisning. Den erstatter ikke [formelle krav](formelle-krav.md), jeres case eller underviserens aftaler. **Begrund altid valg og fravalg** i produktrapporten — det tæller mere end at nævne et buzzword.

!!! warning "Karakter"

    Ingen garanti for karakter. Censor vurderer **helheden** af produkt og dokumentation. Få områder gjort **grundigt og forklaret** slår mange halvt implementerede «features».

---

## Autentifikation og sikkerhed

**JWT (access + refresh)**

- **Access-token** med **kort levetid**; **refresh-token** til fornyelse uden at brugeren logger ind hver gang.
- Beskriv **hvor** refresh opbevares (fx **httpOnly cookie** vs. andre modeller) og **trade-offs** (XSS, CSRF, mobil/web).

**Asymmetrisk signering**

- Fx **RS256** med **nøglepar** (eller tilsvarende) frem for kun én symmetrisk hemmelighed — vis forståelse for **signering/verifikation** og evt. **JWKS**-idéen i dokumentationen.

**OAuth 2.0 / OpenID Connect**

- Login eller konto-link via **Google**, **Discord** og/eller **GitHub** (vælg det der giver mening; **én** velintegreret provider slår tre overfladiske).
- Dokumentér **redirect URI'er**, **scopes** og hvordan I håndterer **bruger-id** og **session**.

**Grundlæggende sikkerhed**

- **Validering** af input på serveren; **rate limiting** på login og følsomme endpoints.
- **Secrets** kun via miljøvariabler eller secret store — **aldrig** i Git.

---

## Test

**Unit tests**

- Især **domænelogik** og services uden netværk/database — hurtige og stabile.

**Integration tests**

- Fx **API** mod **rigtig eller containeriseret database**; autentificerede routes hvor det er kernen i produktet.

**E2E tests**

- Fx **Playwright** eller **Cypress** mod **ét eller to kritiske brugerflows** (login, kerneforretning). I en kort iteration rækker få, velvalgte flows.

**Tip:** Beskriv **testpyramiden** kort i rapporten — hvad I prioriterer, og hvorfor.

---

## Arkitektur og data

**Begrundet arkitektur**

- Vælg **én** hovedretning og forklar den i forhold til jeres case — fx:

    - **Vertical slices** (feature-mapper: UI + API + domæne samlet pr. feature).
    - **Onion / Clean Architecture** (domæne inderst, afhængigheder peger indad).
    - **Domænedrevet** skæring (aggregates, begreber, begrænset kontekst i **lille** målestok).

- Undgå at blande tre halve tilgange uden at forklare det.

**Database**

- **Normaliseret** model (**1NF–3NF** hvor det giver mening), tydelige relationer og begrænsede «alt-i-én»-kolonner.
- Nævn **hvornår** I bevidst **denormaliserer** (fx læseoptimering) — hvis I gør det.

**API og skema**

- **OpenAPI/Swagger** (eller tilsvarende) som kontrakt for jeres backend — hjælper både jer og censoren.

**Versionering af database**

- **Migrationer** (fx EF Core, Flyway, Liquibase) frem for manuelle SQL-ændringer uden historik.

---

## Drift, kvalitet og leverance

**Logging**

- **Struktureret** logging (niveauer, tidspunkt, besked), gerne **correlation-** eller **request-id** på tværs af kald.
- **Ingen** adgangskoder, tokens eller personfølsomme data i logfiler.

**CI**

- Fx **GitHub Actions**: **build**, **test**, **lint** ved push/PR — viser disciplin og gør aflevering mere reproducerbar.

**Containere og README**

- **Docker** / **Docker Compose** så projektet kan køres lokalt med få kommandoer.
- **README**: opsætning, miljøvariabler, hvordan man kører **tests**, link til rapport.

**Observabilitet (valgfrit)**

- **Health**- og **ready**-endpoints hvis I deployer til et miljø hvor det giver mening.

---

## Flere idéer der ofte gør godt

- **Tilgængelighed**: semantisk HTML, tastaturnavigation, rimelig kontrast.
- **Responsiv** UI hvis produktet er web.
- **Kort arkitekturdiagram** (fx C4-niveau 1–2 eller ét velvalgt diagram).
- **Kort UX-refleksion** eller brugertest — ikke obligatorisk, men styrker dokumentationen.
- **Concurrency** (hvis relevant): forståelse for **race conditions** ved samtidige opdateringer — dokumentér strategi (transaction, optimistic locking, osv.).

---

## Prioritering (~20 dage)

1. **Kerneproduktet** og en **sammenhængende** dokumentation slår «ekstra» der ikke fungerer.
2. Vælg **2–4 spor** fra siden (fx auth + integrationstests + migrationer + CI) og **dyk ned**.
3. Skriv **hvorfor** I valgte som I gjorde — det er kernen i den **faglige** vurdering.

Se også [Karakterer](karakterer.md) for hvordan delkaraktererne typisk fungerer.
