> [!WARNING] 
> ### LET OP: Deze RFC voegt de wijzigingen uit [RFC 24064](https://github.com/iStandaarden/iWlz_RequestForChange/issues/64) en [RFC 24080](https://github.com/iStandaarden/iWlz_RequestForChange/issues/80) samen tot één logisch wijzigingsverzoek. 
> 
> De impact op notificaties is beschreven in [RFC 24078](https://github.com/iStandaarden/iWlz_RequestForChange/issues/78) omdat deze specifiek gaat over het aanvullen van notificatietypen. Die RFC geeft daarmee een compleet overzicht met betrekking tot notificaties.  


### eDocs volgnummer

_No response_

### Korte probleem omschrijving

De vervaldatum is de datum waarop de rechtsgeldigheid van een indicatiebesluit vervalt als gevolg van de afgifte van een nieuw indicatiebesluit of het overlijden van de cliënt. De vervaldatum is de laatste dag waarop het indicatiebesluit nog geldig is.

Er zijn geen regels of afspraken die beschrijven hoe de vervaldatum gevuld moet worden als een indicatiebesluit vervalt omdat er een herindicatie met terugwerkende kracht wordt afgegeven.

Zorgkantoren willen graag weten wat de reden is van het vervallen van een indicatie. Dat is vooral van belang als de cliënt een pgb heeft.

### Korte omschrijving voorgestelde oplossing

Duidelijke regels voor het vullen van de vervaldatum, ook als deze met terugwerkende kracht wordt vastgesteld. Reden van het vervallen van een indicatiebesluit toevoegen. 

### RFC gevolgen voor het onderdeel/de onderdelen

ERD (Register), koppelvlak, regels, gegevens (nieuwe codelijst)


### Welk ander onderdeel?

Autorisatiematrix

### Betrokken partij RFC

CIZ

### Andere betrokken partij

_No response_

### Indiener RFC

Zorgkantoren

### Andere organisatie / contactpersoon

_No response_

# Analyse
### Huidige situatie
Op vervaldatum in WlzIndicatie zijn onderstaande regels van toepassing: 

- **IRB0032**: Het CIZ registreert een vervaldatum bij een indicatiebesluit als voor de client een nieuw indicatiebesluit is afgegeven of als de client is overleden.
_Documentatie:_ Na de vervaldatum is het indicatiebesluit niet meer rechtsgeldig.
- **IRG0030:** Vervaldatum vullen met een datum die kleiner is dan einddatum WlzIndicatie.
- **IRI0009:** Hoe wordt vervaldatum gevuld?
Als voor een client een nieuw indicatiebesluit is afgegeven vult het CIZ de vervaldatum met de datum van de dag voorafgaand aan de ingangsdatum van het nieuwe indicatiebesluit.  
Als de client is overleden, vult het CIZ de vervaldatum met de overlijdensdatum van de cliënt.  
Dit geldt voor alle besluiten van de client waarop nog geen vervaldatum is geregistreerd en waarbij de einddatum van de indicatie groter is dan de te vullen vervaldatum.

Het CIZ registreert een vervaldatum als:

1. de cliënt is overleden;
2. er een nieuw indicatiebesluit is afgegeven voor de cliënt;
    - ‘positief' besluit (herindicatie): de cliënt houdt recht op Wlz-zorg (zelfde of ander ZZP);
    - ‘negatief' besluit: de cliënt heeft geen recht meer op Wlz-zorg.

Bij de vervaldatum wordt geen reden opgenomen. Als er sprake is van een herindicatie, dan is niet duidelijk in welke regio de nieuwe indicatie is afgegeven.


### Bezwaren huidige situatie
Voor situaties waarin de vervaldatum met terugwerkende kracht gevuld moet worden geven de bestaande regels onvoldoende duidelijkheid of zijn ze zelfs niet toepasbaar. 
Daarnaast is het niet mogelijk
- om vast te leggen wanneer de vervaldatum is vastgesteld;
- om meer vervaldatums bij hetzelfde indicatiebesluit vast te leggen. 

**vaststellingsmoment**

Als een herindicatie met terugwerkende kracht wordt afgegeven, overlapt deze geheel of gedeeltelijk met de periode waarin de voorgaande indicatie geldig was. Op deze voorgaande indicatie, die met terugwerkende kracht een vervaldatum krijgt, is meestal zorg geleverd. Met terugwerkende kracht blijkt dan dat die indicatie vanaf de vervaldatum niet meer geldig was. Het is dan van belang om te weten wanneer de herindicatie is afgegeven. Dat is ook het moment waarop de vervaldatum is vastgesteld. Dat kan door bij de vervaldatum een vaststellingsmoment (datum en tijd) vast te leggen. 

**meer vervaldatums per besluit**

Als op een geldig indicatiebesluit een volgend, nieuw indicatiebesluit (of herindicatie) wordt afgegeven, wordt bij het vorige, 'oude' indicatiebesluit een vervaldatum ingevuld die gelijk is aan de dag voorafgaand aan de ingangsdatum van het nieuwe besluit. Deze systematiek geldt voor alle volgende besluiten (herindicaties) waarvan de ingangsdatum na de ingangsdatum van het vorige besluit ligt. Hiervoor is het voldoende dat er per indicatiebesluit één vervaldatum kan worden vastgelegd.

In de volgende situaties is één vervaldatum per besluit niet voldoende:
Als een derde of volgende indicatie een ingangsdatum heeft die vóór de ingangsdatum of vóór de vervaldatum van een of meer eerder afgegeven indicaties ligt, kan dat ertoe leiden dat er bij die betreffende eerder afgegeven indicaties een tweede (of volgende) vervaldatum moet worden vastgelegd. Deze situatie kan zich voordoen als er een herindicatie met terugwerkende kracht wordt afgegeven. Dan wordt niet alleen bij het vorige besluit een vervaldatum ingevuld, maar ook bij alle  eerder afgeven besluiten die op de ingangsdatum van het nieuwe besluit nog niet geldig waren of nog niet vervallen waren.
Een andere situatie waarin meer vervaldatums per besluit gevuld moeten kunnen worden: door de afgifte van een nieuw besluit is er al een vervaldatum ingevuld. Dan blijkt dat de cliënt voor de vervaldatum is overleden. Er moet dan een tweede, eerdere vervaldatum gevuld worden.

**achtergrond vervallen onbekend**

Het zorgkantoor weet alleen dát een indicatiebesluit vervallen is en niet waarom het besluit vervallen is. Zorgkantoren willen de reden van het vervallen van het indicatiebesluit weten omdat dit van belang kan zijn voor de uit te voeren vervolgacties. Dat is vooral het geval als de cliënt een pgb heeft. Als voor de cliënt een nieuw ‘positief’ indicatiebesluit is afgegeven is de werkwijze van het zorgkantoor anders dan wanneer er voor de cliënt een ‘negatief’ besluit is afgegeven of wanneer de cliënt is overleden.
Als er sprake is van een herindicatie wil het zorgkantoor weten in welke regio het nieuwe besluit is afgegeven.

# Wijzigingsvoorstel
### Voorstel aanpassing
1. Regels aanvullen en verduidelijken zodat ze ook toepasbaar zijn op situaties waarin een herindicatie met terugwerkende kracht wordt afgegeven. 
2. Mutatiedatum toevoegen bij vervaldatum. 
3. Mogelijk maken om meer vervaldatums bij hetzelfde indicatiebesluit vast te leggen.
4. Reden van het vervallen van een indicatiebesluit toevoegen. Hierdoor weet het zorgkantoor waarom het indicatiebesluit is vervallen en wat de vervolgacties moeten zijn. Daarnaast bij reden herindicatie toevoegen welk zorgkantoor de herindicatie ontvangen heeft. Hierdoor weet het zorgkantoor welk zorgkantoor het nieuwe verantwoordelijke zorgkantoor is.

**Voordelen**
- Het is duidelijk hoe de vervaldatum gevuld moet worden bij een herindicatie die met terugwerkende kracht wordt afgegeven.
- Het is mogelijk om na te gaan wanneer een vervaldatum is vastgesteld.
- Het is mogelijk om meer vervaldatums bij dezelfde indicatie vast te leggen.
- Het zorgkantoor weet waarom het indicatiebesluit is vervallen en kan aan de hand daarvan bepalen welke vervolgacties uitgevoerd moeten worden. Bij herindicatie weet het zorgkantoor wie het nieuwe verantwoordelijke zorgkantoor is.
N.B. dit gegeven kan in de toekomst ook van belang zijn voor de zorgaanbieder.  

**Nadelen**
Doorvoeren van wijzigingen nodig. 

# Uitwerking wijzigingsvoorstel per onderdeel
> [!IMPORTANT]
> **LET OP: RFC24080 bevat uitbreidingen op deze RFC** 
> 
> Ga voor voor de uiteindelijke situatie naar RFC24080 via #80 

- [Analyse](#analyse)
    - [Huidige situatie](#huidige-situatie)
    - [Bezwaren huidige situatie](#bezwaren-huidige-situatie)
- [Wijzigingsvoorstel](#wijzigingsvoorstel)
    - [Voorstel aanpassing](#voorstel-aanpassing)
- [Uitwerking wijzigingsvoorstel per onderdeel](#uitwerking-wijzigingsvoorstel-per-onderdeel)
  - [Wijzigingen ERD](#wijzigingen-erd)
  - [Wijzigingen GEGEVENS](#wijzigingen-gegevens)
  - [Wijzigingen REGELS](#wijzigingen-regels)
  - [Wijzigingen AUTORISATIEMATRIX:](#wijzigingen-autorisatiematrix)
  - [Wijzigingen NOTIFICATIE](#wijzigingen-notificatie)
  - [Wijzigingen PROCES](#wijzigingen-proces)
    - [Proces](#proces)
  - [Wijzigingen KOPPELVLAK](#wijzigingen-koppelvlak)
  - [Overweging](#overweging)
- [Overweging wijzigingsvoorstel(len)](#overweging-wijzigingsvoorstellen)


## Wijzigingen ERD

| **Mutatie** |  **Nieuwe situatie** |
| :--- | :--- | 
| Wijzigen |  `WlzIndicatie`: vervaldatum verwijderd |  
| Toevoegen |  `VervallenGeldigheid` toegevoegd (zie hieronder de samenstelling) |


**Toevoegen `VervallenGeldigheid`:**
| **Entiteit** | **Documentatie** |
| :-- | :--- |
| **`VervallenGeldigheid`** | Vervaldatum van het indicatiebesluit en de datum waarop de vervaldatum is vastgesteld. |

**Samenstelling `VervallenGeldigheid`:**

| **Element** | **ID** | **Verplicht** | **LDT** | **primitive** | **Codelijst** | **Documentatie** |  **Regel** | 
|:---|---|---|---|---|---|---|---|
| wlzIndicatieID | ja | ja | LDT_UUID | string | | Technische sleutel Entiteit .  |
| vervaldatum | ja | ja | LDT_UUID | string | |   |
| vaststellingmoment | ja | ja | LDT_DatumTijd | string | | 
| reden | nee | ja | LDT_RedenVervallenGeldigheidIndicatie | string | | Aanduiding van de reden voor het vervallen van de rechtsgeldigheid van het indicatiebesluit. | GGR0014 | 
| nieuwVerantwoordelijkZorgkantoor | nee | nee | LDT_ZorgkantoorCode | string | COD001 |Zorgkantoor dat bij de afgifte van een herindicatie op grond van het BRP-adres (of het verblijfadres) van de client het verantwoordelijke zorgkantoor is.| GGR0014 / IRG-XXX | 

![Image](https://github.com/user-attachments/assets/487d3419-83a2-41fb-95cf-74ddea4cfd91)

## Wijzigingen GEGEVENS
De volgende wijzigingen zijn nodig op de gegevens (datatypen en codelijsten)


| **Mutatie** | **type** | **Nieuwe situatie** |
| :--- | :--- | :-- |
| Toevoegen | Codelijst |  COD1005: Reden vervallen geldigheid Indicatie (zie hieronder voor samenstelling) |
| Toevoegen |  LDT |  `LDT_RedenVervallenGeldigheidIndicatie`  - string (zie documentatie bij codelijst) |


**Toevoegen Codelijst**
| **Codelijst** | **Documentatie** |
| :-- | :--- |
|  **COD1005: Reden vervallen geldigheid Indicatie** | Gecodeerde aanduidingen voor het aangeven van de reden voor het vervallen van de rechtsgeldigheid van het indicatiebesluit. | 

**Samenstelling `COD1005: Reden vervallen geldigheid Indicatie`**
  **Mutatie** | **Codelijst** | **Id** | **Omschrijving** | **ingangsdatum** | **expiratiedatum** | **mutatiedatum** | 
  |---|---|---|---|---|---|---|
  | toegevoegd | `COD1005` | 1 | herindicatie |  |  |   |
  | toegevoegd | `COD1005` | 2 | negatief indicatiebesluit |  |  |   |
  | toegevoegd | `COD1005` | 3 | cliënt is overleden |  |  |   |

## Wijzigingen REGELS
De volgende wijzigingen zijn nodig op de regels.

**Bedrijfsregels**

| **Bedrijfsregel** | **Mutatie** | **Oud** | **Nieuw** | **Opmerking** |
| :--- | :--- | :--- |  :--- | :-- |
| IRB0032 | Gewijzigd | IRB0032:  Het CIZ registreert een vervaldatum bij een indicatiebesluit als voor de client een nieuw indicatiebesluit is afgegeven of als de client is overleden. <br/><br/>_Documentatie:_ <br/>Het CIZ legt bij de vervaldatum ook het moment vast waarop deze vervaldatum is vastgesteld  <br/>Na de vervaldatum is het indicatiebesluit niet meer rechtsgeldig. | IRB0032:  Het CIZ registreert een vervaldatum bij een indicatiebesluit als voor de client een nieuw indicatiebesluit is afgegeven of als de client is overleden. <br/><br/>_Documentatie:_ <br/>Het CIZ legt bij de vervaldatum ook het moment vast waarop deze vervaldatum is vastgesteld _**en de reden waarom de de geldigheid van het indicatiebesluit is vervallen. Is herindicatie de reden van het vervallen van het besluit, dan registreert het CIZ ook welk zorgkantoor het nieuwe verantwoordelijke zorgkantoor is.**_ <br/>Na de vervaldatum is het indicatiebesluit niet meer rechtsgeldig. | aanvulling docmentatie |

**Gegevensregels**

| **Gegevensregel** | **Mutatie** | **Oud** | **Nieuw** | **Bedrijfsregel** | **Opmerking** |
| :--- | :--- | :--- |  :--- | :-- | :-- |
| IRG0030 | koppeling | IRG0030: Vervaldatum vullen met een datum die kleiner is dan einddatum WlzIndicatie. | koppeling aan vervaldatum | | 
| IRG0031 | nieuw |  | IRG0031: Vervaldatum vullen met een datum die kleiner is dan de eerder vastgelegde vervaldatum(s). | ? | |
| IRG0032 | nieuw |  | IRG0032: VaststellingMoment vullen met een datum en tijdstip die niet in de toekomst liggen. | ? |  (zie BRG0026, GGR van maken?)| 
| IRG-XXX | nieuw |  |  IRG-XXX: Als reden gevuld is met 1 (herindicatie), dan nieuwVerantwoordelijkZorgkantoor verplicht vullen, anders nieuwVerantwoordelijkZorgkantoor leeg laten. | n.b. werkelijk nummer bij publicatie |

**Autorisatieregels**

| **Autorisatieregel** | **Mutatie** | **Oud** | **Nieuw** | **Opmerking** |
| :--- | :--- | :--- |  :--- | :-- |
| ?? |  gewijzigd |  |  |  zie autorisatiematrix |

**Invulinstructies**

| **Invulinstructie** | **Mutatie** | **Oud** | **Nieuw** | **Opmerking** |
| :------------------ | :---------- | :------ | :-------- | :------------ |
| IRI0009 |  gewijzigd | IRI0009: Hoe wordt vervaldatum gevuld? <br/><br/>*Documentatie* <br/> Als voor een client een nieuw indicatiebesluit is afgegeven vult het CIZ de vervaldatum met de datum van de dag voorafgaand aan de ingangsdatum van het nieuwe indicatiebesluit. <br/> - Als de client is overleden, vult het CIZ de vervaldatum met de overlijdensdatum van de cliënt. <br/><br/> - Dit geldt voor alle besluiten van de client waarop nog geen vervaldatum is geregistreerd en waarbij de einddatum van de indicatie groter is dan de te vullen vervaldatum.        | IRI0009: Hoe wordt vervaldatum gevuld? <br/><br/>*Documentatie* <br/> Als voor een client een nieuw indicatiebesluit is afgegeven vult het CIZ de vervaldatum met de datum van de dag voorafgaand aan de ingangsdatum van het nieuwe indicatiebesluit. <br/> - **Dat is ook van toepassing als de ingangsdatum van het nieuwe indicatiebesluit in het verleden ligt. In dat geval is het mogelijk (en toegestaan) dat de vervaldatum vóór de ingangsdatum van het indicatiebesluit ligt.** <br/> - **Als op een tweede of volgende indicatiebesluit een herindicatie met terugwerkende kracht volgt, is het mogelijk dat bij een of meer voorgaande besluiten een tweede of volgende vervaldatum gevuld moet worden. Dat is alleen van toepassing als deze nieuwe vervaldatum vóór de eerder vastgelegde vervaldatum ligt.** <br/> - Als de client is overleden, vult het CIZ de vervaldatum met de overlijdensdatum van de cliënt.<br/> ~~Dit geldt voor alle besluiten van de client waarop nog geen vervaldatum is geregistreerd en waarbij de einddatum van de indicatie groter is dan de te vullen vervaldatum.~~<br/> - **De eerste vervaldatum die wordt vastgelegd bij een indicatiebesluit moet kleiner zijn dan de einddatum van dat besluit. Iedere volgende vervaldatum die wordt vastgelegd bij hetzelfde indicatiebesluit moet kleiner zijn dan de eerder bij dat besluit vastgelegde vervaldatum(s).** |               |


## Wijzigingen AUTORISATIEMATRIX: 
De volgende wijzigingen zijn nodig op de Autorisatiematrix.


| **Mutatie** |  **Nieuwe situatie** |
| :--- | :--- | 
| Toevoegen | Entiteit `VervallenGeldigheid` |
| Toevoegen | Elementen onder `VervallenGeldigheid`, markeren met R onder **welke regel?** |
| Verwijderen | `WlzIndicatie.vervaldatum`| 

<!-- er ontbreekt koppeling met een autorisatie regel voor de losse elementen-->

## Wijzigingen NOTIFICATIE
De volgende wijzigingen zijn nodig op de notificaties.

> [!NOTE]
> [RFC 24078 Aanvullen notificatietypen Indicatieregister voor wijzigen en verwijderen indicatie](https://github.com/iStandaarden/iWlz_RequestForChange/issues/78) geeft het complete overzicht aan wijzigingen van notificatietypen. 
>
> De gevolgen voor het notificeren uit deze RFC zijn daar beschreven. 



## Wijzigingen PROCES
De volgende wijzigingen zijn nodig op het proces.

### Proces
- Bij het vastleggen van een vervaldatum moet altijd gecontroleerd worden of er al eerder een vervaldatum voor hetzelfde besluit is vastgelegd. Alleen als de nieuwe vervaldatum kleiner is dan de eerder vastgelegde vervaldatum(s), wordt de nieuwe vervaldatum geregistreerd,
- Bij de vervaldatum legt het CIZ voortaan de reden van het vervallen van het indicatiebesluit vast. Dat is vooral van belang voor het pgb-proces. 
- Als herindicatie de reden is van het vervallen van de Wlz-indicatie, dan legt het CIZ ook vast welk zorgkantoor op grond van het BRP-adres van de cliënt het nieuwe verantwoordelijke zorgkantoor is. 
- Bij de vervaldatum hoort een vaststellingMoment.: datum en tijdstip waarop de vervaldatum is vastgesteld. Het vaststellingMoment hoort onlosmakelijk bij de vervaldatum en mag niet gewijzigd worden als bijvoorbeeld de reden of de zorgkantoorcode wordt gewijzigd. Om dat te voorkomen wordt vaststellingMoment opgenomen in de logische sleutel. 
 

## Wijzigingen KOPPELVLAK 

De volgende wijzigingen zijn nodig op het koppelvlak-schema

| **Mutatie** |  **Nieuwe situatie** |
| :--- | :--- | 
| Toevoegen |  type `VervallenGeldigheid`  |
| Wijzigen | @deprecated markeren `WlzIndicatie:vervaldatum` | 
| Wijzigen | `WlzIndicatie` aanvullen met edge Vervallengeldigeheid |

Uitbreiden met edge vanuit `WlzIndicatie`: 
```gql
vervallenGeldigheid: [VervallenGeldigheid!]
``` 

Toevoegen node: `VervallenGeldigheid`
```gql
type VervallenGeldigheid {
  vervallenGeldigheidID: UUID!
  vervaldatum: Date!
  vaststellingmoment: DateTime!
}
```

Deprecated markeren `vervaldatum`
```gql
  vervaldatum: Date @deprecated(
      reason: "vervangen door node VervallenGeldigheid"
    )
```

**Query-template**

Query: `QIR-0001-ZKi.graphql` aanpassen met verwijderen `vervaldatum` en aanvullen opvragen `VervallenGeldigheid`
```gql
        vervallenGeldigheid {
            vervallenGeldigheidID
            vervaldatum
            vaststellingmoment
        }
```


## Overweging
Doorvoeren voorgestelde wijziging van belang om herindicatie(s) met terugwerkende kracht te ondersteunen. 

# Overweging wijzigingsvoorstel(len)

| Oplossing     | Voordeel / Nadeel                | 
| :------------ | :------------------------------- | 
| 1. Voorgestelde wijzigingen doorvoeren         | Voordeel: het is mogelijk om herindicatie(s) die met terugwerkende kracht zijn afgegeven te ondersteunen.                       |                            
|               | Nadeel:    Het is noodzakelijk om wijzigingen door te voeren.                      |                            
| #. Niets doen | Voordeel: geen wijziging nodig   |                            
|               | Nadeel: probleem blijft aanwezig |                            





