CCS Relatieservice
====================


**Inhoudsopgave**
---------------------

- [Release notes](#header)
- [Algemene gegevens](#id-section1)
- [Service beschrijving](#id-section2)
- [Mapping](#id-section3)
- [Codelijsten](#id-section5)
- [Functies](#id-section4)
- [Voorbeeldberichten](#id-section6)

---------------------------------------

Release notes
---------------------


| Versie  | Datum | Beschrijving |Auteur|Bedrijf|
| ------------- | ------------- |||
| 1.02 | 01-01-2015 | Het toevoegen van de transactie en test|Nick van der Meij|Zeker.Me|


Algemene gegevens
---------------------


|Omschrijving  | Waarde |
| -------------|-------------|
|Doelsysteem|CCS Level7|
|Bronsysteem|Biztalk / AFD |
|Versie bronsysteem|1.02|
|Versie doelsysteem|8.3|
|Formaat|XML|
|Uitwisselingsprotocol | SOAP|
|Authenticatie | SOAP Header|
|Credentials | Bedrijf: zeker <br>Account: webser
|Adres testomgeving | https://www.vspbvfo.nl/ws_test/relatieservice.asmx |
|Adres acceptatieomgeving | https://www.vspbvfo.nl/ws_accp/relatieservice.asmx|
|Adres productieomgeving	| https://www.vspbvfo.nl/ws_prod/relatieservice.asmx|

Service beschrijving
---------------------
De Level7 relatieservice dient om een relatie aanmaken (create), muteren (update) en later ook verwijderen (delete)

Mapping
---------------------

|AFD Label|Codelijst|AFD Omschrijving  | Waarde Level7|Bijzonderheden
| ------------- | ------------- | ------------- ||
|VP_ENTITEI||Entiteitscode|||
|VP_VRWRKCD||Verwerkingscode entiteit|||
|VP_VOLGNUM||Volgnummer|????||
|VP_ENTREF||Entiteitsreferentie|||
|VP_RELSRTC||Soort relatie, code|relatietype||
|VP_RELNUM||Relatienummer|Relatienummer||
|VP_RELNUMX||Relatienummer externe partij|(later vertalen naar “extern nummer”)||
|VP_ANAAM||Naam|naam||
|VP_EERSTVN||Eerste voornaam|roepnaam||
|VP_GESLACH||Geslacht/rechtspersoon, code|geslacht||
|VP_STRAAT||Straat|adres||
|VP_HUISNR||Huisnummer|adres||
|VP_PLAATS||Plaats|woonplaats||
|VP_PCODE||Postcode|postcode||
|VP_ADRES1||Adresregel-1 (buitenland)|||
|VP_LAND||Land, code|landcode||
|VP_EMAIL||E-mail adres|emailadres||
|VP_GEBDAT||Geboortedatum|geboortedatum||
|VP_PROFURL||Internet profiel link|||
|VP_IDENOMS||Identificatiedocument, oms|||
|VP_BIC||Bank identificatie code, incasso|bicnummer||
|VP_IBAN||Bank account nummer, incasso|ibannummer||
|VP_BANKTNV||Bankrek. incasso, ten name van|||
|VP_RDNMUT||Reden aanvraag, mutatie, code|mutatiereden||
|VP_IDENUIT||Naam controleur identificatiedoc.|||
|VP_EXTERN||||||

Functies
---------------------

**Updaten:**

De mogelijkheid bestaat om relatiegegevens te wijzigen/aan te vullen. Dit noemen wij een mutatie. Na een mutatie worden de relatiegegevens in Level7 bijgewerkt.

Condities:

* Het revisienummer moet aan het request bericht worden toegevoegd. Dit halen wij op door de functie “RelatieLezenViaNummer” van de relatieservice te gebruiken
* Het relatienummer moet in het bericht worden toegevoegd

Stappen:

*	Relatienummer ophalen
*	Revisienummer ophalen
*	Bericht sturen naar Level7

Bericht(en):

	Relatienummer ophalen


	Revisienummer ophalen


Codelijsten
---------------------

**GSSC - Codelijst ADNGEZ (Gezinssamenstelling)**

|Omschrijving|Code AFD|Waarde Level7|
| ------------- | ------------- | ------------- |
|Alleenstaande zonder kinderen|A|?|
|Gezin zonder kinderen|H||
|Gezin met kind(eren)|I||
|Alleenstaande met kinderen|K||
|Andere gezinssamenstelling|Z|||

**GESLACH - Codelijst ADNGES (Geslacht/rechtspersoon)**

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Man|M|M|
|Vrouw|V|V|
|Rechtspersoon|R|?|

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Man|M|M|
|Vrouw|V|V|
|Rechtspersoon|R|?|

Algemene gegevens
---------------------

**VP entiteit binnen het AFD document**
``` xml
<VP>
  <VP_ENTITEI>VP</VP_ENTITEI>
  <VP_VRWRKCD>4</VP_VRWRKCD>
  <VP_VOLGNUM>2</VP_VOLGNUM>
  <VP_ENTREF>564d78cd-c180-4e72-ad76-9b6093aed8a5</VP_ENTREF>
  <VP_RELSRTC>A</VP_RELSRTC>
  <VP_RELNUM>3539283</VP_RELNUM>
  <VP_RELNUMX>93fa868a-20e3-4a14-b9d0-b10c0a72aab</VP_RELNUMX>
  <VP_ANAAM>Meij</VP_ANAAM>
  <VP_VOORL />
  <VP_VOORV>van der</VP_VOORV>
  <VP_EERSTVN>Nick</VP_EERSTVN>
  <VP_TITEL />
  <VP_GESLACH>M</VP_GESLACH>
  <VP_STRAAT>Wijnbrugstraat</VP_STRAAT>
  <VP_HUISNR>206</VP_HUISNR>
  <VP_TOEVOEG />
  <VP_PLAATS>Rotterdam</VP_PLAATS>
  <VP_PCODE>3011XW</VP_PCODE>
  <VP_ADRES1>1128542967</VP_ADRES1>
  <VP_ADRES2>zxKj7DO9H5</VP_ADRES2>
  <VP_GEOBRED>51.9169430</VP_GEOBRED>
  <VP_GEOLENG>4.488591</VP_GEOLENG>
  <VP_TELNUM />
  <VP_EMAIL>nick.ilt@gmail.com</VP_EMAIL>
  <VP_GEBDAT>19820617</VP_GEBDAT>
  <VP_PROFURL>https://graph.facebook.com/1128542967/picture?type=large</VP_PROFURL>
  <VP_IDENOMS>https://scontent-a.xx.fbcdn.net/hphotos-xpa1/t31.0-8/s720x720/10630723</VP_IDENOMS>
  <VP_BANKRK />
  <VP_BIC>INGBNL2A</VP_BIC>
  <VP_IBAN>NL73INGB0007060306</VP_IBAN>
  <VP_BANKTNV>Hr N van der Meij</VP_BANKTNV>
  <VP_RDNMUT>P1</VP_RDNMUT>
  <VP_IDENUIT>FLjZbKys</VP_IDENUIT>
  <VP_TEKST />
  <VP_EXTERN>12245</VP_EXTERN>
  <VP_ADRES3 />
</VP>
```
**Relatieservice Level7 bericht**
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<ns0:RelatieAanmaken xmlns:ns0="http://schemas.ccs.nl/services/relatieservice" xmlns:ns1="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:relatie="http://schemas.ccs.nl/datacatalogus/modellen/modelrelatie">
<ns0:relatie pc="N">
    <relatie:adres>...</relatie:adres>
    <relatie:emailadres>...</relatie:emailadres>
    <relatie:geboortedatum>...</relatie:geboortedatum>
    <relatie:geslacht>...</relatie:geslacht>
    <relatie:herinneringscode>1</relatie:herinneringscode>
    <relatie:incassocodemutatie>MN</relatie:incassocodemutatie>
    <relatie:incassocodeprolongatie>MN</relatie:incassocodeprolongatie>
    <relatie:landcode>NL</relatie:landcode>
    <relatie:mutatiereden>100</relatie:mutatiereden>
    <relatie:naam>...</relatie:naam>
    <relatie:postcode>...</relatie:postcode>
    <relatie:relatienummer>1</relatie:relatienummer>
    <relatie:relatietype>Z</relatie:relatietype>
    <relatie:roepnaam>...</relatie:roepnaam>
    <relatie:woonplaats>...</relatie:woonplaats>
    <relatie:rekeningnummer pc="N">
      <relatie:bicnummer>...</relatie:bicnummer>
      <relatie:ibannummer>...</relatie:ibannummer>
      <relatie:rekeningnummer>...</relatie:rekeningnummer>
      <relatie:volgnummer>1</relatie:volgnummer>
      <relatie:dnotarekeningnummer pc="I" />
    </relatie:rekeningnummer>
  </ns0:relatie>
</ns0:RelatieAanmaken>
```
