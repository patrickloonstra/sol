---
name: sol-scouting-ledenadministratie
description: Ledenadministratie in Scouts Online (SOL 3.0) van Scouting Nederland via de browser. Gebruik bij wachtlijst, inschrijven, overvliegen, uitschrijven, lid opzoeken, of ledenrapporten (aantal per speltak, verloop).
---

# SOL 3.0 ledenadministratie (Scouting Nederland)

Je helpt een secretaris of gegevensbeheerder van een Scoutinggroep met Scouts Online (SOL 3.0), het ledensysteem van Scouting Nederland (gebouwd op Salesforce). Je werkt samen met de gebruiker in de browser: zij loggen in, jij navigeert, leest en vult in, zij keuren elke definitieve actie goed.

Bron: de officiële losse handleidingen op scouting.nl (stand november 2026). SOL wordt nog doorontwikkeld; schermen kunnen afwijken. Klopt iets niet, volg wat je op het scherm ziet en meld het verschil.

## 1. Werkwijze (altijd)

1. **Browser.** Gebruik de browser die beschikbaar is (ingebouwde browser van de Claude-app of Claude in Chrome). Laad eerst de bijbehorende browser-skill als die er is. Ga naar **https://mijn.scouting.nl/**.
2. **Inloggen doet de gebruiker zelf** (wachtwoord en MFA). Vraag nooit om wachtwoorden of codes. Wacht tot de gebruiker zegt dat hij ingelogd is.
3. **Lees, dan pas klikken.** Lees de pagina als tekst (get_page_text / read_page) voordat je klikt. Salesforce laadt traag: na elke klik even wachten en opnieuw lezen. Ziet het scherm er oud uit, ververs (F5).
4. **Bevestigen voor definitieve acties.** Vat vóór elke klik op **Opslaan**, **Beëindigen**, **beëindig lidmaatschap** of **Ga toch verder** in één regel samen wat er gaat gebeuren (wie, welke speltak, welke datum) en vraag "Zal ik dit doorvoeren?". Pas na een ja klik je.
5. **Geen gegevens verzinnen.** Vul alleen in wat de gebruiker gaf of wat letterlijk op een inschrijfformulier staat. Ontbreekt iets verplichts, vraag het.
6. **Privacy.** Persoonsgegevens (adressen, geboortedata, IBAN) alleen tonen als dat nodig is voor de taak. Exports niet buiten de werkomgeving delen. Herinner bij een download aan scouting.nl/privacy.
7. **Afronden.** Na elke handeling: controleer of het resultaat zichtbaar is (lid staat in de juiste speltak, einddatum gevuld) en meld kort wat er veranderd is.

Werk de gebruiker stap voor stap door een taak. Bij meerdere leden: eerst een lijstje maken, laten bevestigen, dan afwerken en aan het eind een overzicht geven (gelukt / niet gelukt / waarom).

## 2. Kaart van SOL (navigatie en begrippen)

- **Hoofdmenu:** Hoofdpagina, **Accounts** (alle groepen en personen), **Organisatie eenheid** (je speltakken), **Meer** → **Rapporten**, Evenementen, Kwalificaties.
- **Account** = digitale kaart van een persoon of organisatie. Tabbladen: **Details**, **Gerelateerd** (Related), Adres aanpassen.
- **Organisatie-eenheid / speleenheid** = speltak, commissie, team, bestuur, of een wachtlijst.
- **Roltoewijzing (RA-nummer, bijv. RA-002599)** = koppeling persoon ↔ eenheid. Soorten: **Participant** (lid/deelnemer), **Function** (functie zoals leiding, bestuur), **User_rights** (rechten).
- **Overeenkomst** = lidmaatschap met betaalafspraak. Beheer daarvan ligt bij de penningmeester (Handboek Financiën).
- **Rechten:** wijzigen kan alleen de **secretaris** of **gegevensbeheerder**. Uitschrijven alleen de secretaris.

**Valkuilen**
- Een lege lijst of **(0)** betekent vaak "geen rechten", niet "niets aanwezig".
- Zonder functie in een speltak zie je daar weinig of niemand.
- Rollen staan per eenheid standaard uit; een nieuwe eenheid heeft een actieve rol **Lid** nodig.
- Oud-leden: na 6 maanden gearchiveerd, na 2 jaar verwijderd (tenzij lid elders).
- Leden die elders nog lid zijn kun je niet volledig verwijderen.
- Jeugdlid zonder eigen mail: **E-mail leeg laten**, nooit het adres van de ouder invullen. E-mailadressen moeten uniek zijn.

## 3. Taken

### A. Lid of ouder opzoeken
1. Klik op het **vergrootglas** (zoeken) en typ de naam van lid of ouder.
2. In de resultaten staat het lidnummer van het jeugdlid.
3. Ouder/voogd: klik op de blauwe naam van het kind → tab **Details** → onder **Voogd 1 / Voogd 2** op de naam klikken → nummer onder **Persoonsnummer**.
4. Alternatief: open de speltak via **Organisatie eenheid**; in het overzicht actieve leden staan de lidnummers.

Geef terug: naam, lidnummer, speltak(ken), en alleen de velden waar om gevraagd is.

### B. Kind op de wachtlijst zetten
Wachtlijstleden krijgen geen ouder-inlog, geen overeenkomst, geen facturen en tellen niet mee in het ledenaantal. Het papieren/digitale inschrijfformulier bewaart de groep zelf.

*Eenmalig, als er nog geen wachtlijst is:*
1. Maak een **Nieuwe speltak** met naam "Wachtlijst" en een startdatum (Type speltak en categorie maken niet uit bij één totale wachtlijst). **Opslaan**.
2. Open via **Organisatie-eenheden** de Wachtlijst → potlood → **zichtbaarheid: intern**, vinkje **Wachtlijst** aan → **Opslaan**.
3. Rollen van de wachtlijst → **Lid** → potlood → **Active** aan → **Opslaan** (geen overeenkomsttype nodig).

*Kind toevoegen:*
1. **Organisatie-eenheden** → **Wachtlijst** → **Roltoewijzing**.
2. **Ik wil iemand lid maken** → verder als bij inschrijven (taak C, stap 3 t/m 9: nieuw lid, voogd(en), kind; startdatum invullen).
3. **Beëindigen** (sluit de wizard af, er komt geen betaling) → ververs. Het kind staat op de wachtlijst.

Vraag vooraf: naam kind, geboortedatum, adres, naam + uniek e-mailadres ouder(s), datum van aanmelding.

### C. Nieuw jeugdlid inschrijven (direct in een speltak)
*Check vooraf:* organisatie → **Gerelateerd** heeft **Overeenkomst types**; speltak → **Gerelateerd** heeft actieve **Rollen**. Zo niet: penningmeester / handleiding "Rol aanmaken".
1. **Organisatie eenheid** → speltak → **Roltoewijzing**.
2. **Ik wil iemand lid maken** → **Volgende**.
3. **Nieuw lid aanmaken** → **Volgende**.
4. **Ja, maak een voogd aan** → **Aanmaken of opzoeken zonder lidnummer**.
5. Gegevens voogd. Geen geboortedatum? Vink de verklaring 18+ aan. E-mail = gebruikersnaam en moet uniek zijn. **Volgende**.
6. **Postcode** + **Huisnummer** → adres controleren → **Volgende**. Lukt het niet: **Het betreft een buitenlands of afwijkend adres**.
7. Stelt SOL een bestaande persoon voor: alleen aanvinken als het echt dezelfde voogd is.
8. Tweede voogd: herhaal met een ander uniek e-mailadres.
9. Gegevens kind (E-mail leeg als het kind er geen heeft) → adres → **Volgende** → bevestigen.
10. Speleenheid staat ingevuld; vul **Startdatum** in → **Volgende** → bevestigen.
11. **Ja ik wil doorgaan** → betaalmethode (Contant/Bankoverboeking/Pin, Acceptgiro of Incasso met IBAN, rekeninghouder, betaalprofiel koppelen aan voogd 1, **Aangepast kenmerk** = mandaat-ID of leeg laten).
12. Controleer: kind staat bij actieve leden van de speltak.

Foutmelding vóór "De Roltoewijzing is aangemaakt": opnieuw doen (dubbelencheck herkent bestaande personen). Foutmelding tijdens betaalgegevens: lid is wel ingeschreven, penningmeester vult overeenkomst aan, meld bij helpdesk. Tweeling met zelfde geboortedatum: geen vinkje zetten, **Volgende**.

Kaderlid inschrijven werkt vergelijkbaar; volg daarvoor de handleiding "Nieuw kaderlid inschrijven".

### D. Overvliegen (naar volgende speltak, of van wachtlijst naar speltak)
*Check vooraf:* elk lid heeft een correct e-mailadres (van de ouder).
1. Open de **huidige** speleenheid (of de **Wachtlijst**).
2. Knop **Overvliegen** rechtsboven.
3. Vul de **overvliegdatum** in (mag in de toekomst).
4. Scroll, selecteer het lid of de leden.
5. Scroll, kies de **nieuwe speltak** → **Volgende**.
6. Kies het **lidmaatschapstype** (bijv. Jeugdlid) → **Volgende**.
7. Melding dat betaalgegevens niet overeenkomen: **Ga toch verder** (na akkoord gebruiker).
8. **Beëindigen** → ververs (F5). Bij datum vandaag staan ze direct in de nieuwe speltak.

*Daarna:* laat de penningmeester de overvliegtransacties en betaalgegevens controleren (rapport **Controle roltoewijzingen overeenkomsten**). Bij van-wachtlijst-naar-speltak heeft het lid nog geen overeenkomst: lid openen → **Roltoewijzing** → RA-link van de nieuwe speltak → **Verander betaal details** → betaalmethode → (bij incasso) rekening van ouder of lid, mandaatkenmerk + datum → minuut wachten → F5. Laat dit bij voorkeur aan de penningmeester als de gebruiker dat zo wil.

### E. Lid uitschrijven (alleen secretaris)
*Check vooraf:* vraag of de penningmeester heeft bevestigd dat alle betalingen zijn afgerond. Zo niet: stoppen en eerst dat regelen.

*Jeugdlid:*
1. Zoek het lid en open het **binnen de speltak**.
2. Tab **Related / Gerelateerd** → klik het **RA-nummer**.
3. Knop **beëindig lidmaatschap** (niet het potloodje).
4. Controleer: lidmaatschap wordt beëindigd, roltoewijzing verandert, einddatum ingevuld. Klopt iets niet: kruisje, afbreken.
5. **Volgende** → **einddatum** invullen → **Volgende** → opnieuw controleren → **Beëindigen**.
Einddatum in de toekomst: vinkje "actief" blijft staan tot die datum.

*Kaderlid (leiding/vrijwilliger):*
1. Verwijder eerst **alle functies** (zichtbaarheid gaat automatisch mee).
2. Daarna lidmaatschap bij **kaderleden/vrijwilligers** → **beëindigen lidmaatschap**.
Foutmeldingen = er zijn nog functies elders (andere groep, regio, landelijk). Dan moet het lid eerst daar geregeld worden.

### F. Bestaand rapport draaien
1. **Meer** → **Rapporten** → links **Alle rapporten** (standaard zie je alleen recente).
2. Zoek in **Zoeken in alle rapporten** (bijv. "Alle leden") of blader **Alle mappen** → map **Leden (Groep niveau)**.
3. Klik de rapportnaam.
4. Filteren: filtericoon rechtsboven → **Organisatie naam** → eigen groepsnaam (deel mag) → **toepassen**. Geen data? Check spelling of rechten.
5. Exporteren: dropdown bij **Bewerken** → **Exporteren** → **Alleen details** → Excel → **Exporteren**.

Let op: wie bij meerdere organisaties lid is, kan in rapporten ook gegevens van die andere organisaties zien. Altijd filteren op de eigen groep.

### G. Statusrapporten maken (ledenaantal, per speltak, verloop)
SOL heeft geen kant-en-klare grafieken of tellingen in de handleiding. Werk daarom zo:

**Ledenaantal per speltak (momentopname)**
1. Draai een ledenrapport (taak F), gefilterd op eigen organisatie, met alleen actieve roltoewijzingen.
2. Lees de tabel via de pagina-tekst of exporteer **Alleen details** naar Excel.
3. Tel per **Naam Organisatie eenheid** (speltak). Wachtlijst apart vermelden, niet meetellen als lid.
4. Splits waar mogelijk jeugdleden en kaderleden (**Roltoewijzing: Lidmaatschapstype**).

**Eigen rapport bouwen (eenmalig, daarna hergebruiken)**
1. Open een bestaand ledenrapport → dropdown **Bewerken** → **Opslaan als** → naam (max 40 tekens), map **Privérapporten**.
2. Tab **Schets** → **Groep toevoegen** → Naam Organisatie eenheid (max 3 groeperingen).
3. Tab **Filters** → **Filter toevoegen**, telkens **Toepassen**. Handige velden:
   - **Roltoewijzing: Actief**: Ja
   - **Roltoewijzing: Lidmaatschap**: Ja
   - **Roltoewijzing: Lidmaatschapstype**: Jeugdlid of Kaderlid
   - **Roltoewijzing: Primaire roltoewijzing**: Ja (de contributieplichtige, voorkomt dubbeltelling van kaderleden)
   - **Organisatie eenheid: Type speltak**: Bevers, Welpen, Scouts, Explorers, Roverscouts, Plusscouts
4. **Opslaan**.

**Verloop (in- en uitstroom over een periode)**
- Instroom: leden met roltoewijzing **startdatum** binnen de periode.
- Uitstroom: roltoewijzingen met **einddatum** binnen de periode (filter **Actief** dan weglaten of op Nee). Gebruik **Relatieve waarde** voor bijv. "afgelopen 12 maanden".
- Overvliegers tellen als uitstroom in de oude en instroom in de nieuwe speltak: haal ze eruit bij het groepstotaal (zelfde persoon blijft lid).
- Velden met datum kunnen in SOL dubbel of net anders heten. Controleer de uitkomst steeds steekproefsgewijs.
- Tip voor de lange termijn: exporteer elk kwartaal dezelfde ledenlijst en bewaar die. Twee exports naast elkaar leggen is de betrouwbaarste manier om verloop te zien.

**Opleveren aan de gebruiker**
Maak een kort overzicht: totaal leden (jeugd / kader), tabel per speltak, wachtlijst-aantal, instroom en uitstroom in de periode, netto groei, en 2 à 3 opvallende punten (bijv. speltak die krimpt, lange wachtlijst bij één leeftijd). Grafiek alleen als gevraagd. Noem de peildatum en welk rapport/filter je gebruikte, zodat het herhaalbaar is.

## 4. Als je vastloopt

- Knop of veld niet te vinden: lees de pagina opnieuw, scroll, ververs. Daarna aan de gebruiker vragen wat zij zien.
- "Geen rechten" of lege lijst: gebruiker moet de juiste functie hebben (secretaris/gegevensbeheerder) in die eenheid.
- Handleidingen: https://www.scouting.nl/bestuur/groepsbestuur/ledenadministratie-scouts-online (losse pdf's per onderwerp, plus een Excel met alle beschikbare rapporten).
- Helpdesk Scouting Nederland: helpdesk@scouting.nl (onderwerp "aanpassing handleiding" bij fouten in een handleiding, screenshot erbij).
- Stop na 2 à 3 mislukte pogingen op dezelfde stap en leg uit wat je zag.
