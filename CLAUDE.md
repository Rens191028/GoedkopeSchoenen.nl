# GoedkopeSchoenen.com — Website-vernieuwing

Dit document bevat alle beslissingen en richtlijnen voor de vernieuwing van goedkopeschoenen.com,
zodat Claude (of elke ontwikkelaar) consistent kan bouwen zonder dat context verloren gaat.
Plaats dit bestand als `CLAUDE.md` in de root van het project.

## 1. Project in het kort

- **Winkel**: Shopify-webshop, 750 producten (de hoofdcollectie "Alle Goedkope Schoenen" bevat er 499)
- **Doelgroep**: vooral dames; schoenen, tassen en accessoires, prijsklasse €8,99–€90
- **Positionering**: toegankelijk en vriendelijk, maar met een premium uitstraling
- **Referentiemerk**: Adidas — strak, grijs/zwart, met één doordachte accentkleur
- **Scope van dit traject**: volledige vernieuwing — huisstijl, logo, homepage, navigatie,
  productpagina's, animaties

## 2. Echte bedrijfsgegevens (geverifieerd op de huidige site)

Gebruik deze gegevens overal waar de site bedrijfsinformatie toont (footer, contactpagina,
vertrouwenssectie, structured data):

- **Bedrijfsnaam**: GoedkopeSchoenen.com
- **Adres**: Taminiausingel 15, 6662MD Elst
- **KvK-nummer**: 84772018
- **BTW-nummer**: NL863360324B01
- **Telefoon**: 06-19671591
- **E-mail**: info@goedkopeschoenen.com
- **Achtergrond**: opgericht in 2012, begonnen op beurzen (Huishoudbeurs, Libelle Zomerweek,
  Margriet Winterfair) en vanuit een garage; in 2023 samengevoegd met de voormalige
  tassenwebshop Goedkope-tassen.com tot één site

> Kiyoh-score (9,3 / 6.531 beoordelingen) en de huidige USP's (same-day verzending, Klarna,
> gratis verzending vanaf €65) zijn gebaseerd op eerdere analyse van de live site — controleer
> deze cijfers bij livegang, ze kunnen inmiddels gewijzigd zijn.

## 3. Huisstijl en merkidentiteit

### Logo
- Los icoon/symbool **plus** de volledige naam ernaast (geen afkorting)
- Icoon: abstracte "speed stripes" — drie diagonale, afgeronde balken van aflopende lengte,
  de kortste (bovenste) in de accentkleur, de andere twee in het donkere basiszwart
- Strak en modern, geen letterlijke schoen-vorm (te cliché)
- Icoon moet los bruikbaar zijn: favicon, social media, tags
- Logo-typografie bouwt voort op de kop-typografie, zodat logo en site visueel één merk vormen
  (dit loste het probleem op dat het oude logo en de hero als twee verschillende merken aanvoelden)

### Kleuren
| Token | Hex | Gebruik |
|---|---|---|
| `--color-bg` | `#FAFAF8` | Hoofdachtergrond |
| `--color-surface-alt` | `#F0EEE8` | Kaarten, badges, subtiele vlakken |
| `--color-text-primary` | `#141413` | Koppen, hoofdtekst, logo |
| `--color-text-secondary` | `#5B5953` / `#8C8679` | Subtekst, labels |
| `--color-border` | `#E4E1D9` / `#EAE7E0` | Randen, scheidingslijnen |
| `--color-accent` | `#B5582E` | Terracotta/roestbruin — **spaarzaam**: CTA-knoppen, sale-badges, highlights |
| `--color-accent-hover` | `#99471F` | Hover-state van de accentkleur |

**Regel**: basis is grijs/zwart/wit. De accentkleur wordt bewust spaarzaam ingezet (CTA's,
badges, belangrijke highlights) — niet als decoratie door de hele pagina heen. Geen felle of
drukke kleuren.

### Typografie
- **Koppen**: Archivo (geometrisch, zelfverzekerd, 700–800) — alternatief: Poppins
- **Body/productinfo**: Inter (400–600) — alternatief: Public Sans
- Google Fonts: `Archivo:wght@600;700;800` + `Inter:wght@400;500;600;700`

### Sfeer en layout
- Rustige, overzichtelijke pagina's met voldoende witruimte
- Referentie voor structuur: groot fotografie-gebruik, rustige grid (zwart-wit portfolio-stijl)
- Productpagina-opzet: groot productbeeld, strak info-paneel, uitklapbare secties
  (Description/Delivery/Product Care)

## 4. Animaties en interactie

**Basisprincipe**: kort (200–400ms) en rustig — ondersteunt het premium/overzichtelijke gevoel,
leidt niet af. Nooit schokkerig of langdurig.

### Staggered entrance- en scroll-animaties
- Hero: kop, badge, subtekst, CTA's en trustbalk komen staggered in beeld bij het laden
  (`fadeUp`, ~560ms, oplopende delay per element van ~90ms)
- Productkaarten: lichte fade + schuif omhoog zodra ze in beeld scrollen
- Vertrouwenselementen (Kiyoh-score, stats): zelfde staggered-kaartje-effect

### Hover- en microinteracties
- Productkaarten: zachte schaal/lift + crossfade naar een tweede productfoto bij hover
- Primaire knoppen: subtiele kleurverdieping + pijl-icoon die iets naar rechts schuift
- Mega-menu: zacht in-/uitfaden (opacity + translateY), nooit abrupt tonen/verbergen

### 3D-elementen — bewust beperkt tot 1–2 plekken
- **Homepage-hero**: uitgelicht productvlak met 3D-tilt die meebeweegt met de muis
  (`perspective(900px)`, rotatie tot ±26° o.b.v. cursorpositie, met dynamische schaduw-diepte
  en twee zwevende infokaartjes die een lichte parallax meebewegen)
- **Productpagina** (nog te bouwen): 3D-rotatie/kanteling van het product bij hover of
  sleep-interactie
- Bewust niet overal toepassen — zo blijft de site overzichtelijk in plaats van druk

## 5. Homepage — opgebouwde onderdelen

Een eerste visueel ontwerp is uitgewerkt (zie het Design-artifact in het project). Onderdelen:

1. **Aankondigingsbalk**: donkere strip bovenaan met vriendelijke micro-copy + USP's
   ("Zoolblij met elke bestelling — gratis verzending vanaf €65 · achteraf betalen met Klarna")
2. **Header**: logo + icoon links, navigatie (Schoenen/Tassen/Accessoires/Sale) centraal,
   zoek/account/winkelwagen-iconen rechts
3. **Mega-menu** (bij "Schoenen"): 3 kolommen gegroepeerd per subthema
   (Sneakers / Laarzen & boots / Instappers & pantoffels) + een promo-blok met actuele actie
4. **Hero**: Kiyoh-badge, kop + subtekst, primaire + secundaire CTA, trustrij (verzending/Klarna/
   same-day), productvlak met 3D-tilt en twee zwevende infokaartjes
5. **USP-balk**: donkere band met 4 vertrouwenspunten
6. **Productgrid "Nieuw binnen"**: 4 productkaarten met badges (Nieuw/sale-% /Bestseller),
   van-voor-prijzen, hover-crossfade en "snel toevoegen"-knop
7. **Vertrouwenssectie**: grote Kiyoh-score met sterren, 3 reviewkaartjes, KvK/adres/btw-balk
   onderaan

### Responsive gedrag
- Hero-grid valt terug naar 1 kolom onder 860px, gecentreerd
- Mega-menu wordt verborgen onder 860px (hover werkt toch niet op touch — moet nog een
  mobiele menu-oplossing krijgen, bijv. accordion)
- Productgrid: 4 → 2 kolommen onder 860px → 1 kolom onder 560px
- Trust-sectie: 2 kolommen → 1 kolom onder 860px

## 6. Productpagina — huidige situatie (live site)

Geverifieerd op een echte productpagina: `/products/trendy-laarzen-met-slouchy-design-bruin`
(Trendy laarzen met slouchy design bruin, €39,99). Dit is de basis voor de nieuwe productpagina.

### Huidige opbouw
1. **Trustbalk boven**: Kiyoh-widget, "Op werkdagen voor 15:00 besteld: zelfde dag verzonden",
   "Achteraf betalen", bekendheid via beurzen/tijdschriften, gratis verzending vanaf €65
2. **Navigatie**: hoofdmenu (Goedkope Schoenen / Goedkope Tassen / Goedkope accessoires / Sale)
   met subcategorieën, promo-links ("Pantoffels 2 voor €24,99", "Boots festival 2 paar €50"),
   Contact/Retourportaal/Cadeaubon, social links (Facebook/Instagram/TikTok), skiplink
   "Meteen naar de content"
3. **Productgalerij**: 3 foto's, teller "1 / van 3", vergroot-knop "Media openen in modaal"
4. **Productkop en prijs**: titel, SKU (kleur+maatcode), prijsblok met labels "Normale prijs" /
   "Aanbiedingsprijs", btw-vermelding, "Aanbieding"-label, "Uitverkocht"-status
5. **Variantkeuzes**: kleur (bij dit product 1 optie), maatknoppen 36–41, elk met verborgen tekst
   "Variant uitverkocht of niet beschikbaar" voor toegankelijkheid
6. **Aankoopblok**: hoeveelheidsveld "Aantal (0 in winkelwagen)" met +/− knoppen, CTA
   "Aan winkelwagen toevoegen"
7. **Verzend-/servicekaarten**: levertermijn, PostNL + afhaalpunt-optie, verzendkosten
   (gratis vanaf €65, anders €5,99; sommige tassen €4,45), retourportaal-link, betaalmethoden
   (iDeal, Klarna, creditcard, Bancontact)
8. **Beschrijving en specificaties**: marketingtekst + concrete maten (bijv. "totale hoogte 28 cm
   incl. hak van 7 cm, schachtwijdte 40 cm bij maat 39")
9. **Delen**: "Link kopiëren", link "Alle details bekijken"
10. **Reviews en cross-sell**: Kiyoh-slider zonder zichtbare reviewteksten; **geen** gerelateerde
    producten of "Vaak samen gekocht"-sectie
11. **Footer**: klantenservicelinks, nieuwsbrief ("10% korting op je eerste aankoop"), landkeuze
    (BE/DE/NL, EUR), beleidspagina's

### Wat behouden moet blijven
- Verzend-/retour-/betaalkaarten direct naast de aankoopknop (PostNL, iDeal/Klarna/creditcard/
  Bancontact) — functioneel sterk
- Maatkeuze als knoppen met duidelijke uitverkocht-status per variant
- Concrete specificaties (hoogte, hakhoogte, schachtwijdte) — relevant voor een schoenenwebshop
- Deel-functie

### Wat moet verbeteren in het nieuwe ontwerp
- **Prijsblok**: toont nu altijd zowel "Normale prijs" als "Aanbiedingsprijs", ook als beide
  hetzelfde bedrag zijn (geen echte korting) — verwarrend. Nieuw: toon alleen een
  doorgestreepte van-prijs wanneer er daadwerkelijk korting is
- **Reviews ontbreken inhoudelijk**: alleen een lege Kiyoh-slider, geen reviewteksten zichtbaar
  op de productpagina zelf — mist het vertrouwenssignaal dat elders (9,3 Kiyoh-score) sterk is.
  Nieuw: zichtbare reviewcitaten met naam en sterrenscore, zoals in de vertrouwenssectie op de
  homepage
- **Geen cross-sell/upsell**: geen "Vaak samen gekocht" of gerelateerde producten, terwijl de
  winkelwagen-drawer dit patroon elders al goed doet (cross-sell met kleur-/maatkeuze direct
  toevoegbaar). Nieuw: "Vaak samen gekocht" of "Dit vind je misschien ook leuk"-sectie onderaan
- **Tegenstrijdige levertijd-copy**: bovenbalk zegt "zelfde dag verzonden", servicekaart zegt
  "morgen in huis" — op elkaar afstemmen tot één consistente belofte
- **Geen zoom/360°-weergave** van het product — i.c.m. de besproken 3D-tilt/rotatie-interactie
  een kans om het product beter te laten zien dan nu

### Richting voor het nieuwe ontwerp
- Groot productbeeld met 3D-tilt/rotatie-interactie bij hover (zie sectie 4, 3D-elementen)
- Strak info-paneel ernaast: titel, prijs (met correcte van-voor-logica), maatknoppen, CTA
- Verzend-/retour-/betaalkaarten behouden, visueel in de nieuwe huisstijl
- Uitklapbare secties voor Beschrijving / Specificaties / Verzending & retour (i.p.v. alles
  los onder elkaar)
- Zichtbare reviewsectie met echte citaten (niet alleen een widget)
- "Vaak samen gekocht" / gerelateerde producten-sectie onderaan, voor de footer
- Consistente levertijd-copy door de hele pagina (en bij voorkeur site-breed)

## 7. Nog openstaand / vervolgstappen

Uit het oorspronkelijke verbeterplan, nog niet uitgewerkt in ontwerp:

- **Productpagina**: groot productbeeld, strak info-paneel, uitklapbare secties, 3D-productrotatie
- **Mobiele mega-menu-oplossing** (accordion i.p.v. hover-dropdown)
- **Echte productfotografie** i.p.v. placeholders in hero en productkaarten
- **Echte reviewcitaten en klantnamen** i.p.v. placeholders in de vertrouwenssectie
- **Kleurfilter normaliseren** op de collectiepagina (dubbele "Bruin"/"bruin"-varianten — datahygiëne,
  geen ontwerpwijziging)
- **Social media-links corrigeren** (Facebook verwees naar oude merknaam "mijnschoenenshop.nl")
- **Accessoires-tegel** toevoegen aan de Assortiment-sectie op de homepage

## 8. Technische context

- Huidige site draait op **Shopify** — implementatie van het nieuwe ontwerp gebeurt dus in een
  Shopify-thema (Liquid + CSS + JS), niet als losstaande webapp
- Bestaande sterke punten om te behouden: winkelwagen-drawer met gratis-verzendingbalk en
  cross-sell met variantkeuze, Sale-collectie badge/van-voor-prijs-patroon (als basis voor het
  patroon dat nu overal wordt doorgevoerd)
