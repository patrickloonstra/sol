# SOL-skill voor Claude: ledenadministratie zonder zoekwerk

**Je ledenadministratie in Scouts Online (SOL 3.0) op orde, zonder handleidingen door te spitten.**

SOL 3.0 doet wat het moet doen, maar de knoppen zitten niet altijd waar je ze verwacht. En de handleidingen zijn verspreid over een stapel losse pdf's. Deze skill bundelt al die stappen voor [Claude](https://claude.ai). Claude werkt met je mee in de browser: je zegt wat je wilt ("zet dit kind op de wachtlijst", "laat de welpen overvliegen", "hoeveel leden hebben we per speltak?") en Claude loopt de stappen met je door. Jij houdt de regie, Claude doet het zoekwerk.

Gemaakt door een secretaris, voor secretarissen en gegevensbeheerders van Scoutinggroepen.

> **Onofficieel.** Dit is een vrijwilligersinitiatief en geen product van Scouting Nederland. De stappen zijn gebaseerd op de officiële handleidingen op [scouting.nl](https://www.scouting.nl/bestuur/groepsbestuur/ledenadministratie-scouts-online) (stand november 2026). SOL wordt nog doorontwikkeld, dus schermen kunnen afwijken.

## Wat kan het?

- Lid of ouder opzoeken (lidnummer, persoonsnummer)
- Kind op de wachtlijst zetten (en zo nodig de wachtlijst inrichten)
- Nieuw jeugdlid inschrijven
- Overvliegen, ook van wachtlijst naar speltak
- Lid uitschrijven (jeugdlid en kaderlid)
- Rapporten draaien, filteren en exporteren
- Statusrapporten: ledenaantal per speltak, wachtlijst, in- en uitstroom

## Veiligheid

- **Je logt zelf in** (wachtwoord en MFA). Claude vraagt nooit om inloggegevens.
- **Claude vraagt bevestiging** vóór elke definitieve actie (Opslaan, Beëindigen, lidmaatschap beëindigen).
- Uitschrijven pas nadat de penningmeester heeft bevestigd dat betalingen rond zijn.
- Ga zorgvuldig om met persoonsgegevens en exports: zie [scouting.nl/privacy](https://www.scouting.nl/privacy).

## Installeren

**Claude-app (web of desktop)**
1. Download `sol-scouting-ledenadministratie.zip` via [Releases](https://github.com/patrickloonstra/sol/releases) (of zip zelf de map `sol-scouting-ledenadministratie`).
2. Ga in Claude naar de instellingen en zoek het onderdeel **Skills**. Upload daar de zip.
3. Gebruik de Claude-desktopapp met de ingebouwde browser of Claude in Chrome, zodat Claude in SOL kan meekijken en klikken.

**Claude Code**
```bash
git clone https://github.com/patrickloonstra/sol.git
cp -r sol/sol-scouting-ledenadministratie ~/.claude/skills/
```

## Gebruiken

Vraag bijvoorbeeld:
- "Zet Sanne de Vries op de wachtlijst" (geef de gegevens van het inschrijfformulier mee)
- "Laat de welpen die 11 zijn overvliegen naar de scouts per 1 september"
- "Schrijf lid 12345678 uit per 31 december"
- "Maak een overzicht van het aantal leden per speltak en de in- en uitstroom van het afgelopen jaar"

## Bijdragen

Klopt een stap niet meer omdat SOL is veranderd? Open een [issue](https://github.com/patrickloonstra/sol/issues) met wat je ziet (graag zonder persoonsgegevens in screenshots) of stuur een pull request. Fouten in de officiële handleidingen meld je bij helpdesk@scouting.nl.

## Licentie

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.nl): vrij te gebruiken, delen en aanpassen, ook door andere Scoutinggroepen, mits je de maker (Patrick Loonstra) vermeldt. Zie [LICENSE](LICENSE).
