#CCS Relatieservice


##Inhoudsopgave

- [Release notes](#header)
- [Algemene gegevens](#id-section1)
- [Service beschrijving](#id-section2)
- [Mapping](#id-section3)
- [Codelijsten](#id-section4)
- [Functies](#id-section5)
- [Relatie Aanmaken](#id-section6)
- [Relatie Muteren](#id-section7)
- [Foutafhandeling](#id-section8)
- [Testen](#id-section9)

##Release notes

| Versie  | Datum | Beschrijving |Auteur|Bedrijf|
| ------------- | ------------- |||
| 1.01 | 01-01-2015 | De eerste versie van de servicebeschrijving|Dennis van den Hurk|Zeker.Me|

##Algemene gegevens

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
|Endpoint testomgeving | https://www.vspbvfo.nl/ws_test/relatieservice.asmx |
|Endpoint acceptatieomgeving | https://www.vspbvfo.nl/ws_accp/relatieservice.asmx|
|Endpoint productieomgeving | https://www.vspbvfo.nl/ws_prod/relatieservice.asmx|

##Service beschrijving

De Level7 relatieservice dient om een relatie aan te maken (create), muteren (update) en later ook te verwijderen (delete)

##Mapping

|AFD Label|Codelijst|AFD Omschrijving  | Waarde Level7|Bijzonderheden
| ------------- | ------------- | ------------- ||
|VP_VRWRKCD|ADNVRC|Verwerkingscode entiteit|pc||
|VP_VOLGNUM||Volgnummer|revisienummer|Is dit juist??? |
|VP_ENTREF||Entiteitsreferentie|||
|VP_RELSRTC|ADNBEG|Soort relatie, code|relatietype||
|VP_RELNUM||Relatienummer|relatienummer||
|VP_RELNUMX||Relatienummer externe partij|externrelatienummer||
|VP_ANAAM||Naam|naam||
|VP_VOORL||Voorletters|voorletters||
|VP_EERSTVN||Eerste voornaam|roepnaam||
|VP_GESLACH|ADNGES|Geslacht/rechtspersoon, code|geslacht|Wat te doen bij rechtspersoon???|
|VP_STRAAT||Straat|adres||
|VP_HUISNR||Huisnummer|adres||
|VP_TOEVOEG||Huisnummertoevoeging|adres||
|VP_PLAATS||Plaats|woonplaats||
|VP_PCODE||Postcode|postcode||
|VP_ADRES1||Adresregel-1 (buitenland)|adres||
|VP_LAND|ISOLAN|Land, code|landcode||
|VP_EMAIL||E-mail adres|emailadres||
|VP_TELNUM||Telefoonnummer|telefoonprive||
|VP_MOBIEL||Mobiel telefoonnummer|telefoonmobiel||
|VP_TITEL||Titels|titel||
|VP_GEBDAT||Geboortedatum|geboortedatum||
|VP_PROFURL||Internet profiel link|||
|VP_IDENOMS||Identificatiedocument, oms|omsidentificatief||
|VP_BANKRK||Bankrekeningnummer, incasso|rekeningnummer||
|VP_BIC||Bank identificatie code, incasso|bicnummer||
|VP_IBAN||Bank account nummer, incasso|ibannummer||
|VP_|||herinneringscode||
|VP_|||incassocodemutatie||
|VP_|||incassocodeprolongatie||
|VP_BSNR||Burger service nummer|burgerservicenummer||
|VP_BURGST|ADNBUR|Burgerlijke staat, code|burgerlijkestaatcode||
|VP_RDNMUT|ADNMUT|Reden aanvraag, mutatie, code|mutatiereden||
|VP_EXTERN|||||
|SP_ENTITEI|ADNENT|Entiteitscode|partner||
|SP_IDENDAT||Datum afgifte document|afgiftedatumlegitimatie||
|SP_AFGDAT||Datum afgifte eerste rijbewijs|afgiftedatumrijbewijs||
|SP_ANAAM||Naam|naam||
|SP_VOORL||Voorletters|voorletters||
|SP_EERSTVN||Eerste voornaam|roepnaam||
|SP_GESLACH|ADNGES|Geslacht/rechtspersoon, code|geslacht|Verplichte keuze M of V|
|SP_STRAAT||Straat|adres||
|SP_HUISNR||Huisnummer|adres||
|SP_PLAATS||Plaats|woonplaats||
|SP_PCODE||Postcode|postcode||
|SP_LAND|ISOLAN|Land, code|landcode||
|SP_NATIONA|ISOLAN|Nationaliteit, code|nationaliteit||
|SP_GEBDAT||Geboortedatum|geboortedatum||
|SP_OVLDAT||Datum overlijden|overlijdensdatum||
|SP_BSNR||Burger service nummer|burgerservicenummer||
|SP_IDENNR||Nummer afgifte document|legitimatienummer||
|SP_IDENOMS||Identificatiedocument, oms|soortlegitimatie||
|SP_PROFURL||Internet profiel link|||
|SP_TITULAT|ADNTIT|Titulatuur, code|titulatuurcode||
|SP_CATRIJB||Categorie rijbewijs|rijbewijscategorie||
|KN_ENTITEI|ADNENT|Entiteitscode|gezinslid||
|KN_ANAAM||Naam|naam||
|KN_VOORL||Voorletters|voorletters||
|KN_EERSTVN||Eerste voornaam|roepnaam||
|KN_GESLACH|ADNGES|Geslacht/rechtspersoon, code|geslacht|Indien niet gevuld in AFD, dan in level7 gevuld met: O (onbekend)|
|KN_STRAAT||Straat|adres||
|KN_HUISNR||Huisnummer|adres||
|KN_PLAATS||Plaats|woonplaats||
|KN_PCODE||Postcode|postcode||
|KN_LAND|ISOLAN|Land, code|landcode||
|KN_GEBDAT||Geboortedatum|geboortedatum||
|KN_OVLDAT||Datum overlijden|overlijdensdatum||
|KN_BSNR||Burger service nummer|burgerservicenummer||
|KN_RELSRTC||Soort relatie, code|inwonend||
|KN_PROFURL||Internet profiel link||||

##Codelijsten

####VRWRKCD - Codelijst ADNVRC (Verwerkingscode)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Nieuw|0|N|
|Gewijzigd|1|W|
|Vervallen|2|V|
|Ter informatie|4|I|

####RELSRTC - Codelijst ADNBEG (Relatie partij/partij)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Gezinslid|2||
|Bedrijf|3||
|Verzekeringnemer|A||
|Medeverzekerde|M||
|(Regelmatige) bestuurder|R||
|Partner|P||
|Geen|Y||
|Overige|Z||
|Reisgenoot, meeverzekerd|10||
|Samenwonende|SW||
|Werkgever|WG||
|Werknemer|WN|||


####GSSC - Codelijst ADNGEZ (Gezinssamenstelling)

|Omschrijving|Code AFD|Waarde Level7|
| ------------- | ------------- | ------------- |
|Alleenstaande zonder kinderen|A|?|
|Gezin zonder kinderen|H||
|Gezin met kind(eren)|I||
|Alleenstaande met kinderen|K||
|Andere gezinssamenstelling|Z|||

####GESLACH - Codelijst ADNGES (Geslacht/rechtspersoon)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Man|M|M|
|Vrouw|V|V|
|Rechtspersoon|R|||

####LAND - Codelijst ISOLAN (ISO landencodetabel)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Nederland|NL|NL|
|Anders|ZZ|||

####BURGST - Codelijst ADNBUR (Burgerlijke staat)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Gehuwd|1||
|Samenwonend|2||
|Ongehuwd|3||
|Gescheiden|4||
|Onbekend|9|||

####RDNMUT - Codelijst ADNMUT (Mutatiereden)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|Nieuwe relatie|P1||
|Echtscheiding|E||
|Beëindiging samenwoning|41||
|Wijziging bankrekening|85||
|Emigratie|37||
|Kind toevoegen|K1||
|Wijzigen telefoonnummer(s))|P3||
|Adreswijziging|80||
|Wijzigen e-mailadres|P2||
|Kind verwijderen|K2||
|Trouwen|26||
|Samenwoning aangaan|44||
|Overlijden|O|||


####TITULAT - Codelijst ADNTIT (Titulatuur, code)

|Omschrijving|Code AFD|Waarde Level7|
| -------------|-------------|
|De heer|00001|1|
|Mevrouw|00002|2|

##Functies

* :x: ControleerGebruiker
* :white_check_mark: RelatieAanmaken
* :x: RelatieLezenViaEmail
* :x: RelatieLezenViaExternNummer
* :x: RelatieLezenViaNaam
* :white_check_mark: RelatieLezenViaNummer
* :x: RelatieLezenViaPostCode
* :x: RelatieLezenViaPostCodeHuisNummer
* :white_check_mark: RelatieMuteren


##Relatie Aanmaken:


###Proces:
![Omschrijving afbeelding](/img_level7_relatieservice_relatie_aanmaken.png)

####Condities:
Verplicht
* :exclamation: Een VP entiteit moet verwerkingscode 0 hebben

Optioneel
* :question: Een SP entiteit moet verwerkingscode 0 hebben
* :question: Een KN entiteit moet verwerkingscode 0 hebben
* :question: Een rekeningnummer?????

####Bijzonderheden:
Er kan geen XML uitval binnen Level7 ontstaan bij de Relatieservice. Deze fouten worden afgevangen op de wsdl.

####Stappen:

1. **RelatieAanmaken** <br>
*Met deze stap maken wij de relatie aan.*
2. **RelatieLezenViaNummer** <br>
*Wij controleren hiermee of tranasctie consistent is.*


###Voorbeeldberichten:


#### Relatieservice
* :white_check_mark: Gezinslid
* :white_check_mark: Partner
* :white_check_mark: Rekeningnummer
* :x: Werk
* :x: Zaak

#####1. RelatieAanmaken:

Request:

``` xml
<ns0:RelatieAanmaken xmlns:ns0="http://schemas.ccs.nl/services/relatieservice" xmlns:ns1="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:relatie="http://schemas.ccs.nl/datacatalogus/modellen/modelrelatie">
  <ns0:relatie pc="N">
    <relatie:adres>de Vriesstraat 4 </relatie:adres>
    <relatie:emailadres>webmaster@zeker.me</relatie:emailadres><!-- Optioneel -->
    <relatie:geboortedatum>1950-01-01</relatie:geboortedatum><!-- Optioneel -->
    <relatie:geslacht>M</relatie:geslacht><!-- Optioneel -->
    <relatie:herinneringscode>1</relatie:herinneringscode>
    <relatie:incassocodemutatie>MN</relatie:incassocodemutatie>
    <relatie:incassocodeprolongatie>MN</relatie:incassocodeprolongatie>
    <relatie:landcode>NL</relatie:landcode>
    <relatie:mutatiereden>100</relatie:mutatiereden>
    <relatie:naam>Zeker.Me</relatie:naam>
    <relatie:postcode>3261 PC</relatie:postcode>
    <relatie:relatienummer>1</relatie:relatienummer>
    <relatie:relatietype>Z</relatie:relatietype>
    <relatie:roepnaam>Me</relatie:roepnaam><!-- Optioneel -->
    <relatie:telefoonprive /><!-- Optioneel -->
    <relatie:titel /><!-- Optioneel -->
    <relatie:voorletters /><!-- Optioneel -->
    <relatie:voorvoegsels>van</relatie:voorvoegsels><!-- Optioneel -->
    <relatie:woonplaats>OUD-BEIJERLAND</relatie:woonplaats>
    <!-- Optionele node Gezinslid (Itererend)-->
    <relatie:gezinslid pc="N">
      <relatie:geboortedatum>2014-01-01</relatie:geboortedatum><!-- Optioneel -->
      <relatie:geslacht>M</relatie:geslacht><!-- Optioneel -->
      <relatie:inwonend>1</relatie:inwonend><!-- Optioneel -->
      <relatie:naam>Baas</relatie:naam>
      <relatie:overlijdensdatum>2015-02-01</relatie:overlijdensdatum><!-- Optioneel -->
      <relatie:roepnaam>Kees</relatie:roepnaam><!-- Optioneel -->
      <relatie:voorletters>K</relatie:voorletters><!-- Optioneel -->
      <relatie:voorvoegsels>de</relatie:voorvoegsels><!-- Optioneel -->
    </relatie:gezinslid>
    <!-- Optionele node Partner -->
    <relatie:partner pc="N">
      <relatie:afgiftedatumlegitimatie>2014-01-03</relatie:afgiftedatumlegitimatie><!-- Optioneel -->
      <relatie:afgiftedatumrijbewijs>2013-05-01</relatie:afgiftedatumrijbewijs/><!-- Optioneel -->
      <relatie:geboortedatum>1980-01-02</relatie:geboortedatum><!-- Optioneel -->
      <relatie:legitimatienummer>123456</relatie:legitimatienummer><!-- Optioneel -->
      <relatie:geslacht>M</relatie:geslacht><!-- Optioneel -->
      <relatie:naam>Veen</relatie:naam>
      <relatie:nationaliteit>NL</relatie:nationaliteit><!-- Optioneel -->
      <relatie:roepnaam>Piet</relatie:roepnaam><!-- Optioneel -->
      <relatie:soortlegitimatie>RB</relatie:soortlegitimatie><!-- Optioneel -->
      <relatie:titulatuurcode>1</relatie:titulatuurcode><!-- Optioneel -->
      <relatie:overlijdensdatum>2015-01-01</relatie:overlijdensdatum><!-- Optioneel -->
      <relatie:rijbewijscategorie>B</relatie:rijbewijscategorie><!-- Optioneel -->
      <relatie:voorletters>P</relatie:voorletters><!-- Optioneel -->
      <relatie:voorvoegsels>van</relatie:voorvoegsels><!-- Optioneel -->
    </relatie:partner>
    <!-- Optionele node Rekeningnummer (Itererend)-->
    <relatie:rekeningnummer pc="N">
      <relatie:bicnummer>INGBNL2A</relatie:bicnummer>
      <relatie:ibannummer>NL53INGB0654422370</relatie:ibannummer>
      <relatie:rekeningnummer>654422370</relatie:rekeningnummer>
      <relatie:volgnummer>1</relatie:volgnummer>
      <relatie:dnotarekeningnummer pc="I" />
    </relatie:rekeningnummer>
    <!-- Einde optionele node -->
  </ns0:relatie>
</ns0:RelatieAanmaken>
```

Response:

``` xml

<s:RelatieAanmakenResponse xmlns:s="http://schemas.ccs.nl/services/relatieservice" xmlns:bt="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <s:RelatieAanmakenResult>3540974</s:RelatieAanmakenResult>
</s:RelatieAanmakenResponse>
```

#####2. RelatieLezenViaNummer

Request:

``` xml
      <rel:RelatieLezenViaNummer>
         <rel:relatieNummer>3540974</rel:relatieNummer>
      </rel:RelatieLezenViaNummer>

```


Response:

``` xml
    <s:RelatieLezenViaNummerResponse xmlns="http://schemas.ccs.nl/datacatalogus/modellen/modelrelatie" xmlns:bt="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:s="http://schemas.ccs.nl/services/relatieservice">
         <s:RelatieLezenViaNummerResult>
            <adres>de Vriesstraat 4</adres>
            <afdelingscode/>
            <afgiftedatumeersterijbewijs xsi:nil="true"/>
            <afgiftedatumlegitimatie xsi:nil="true"/>
            <afgiftedatumrijbewijs xsi:nil="true"/>
            <alleenwerknemer>N</alleenwerknemer>
            <beroepscode>0</beroepscode>
            <bezoekadres/>
            <burgerlijkestaatcode/>
            <burgerservicenummer/>
            <categoriecodewfd/>
            <communicatiercklant>Post</communicatiercklant>
            <dubieuzedebiteur>N</dubieuzedebiteur>
            <emailadres>webmaster@zeker.me</emailadres>
            <externrelatienummer/>
            <faxnummer/>
            <financieringscode/>
            <geboortedatum>1950-01-01</geboortedatum>
            <geslacht>M</geslacht>
            <herinneringscode>1</herinneringscode>
            <huisvestingscode/>
            <huwelijksdatum xsi:nil="true"/>
            <huwelijksevoorwaarden>O</huwelijksevoorwaarden>
            <hypotheekcode/>
            <incassocodemutatie>MN</incassocodemutatie>
            <incassocodeprolongatie>MN</incassocodeprolongatie>
            <indicatief/>
            <inkomenscode/>
            <kantoormedewerker>0</kantoormedewerker>
            <kantoornummer>0</kantoornummer>
            <laatstebezoekdatum xsi:nil="true"/>
            <landcode>NL</landcode>
            <landcodebezoekadres/>
            <legitimatienummer/>
            <locatie/>
            <mailingcode/>
            <mutatiedatum>2015-04-24</mutatiedatum>
            <mutatiereden>100</mutatiereden>
            <naam>Zeker.Me</naam>
            <naam2/>
            <naam3/>
            <naamfonetisch>S598</naamfonetisch>
            <naamfonetischdeel>S598</naamfonetischdeel>
            <naaminclaanhef/>
            <naamproducent/>
            <naamtussenpersoon/>
            <nationaliteit>NL</nationaliteit>
            <omsberoepscode/>
            <omsburgerlijkestaatcode>Onbekend</omsburgerlijkestaatcode>
            <omschrijvingtoegangfo/>
            <omsincassocodemutatie>Machtiging met nota</omsincassocodemutatie>
            <omsincassocodeprolongatie>Machtiging met nota</omsincassocodeprolongatie>
            <omsindicatief/>
            <omslandcode>Nederland</omslandcode>
            <omslandcodebezoekadres/>
            <omsmutatiereden>Nieuwe Relatie</omsmutatiereden>
            <omsnationaliteit>Nederlandse</omsnationaliteit>
            <omstitulatuurcode/>
            <omvangskortingscode/>
            <overlijdensdatum xsi:nil="true"/>
            <pensioencode/>
            <polisdigitaalversturen>N</polisdigitaalversturen>
            <postcode>3261 PC</postcode>
            <postcodebezoekadres/>
            <preselectiecode/>
            <producent>0</producent>
            <productprofieldoelgroep/>
            <rekeningnummer1>654422370</rekeningnummer1>
            <rekeningnummer2/>
            <rekeningnummer3/>
            <rekeningnummer4/>
            <relatiecode/>
            <relatienummer>3540974</relatienummer>
            <relatiesinds xsi:nil="true"/>
            <relatietoneninwa>J</relatietoneninwa>
            <relatietype>Z</relatietype>
            <revisienummer>0</revisienummer>
            <rijbewijscategorie/>
            <roepnaam>Me</roepnaam>
            <selectiecode1/>
            <selectiecode2/>
            <selectiecode3/>
            <selectiecode4/>
            <selectiecode5/>
            <soortdienstverlening>S</soortdienstverlening>
            <soortlegitimatie/>
            <taalcode>nl</taalcode>
            <telefoonmobiel/>
            <telefoonprive/>
            <titel/>
            <titulatuurcode>0</titulatuurcode>
            <toegangscodefo>V</toegangscodefo>
            <tussenpersoonnummer>0</tussenpersoonnummer>
            <verstuurwijzenota>Post</verstuurwijzenota>
            <verstuurwijzeoverig>Post</verstuurwijzeoverig>
            <vertrouwelijk/>
            <voorletters/>
            <voorvoegsels>van</voorvoegsels>
            <werkgevernaam/>
            <werkgevernummer>0</werkgevernummer>
            <woonplaats>OUD-BEIJERLAND</woonplaats>
            <woonplaatsbezoekadres/>
            <ziektekostencode/>
            <partner>
               <afgiftedatumeersterijbewijs xsi:nil="true"/>
               <afgiftedatumlegitimatie xsi:nil="true"/>
               <afgiftedatumrijbewijs xsi:nil="true"/>
               <bedrijfsspaarregeling>0</bedrijfsspaarregeling>
               <beroepscode>0</beroepscode>
               <burgerservicenummer/>
               <geboortedatum xsi:nil="true"/>
               <geslacht/>
               <legitimatienummer/>
               <naam/>
               <nationaliteit>NL</nationaliteit>
               <omsberoepscode/>
               <omsnationaliteit/>
               <omstitulatuurcode/>
               <overlijdensdatum xsi:nil="true"/>
               <relatieidpartner>0</relatieidpartner>
               <relatienummer>3540974</relatienummer>
               <rijbewijscategorie/>
               <roepnaam/>
               <soortlegitimatie/>
               <titel/>
               <titulatuurcode>0</titulatuurcode>
               <voorletters/>
               <voorvoegsels/>
            </partner>
            <rekeningnummer>
               <bicnummer>INGBNL2A</bicnummer>
               <gebruikerlaatsterevisie/>
               <ibannummer>NL53INGB0654422370</ibannummer>
               <idrekeningnummer>2269453</idrekeningnummer>
               <landcode>NL</landcode>
               <medewerkermutatie>0</medewerkermutatie>
               <omschrijving/>
               <rekeningnummer>654422370</rekeningnummer>
               <revisienummer>0</revisienummer>
               <tenaamstelling/>
               <volgnummer>1</volgnummer>
            </rekeningnummer>
            <werk>
               <aardwerkzaamheden/>
               <bedrijfsomschrijving/>
               <bedrijfsspaarregeling>0</bedrijfsspaarregeling>
               <datumindienst xsi:nil="true"/>
               <datumuitdienst xsi:nil="true"/>
               <emolumenten>0</emolumenten>
               <emolumentenperc>0</emolumentenperc>
               <extramaanden>0</extramaanden>
               <functiecode/>
               <handenarbeid>0</handenarbeid>
               <leidinggevend>0</leidinggevend>
               <machinalebewerking>0</machinalebewerking>
               <mutatiedatumsalaris xsi:nil="true"/>
               <omschrijvingwerkgever/>
               <opleidingscode/>
               <parttimeperc>0</parttimeperc>
               <peildag>0</peildag>
               <peilmaand>0</peilmaand>
               <personeelsnummer/>
               <premiespaarregeling/>
               <relatieidwerkgever>0</relatieidwerkgever>
               <relatienrwerkgever>0</relatienrwerkgever>
               <relatienummer>3540974</relatienummer>
               <salaris>0</salaris>
               <salaristermijn/>
               <soortbaan/>
               <soortregeling/>
               <vakantietoeslagperc>0</vakantietoeslagperc>
               <werkgevercode/>
               <werknemerebl>0</werknemerebl>
            </werk>
            <zaak>
               <aantalpersoneelsleden>0</aantalpersoneelsleden>
               <bedrijfscode>0</bedrijfscode>
               <bikcode/>
               <kvknummer/>
               <naamaccountant/>
               <naamadviseur/>
               <naamcontactpersoon/>
               <naamdirecteur/>
               <omsrechtsvorm/>
               <oprichtingsdatum xsi:nil="true"/>
               <premiespaarregeling/>
               <premiespaarregelingscode/>
               <rechtsvormcode/>
               <relatieidaccountant>0</relatieidaccountant>
               <relatieidadviseur>0</relatieidadviseur>
               <relatieiddirecteur>0</relatieiddirecteur>
               <relatienummer>3540974</relatienummer>
               <rsin>0</rsin>
               <sbicode/>
               <spaarloonregeling/>
               <spaarloonregelingscode/>
               <telefooncontactpersoon/>
               <telefooncontactpersoonacc/>
               <telefoonzaak/>
               <vertrouwelijk/>
               <vestigingsnummer>0</vestigingsnummer>
               <werkgeverebl>0</werkgeverebl>
               <woonplaatskvk/>
            </zaak>
         </s:RelatieLezenViaNummerResult>
      </s:RelatieLezenViaNummerResponse>
```

## Relatie Muteren

###Proces:
![Omschrijving afbeelding](/img_level7_relatieservice_relatie_muteren.png)

####Condities:
Verplicht
* :exclamation: Een VP entiteit moet verwerkingscode 1 hebben

Optioneel
* :question: Een SP entiteit moet verwerkingscode 1 hebben
* :question: Een KN entiteit moet verwerkingscode 1 hebben
* :question: Een rekeningnummer????
* :question: Bedrijf????
* :question: Nieuwe werkgever???

####Mutatieredenen:

|Mutatiereden Zeker.Me|AFD Codelijst|AFD Code|AFD Omschrijving  |Mutatiereden Level7|Waarde Level7|
| ------------- | ------------- | ------------- ||
|Relatie aanmaken|ADNMUT|P1|Nieuwe relatie|100|Nieuwe relatie|
|Verzekering beëindigen|ADNMUT|R1|Opzegging door client|||
|Ik heb me bedacht|ADNMUT|R3|Royement ivm niet doorgaan (wacht)|||
|Ik verzeker me elders|ADNMUT|R8|Royement oversluiting andere maatschappij|||
|Dekking wijzigen|ADNMUT|50|Wijziging (aanvullende) dekkingen|||
|Andere auto gekocht|ADNMUT|79|Wijziging verzekerde object, dekking|||
|Regelmatige bestuurder wijzigen|ADNMUT|91|Wijziging regelmatige bestuurder Personenauto|||
|Ik ga scheiden|ADNMUT|E|Echtscheiding|||
|Wij gaan uit elkaar|ADNMUT|41|Beëindiging samenwoning|||
|Wijzig bankrekeningnummer|ADNMUT|85|Wijziging bankrekening|||
|Ik ga emigreren|ADNMUT|37|Emigratie|||
|Ik heb een kind gekregen|ADNMUT|K1|Kind toevoegen|||
|Wijzig telefoonnummer|ADNMUT|P3|Wijzigen telefoonnummer(s))|||
|Ik ga verhuizen|ADNMUT|80|Adreswijziging|||
|Wijzig e-mailadres|ADNMUT|P2|Wijzigen e-mailadres|||
|Mijn kind gaat het huis uit|ADNMUT|K2|Kind verwijderen|||
|Ik ga trouwen|ADNMUT|26|Trouwen|||
|Ik ga samenwonen|ADNMUT|44|Samenwoning aangaan|||
|Overlijden|ADNMUT|O|Overlijden||||

####Bijzonderheden:

- Voor iedere mutatie dient er een nieuw revisienummer opgehaald te worden. In het AFD is dit VP_VOLGNUM (?) // OOK TERUGSCHRIJVEN. Dit speelt ook na relatieaanmaken.
- Er kan geen XML uitval binnen Level7 ontstaan bij de Relatieservice. De fouten worden afgevangen op de wsdl.

####Stappen:

1. **RelatieLezenViaNummer** <br>
*Wij achterhalen hiermee wat het revisienummer is.*
2. **RelatieMuteren** <br>
*Met deze stap wijzigen wij de relatie.*
3. **RelatieLezenViaNummer** <br>
*Wij controleren hiermee of tranasctie consistent is.*


###Voorbeeldberichten


#### RelatieService
* :white_check_mark: Gezinslid
* :white_check_mark: Partner
* :white_check_mark: Rekeningnummer
* :x: Werk
* :x: Zaak

#####1. RelatieLezenViaNummer:

Request:

``` xml
<rel:RelatieLezenViaNummer>
   <rel:relatieNummer>3540974</rel:relatieNummer>
</rel:RelatieLezenViaNummer>

```


Response:

``` xml
<s:RelatieLezenViaNummerResponse xmlns="http://schemas.ccs.nl/datacatalogus/modellen/modelrelatie" xmlns:bt="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:s="http://schemas.ccs.nl/services/relatieservice">
   <s:RelatieLezenViaNummerResult>
      <adres>de Vriesstraat 4</adres>
      <afdelingscode/>
      <afgiftedatumeersterijbewijs xsi:nil="true"/>
      <afgiftedatumlegitimatie xsi:nil="true"/>
      <afgiftedatumrijbewijs xsi:nil="true"/>
      <alleenwerknemer>N</alleenwerknemer>
      <beroepscode>0</beroepscode>
      <bezoekadres/>
      <burgerlijkestaatcode/>
      <burgerservicenummer/>
      <categoriecodewfd/>
      <communicatiercklant>Post</communicatiercklant>
      <dubieuzedebiteur>N</dubieuzedebiteur>
      <emailadres>webmaster@zeker.me</emailadres>
      <externrelatienummer/>
      <faxnummer/>
      <financieringscode/>
      <geboortedatum>1950-01-01</geboortedatum>
      <geslacht>M</geslacht>
      <herinneringscode>1</herinneringscode>
      <huisvestingscode/>
      <huwelijksdatum xsi:nil="true"/>
      <huwelijksevoorwaarden>O</huwelijksevoorwaarden>
      <hypotheekcode/>
      <incassocodemutatie>MN</incassocodemutatie>
      <incassocodeprolongatie>MN</incassocodeprolongatie>
      <indicatief/>
      <inkomenscode/>
      <kantoormedewerker>0</kantoormedewerker>
      <kantoornummer>0</kantoornummer>
      <laatstebezoekdatum xsi:nil="true"/>
      <landcode>NL</landcode>
      <landcodebezoekadres/>
      <legitimatienummer/>
      <locatie/>
      <mailingcode/>
      <mutatiedatum>2015-04-24</mutatiedatum>
      <mutatiereden>100</mutatiereden>
      <naam>Zeker.Me</naam>
      <naam2/>
      <naam3/>
      <naamfonetisch>S598</naamfonetisch>
      <naamfonetischdeel>S598</naamfonetischdeel>
      <naaminclaanhef/>
      <naamproducent/>
      <naamtussenpersoon/>
      <nationaliteit>NL</nationaliteit>
      <omsberoepscode/>
      <omsburgerlijkestaatcode>Onbekend</omsburgerlijkestaatcode>
      <omschrijvingtoegangfo/>
      <omsincassocodemutatie>Machtiging met nota</omsincassocodemutatie>
      <omsincassocodeprolongatie>Machtiging met nota</omsincassocodeprolongatie>
      <omsindicatief/>
      <omslandcode>Nederland</omslandcode>
      <omslandcodebezoekadres/>
      <omsmutatiereden>Nieuwe Relatie</omsmutatiereden>
      <omsnationaliteit>Nederlandse</omsnationaliteit>
      <omstitulatuurcode/>
      <omvangskortingscode/>
      <overlijdensdatum xsi:nil="true"/>
      <pensioencode/>
      <polisdigitaalversturen>N</polisdigitaalversturen>
      <postcode>3261 PC</postcode>
      <postcodebezoekadres/>
      <preselectiecode/>
      <producent>0</producent>
      <productprofieldoelgroep/>
      <rekeningnummer1>654422370</rekeningnummer1>
      <rekeningnummer2/>
      <rekeningnummer3/>
      <rekeningnummer4/>
      <relatiecode/>
      <relatienummer>3540974</relatienummer>
      <relatiesinds xsi:nil="true"/>
      <relatietoneninwa>J</relatietoneninwa>
      <relatietype>Z</relatietype>
      <revisienummer>0</revisienummer>
      <rijbewijscategorie/>
      <roepnaam>Me</roepnaam>
      <selectiecode1/>
      <selectiecode2/>
      <selectiecode3/>
      <selectiecode4/>
      <selectiecode5/>
      <soortdienstverlening>S</soortdienstverlening>
      <soortlegitimatie/>
      <taalcode>nl</taalcode>
      <telefoonmobiel/>
      <telefoonprive/>
      <titel/>
      <titulatuurcode>0</titulatuurcode>
      <toegangscodefo>V</toegangscodefo>
      <tussenpersoonnummer>0</tussenpersoonnummer>
      <verstuurwijzenota>Post</verstuurwijzenota>
      <verstuurwijzeoverig>Post</verstuurwijzeoverig>
      <vertrouwelijk/>
      <voorletters/>
      <voorvoegsels>van</voorvoegsels>
      <werkgevernaam/>
      <werkgevernummer>0</werkgevernummer>
      <woonplaats>OUD-BEIJERLAND</woonplaats>
      <woonplaatsbezoekadres/>
      <ziektekostencode/>
      <partner>
         <afgiftedatumeersterijbewijs xsi:nil="true"/>
         <afgiftedatumlegitimatie xsi:nil="true"/>
         <afgiftedatumrijbewijs xsi:nil="true"/>
         <bedrijfsspaarregeling>0</bedrijfsspaarregeling>
         <beroepscode>0</beroepscode>
         <burgerservicenummer/>
         <geboortedatum xsi:nil="true"/>
         <geslacht/>
         <legitimatienummer/>
         <naam/>
         <nationaliteit>NL</nationaliteit>
         <omsberoepscode/>
         <omsnationaliteit/>
         <omstitulatuurcode/>
         <overlijdensdatum xsi:nil="true"/>
         <relatieidpartner>0</relatieidpartner>
         <relatienummer>3540974</relatienummer>
         <rijbewijscategorie/>
         <roepnaam/>
         <soortlegitimatie/>
         <titel/>
         <titulatuurcode>0</titulatuurcode>
         <voorletters/>
         <voorvoegsels/>
      </partner>
      <rekeningnummer>
         <bicnummer>INGBNL2A</bicnummer>
         <gebruikerlaatsterevisie/>
         <ibannummer>NL53INGB0654422370</ibannummer>
         <idrekeningnummer>2269453</idrekeningnummer>
         <landcode>NL</landcode>
         <medewerkermutatie>0</medewerkermutatie>
         <omschrijving/>
         <rekeningnummer>654422370</rekeningnummer>
         <revisienummer>0</revisienummer>
         <tenaamstelling/>
         <volgnummer>1</volgnummer>
      </rekeningnummer>
      <werk>
         <aardwerkzaamheden/>
         <bedrijfsomschrijving/>
         <bedrijfsspaarregeling>0</bedrijfsspaarregeling>
         <datumindienst xsi:nil="true"/>
         <datumuitdienst xsi:nil="true"/>
         <emolumenten>0</emolumenten>
         <emolumentenperc>0</emolumentenperc>
         <extramaanden>0</extramaanden>
         <functiecode/>
         <handenarbeid>0</handenarbeid>
         <leidinggevend>0</leidinggevend>
         <machinalebewerking>0</machinalebewerking>
         <mutatiedatumsalaris xsi:nil="true"/>
         <omschrijvingwerkgever/>
         <opleidingscode/>
         <parttimeperc>0</parttimeperc>
         <peildag>0</peildag>
         <peilmaand>0</peilmaand>
         <personeelsnummer/>
         <premiespaarregeling/>
         <relatieidwerkgever>0</relatieidwerkgever>
         <relatienrwerkgever>0</relatienrwerkgever>
         <relatienummer>3540974</relatienummer>
         <salaris>0</salaris>
         <salaristermijn/>
         <soortbaan/>
         <soortregeling/>
         <vakantietoeslagperc>0</vakantietoeslagperc>
         <werkgevercode/>
         <werknemerebl>0</werknemerebl>
      </werk>
      <zaak>
         <aantalpersoneelsleden>0</aantalpersoneelsleden>
         <bedrijfscode>0</bedrijfscode>
         <bikcode/>
         <kvknummer/>
         <naamaccountant/>
         <naamadviseur/>
         <naamcontactpersoon/>
         <naamdirecteur/>
         <omsrechtsvorm/>
         <oprichtingsdatum xsi:nil="true"/>
         <premiespaarregeling/>
         <premiespaarregelingscode/>
         <rechtsvormcode/>
         <relatieidaccountant>0</relatieidaccountant>
         <relatieidadviseur>0</relatieidadviseur>
         <relatieiddirecteur>0</relatieiddirecteur>
         <relatienummer>3540974</relatienummer>
         <rsin>0</rsin>
         <sbicode/>
         <spaarloonregeling/>
         <spaarloonregelingscode/>
         <telefooncontactpersoon/>
         <telefooncontactpersoonacc/>
         <telefoonzaak/>
         <vertrouwelijk/>
         <vestigingsnummer>0</vestigingsnummer>
         <werkgeverebl>0</werkgeverebl>
         <woonplaatskvk/>
      </zaak>
   </s:RelatieLezenViaNummerResult>
</s:RelatieLezenViaNummerResponse>
```

#####2. RelatieMuteren:

Request:

``` xml
   <ns0:RelatieMuteren xmlns:ns0="http://schemas.ccs.nl/services/relatieservice" xmlns:ns1="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:relatie="http://schemas.ccs.nl/datacatalogus/modellen/modelrelatie">
  		<ns0:relatie pc="W">
    		<relatie:adres>de Vriesstraat 4 </relatie:adres>
    		<relatie:emailadres>webmaster@zeker.me</relatie:emailadres>
    		<relatie:geboortedatum>1950-01-01</relatie:geboortedatum>
    		<relatie:geslacht>M</relatie:geslacht>
    		<relatie:herinneringscode>1</relatie:herinneringscode>
    		<relatie:incassocodemutatie>MN</relatie:incassocodemutatie>
    		<relatie:incassocodeprolongatie>MN</relatie:incassocodeprolongatie>
    		<relatie:landcode>NL</relatie:landcode>
    		<relatie:mutatiereden>999</relatie:mutatiereden>
    		<relatie:naam>Zeker.Me</relatie:naam>
    		<relatie:postcode>3261 PC</relatie:postcode>
    		<relatie:relatienummer>3540974</relatie:relatienummer>
    		<relatie:relatietype>Z</relatie:relatietype>
    		<relatie:revisienummer>0</relatie:revisienummer>
    		<relatie:roepnaam>Me</relatie:roepnaam>
    		<relatie:telefoonprive />
    		<relatie:titel/>
    		<relatie:voorletters />
    		<relatie:voorvoegsels>van</relatie:voorvoegsels>
    		<relatie:woonplaats>OUD-BEIJERLAND</relatie:woonplaats>
    		<relatie:gezinslid pc="W">
      		<relatie:geboortedatum>2014-01-01</relatie:geboortedatum>
      		<relatie:geslacht>M</relatie:geslacht>
      		<relatie:inwonend>1</relatie:inwonend>
      		<relatie:naam>Baas</relatie:naam>
      		<relatie:overlijdensdatum>2015-02-01</relatie:overlijdensdatum>
      		<relatie:roepnaam>Kees</relatie:roepnaam>
      		<relatie:voorletters>K</relatie:voorletters>
      		<relatie:voorvoegsels>de</relatie:voorvoegsels>
    		</relatie:gezinslid>
    		<relatie:partner pc="W">
      		<relatie:afgiftedatumlegitimatie>2014-01-03</relatie:afgiftedatumlegitimatie>
      		<relatie:afgiftedatumrijbewijs>2013-05-01</relatie:afgiftedatumrijbewijs>
      		<relatie:geboortedatum>1980-01-02</relatie:geboortedatum>
      		<relatie:legitimatienummer>123456</relatie:legitimatienummer>
      		<relatie:naam>Veen</relatie:naam>
      		<relatie:nationaliteit>NL</relatie:nationaliteit>
      		<relatie:roepnaam>Piet</relatie:roepnaam>
      		<relatie:soortlegitimatie>RB</relatie:soortlegitimatie>
      		<relatie:titulatuurcode>1</relatie:titulatuurcode>
      		<relatie:voorletters>P</relatie:voorletters>
      		<relatie:voorvoegsels>de</relatie:voorvoegsels>
  		</relatie:partner>
    		<relatie:rekeningnummer pc="W">
      		<relatie:bicnummer>INGBNL2A</relatie:bicnummer>
      		<relatie:ibannummer>NL53INGB0654422370</relatie:ibannummer>
      		<relatie:rekeningnummer>654422370</relatie:rekeningnummer>
      		<relatie:volgnummer>1</relatie:volgnummer>
      		<relatie:dnotarekeningnummer pc="I" />
    		</relatie:rekeningnummer>
  		</ns0:relatie>
      </ns0:RelatieMuteren>
   </soapenv:Body>
</soapenv:Envelope>
```


Response:

``` xml
<s:RelatieMuterenResponse xmlns:bt="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:s="http://schemas.ccs.nl/services/relatieservice">
         <s:RelatieMuterenResult>3540974</s:RelatieMuterenResult>
      </s:RelatieMuterenResponse>
```


#####3. RelatieLezenViaNummer

Request:

``` xml
      <rel:RelatieLezenViaNummer>
         <rel:relatieNummer>3540974</rel:relatieNummer>
      </rel:RelatieLezenViaNummer>

```


Response:

``` xml
    <s:RelatieLezenViaNummerResponse xmlns="http://schemas.ccs.nl/datacatalogus/modellen/modelrelatie" xmlns:bt="http://schemas.ccs.nl/datacatalogus/basistypes" xmlns:s="http://schemas.ccs.nl/services/relatieservice">
         <s:RelatieLezenViaNummerResult>
            <adres>de Vriesstraat 4</adres>
            <afdelingscode/>
            <afgiftedatumeersterijbewijs xsi:nil="true"/>
            <afgiftedatumlegitimatie xsi:nil="true"/>
            <afgiftedatumrijbewijs xsi:nil="true"/>
            <alleenwerknemer>N</alleenwerknemer>
            <beroepscode>0</beroepscode>
            <bezoekadres/>
            <burgerlijkestaatcode/>
            <burgerservicenummer/>
            <categoriecodewfd/>
            <communicatiercklant>Post</communicatiercklant>
            <dubieuzedebiteur>N</dubieuzedebiteur>
            <emailadres>webmaster@zeker.me</emailadres>
            <externrelatienummer/>
            <faxnummer/>
            <financieringscode/>
            <geboortedatum>1950-01-01</geboortedatum>
            <geslacht>M</geslacht>
            <herinneringscode>1</herinneringscode>
            <huisvestingscode/>
            <huwelijksdatum xsi:nil="true"/>
            <huwelijksevoorwaarden>O</huwelijksevoorwaarden>
            <hypotheekcode/>
            <incassocodemutatie>MN</incassocodemutatie>
            <incassocodeprolongatie>MN</incassocodeprolongatie>
            <indicatief/>
            <inkomenscode/>
            <kantoormedewerker>0</kantoormedewerker>
            <kantoornummer>0</kantoornummer>
            <laatstebezoekdatum xsi:nil="true"/>
            <landcode>NL</landcode>
            <landcodebezoekadres/>
            <legitimatienummer/>
            <locatie/>
            <mailingcode/>
            <mutatiedatum>2015-04-24</mutatiedatum>
            <mutatiereden>100</mutatiereden>
            <naam>Zeker.Me</naam>
            <naam2/>
            <naam3/>
            <naamfonetisch>S598</naamfonetisch>
            <naamfonetischdeel>S598</naamfonetischdeel>
            <naaminclaanhef/>
            <naamproducent/>
            <naamtussenpersoon/>
            <nationaliteit>NL</nationaliteit>
            <omsberoepscode/>
            <omsburgerlijkestaatcode>Onbekend</omsburgerlijkestaatcode>
            <omschrijvingtoegangfo/>
            <omsincassocodemutatie>Machtiging met nota</omsincassocodemutatie>
            <omsincassocodeprolongatie>Machtiging met nota</omsincassocodeprolongatie>
            <omsindicatief/>
            <omslandcode>Nederland</omslandcode>
            <omslandcodebezoekadres/>
            <omsmutatiereden>Nieuwe Relatie</omsmutatiereden>
            <omsnationaliteit>Nederlandse</omsnationaliteit>
            <omstitulatuurcode/>
            <omvangskortingscode/>
            <overlijdensdatum xsi:nil="true"/>
            <pensioencode/>
            <polisdigitaalversturen>N</polisdigitaalversturen>
            <postcode>3261 PC</postcode>
            <postcodebezoekadres/>
            <preselectiecode/>
            <producent>0</producent>
            <productprofieldoelgroep/>
            <rekeningnummer1>654422370</rekeningnummer1>
            <rekeningnummer2/>
            <rekeningnummer3/>
            <rekeningnummer4/>
            <relatiecode/>
            <relatienummer>3540974</relatienummer>
            <relatiesinds xsi:nil="true"/>
            <relatietoneninwa>J</relatietoneninwa>
            <relatietype>Z</relatietype>
            <revisienummer>0</revisienummer>
            <rijbewijscategorie/>
            <roepnaam>Me</roepnaam>
            <selectiecode1/>
            <selectiecode2/>
            <selectiecode3/>
            <selectiecode4/>
            <selectiecode5/>
            <soortdienstverlening>S</soortdienstverlening>
            <soortlegitimatie/>
            <taalcode>nl</taalcode>
            <telefoonmobiel/>
            <telefoonprive/>
            <titel/>
            <titulatuurcode>0</titulatuurcode>
            <toegangscodefo>V</toegangscodefo>
            <tussenpersoonnummer>0</tussenpersoonnummer>
            <verstuurwijzenota>Post</verstuurwijzenota>
            <verstuurwijzeoverig>Post</verstuurwijzeoverig>
            <vertrouwelijk/>
            <voorletters/>
            <voorvoegsels>van</voorvoegsels>
            <werkgevernaam/>
            <werkgevernummer>0</werkgevernummer>
            <woonplaats>OUD-BEIJERLAND</woonplaats>
            <woonplaatsbezoekadres/>
            <ziektekostencode/>
            <partner>
               <afgiftedatumeersterijbewijs xsi:nil="true"/>
               <afgiftedatumlegitimatie xsi:nil="true"/>
               <afgiftedatumrijbewijs xsi:nil="true"/>
               <bedrijfsspaarregeling>0</bedrijfsspaarregeling>
               <beroepscode>0</beroepscode>
               <burgerservicenummer/>
               <geboortedatum xsi:nil="true"/>
               <geslacht/>
               <legitimatienummer/>
               <naam/>
               <nationaliteit>NL</nationaliteit>
               <omsberoepscode/>
               <omsnationaliteit/>
               <omstitulatuurcode/>
               <overlijdensdatum xsi:nil="true"/>
               <relatieidpartner>0</relatieidpartner>
               <relatienummer>3540974</relatienummer>
               <rijbewijscategorie/>
               <roepnaam/>
               <soortlegitimatie/>
               <titel/>
               <titulatuurcode>0</titulatuurcode>
               <voorletters/>
               <voorvoegsels/>
            </partner>
            <rekeningnummer>
               <bicnummer>INGBNL2A</bicnummer>
               <gebruikerlaatsterevisie/>
               <ibannummer>NL53INGB0654422370</ibannummer>
               <idrekeningnummer>2269453</idrekeningnummer>
               <landcode>NL</landcode>
               <medewerkermutatie>0</medewerkermutatie>
               <omschrijving/>
               <rekeningnummer>654422370</rekeningnummer>
               <revisienummer>0</revisienummer>
               <tenaamstelling/>
               <volgnummer>1</volgnummer>
            </rekeningnummer>
            <werk>
               <aardwerkzaamheden/>
               <bedrijfsomschrijving/>
               <bedrijfsspaarregeling>0</bedrijfsspaarregeling>
               <datumindienst xsi:nil="true"/>
               <datumuitdienst xsi:nil="true"/>
               <emolumenten>0</emolumenten>
               <emolumentenperc>0</emolumentenperc>
               <extramaanden>0</extramaanden>
               <functiecode/>
               <handenarbeid>0</handenarbeid>
               <leidinggevend>0</leidinggevend>
               <machinalebewerking>0</machinalebewerking>
               <mutatiedatumsalaris xsi:nil="true"/>
               <omschrijvingwerkgever/>
               <opleidingscode/>
               <parttimeperc>0</parttimeperc>
               <peildag>0</peildag>
               <peilmaand>0</peilmaand>
               <personeelsnummer/>
               <premiespaarregeling/>
               <relatieidwerkgever>0</relatieidwerkgever>
               <relatienrwerkgever>0</relatienrwerkgever>
               <relatienummer>3540974</relatienummer>
               <salaris>0</salaris>
               <salaristermijn/>
               <soortbaan/>
               <soortregeling/>
               <vakantietoeslagperc>0</vakantietoeslagperc>
               <werkgevercode/>
               <werknemerebl>0</werknemerebl>
            </werk>
            <zaak>
               <aantalpersoneelsleden>0</aantalpersoneelsleden>
               <bedrijfscode>0</bedrijfscode>
               <bikcode/>
               <kvknummer/>
               <naamaccountant/>
               <naamadviseur/>
               <naamcontactpersoon/>
               <naamdirecteur/>
               <omsrechtsvorm/>
               <oprichtingsdatum xsi:nil="true"/>
               <premiespaarregeling/>
               <premiespaarregelingscode/>
               <rechtsvormcode/>
               <relatieidaccountant>0</relatieidaccountant>
               <relatieidadviseur>0</relatieidadviseur>
               <relatieiddirecteur>0</relatieiddirecteur>
               <relatienummer>3540974</relatienummer>
               <rsin>0</rsin>
               <sbicode/>
               <spaarloonregeling/>
               <spaarloonregelingscode/>
               <telefooncontactpersoon/>
               <telefooncontactpersoonacc/>
               <telefoonzaak/>
               <vertrouwelijk/>
               <vestigingsnummer>0</vestigingsnummer>
               <werkgeverebl>0</werkgeverebl>
               <woonplaatskvk/>
            </zaak>
         </s:RelatieLezenViaNummerResult>
      </s:RelatieLezenViaNummerResponse>
```

##Fout afhandeling

Op deze wijze worden de berichten afgehandeld, die fout gaan

####Proces:
![Omschrijving afbeelding](/img_level7_relatieservice_foutafhandelingsproces.png)



##Testen

* ####Ping
* ####Relatie Aanmaken
* ####Relatie Muteren

###Voorbeeldberichten

Nog aan te vullen


### Wat gaat er nog fout

- Na het aanmaken van een relatie wordt het nummer extern niet gevuld
- Het toevoegen van gezinsleden werkt niet
- Het verwijderen van gezinsleden werkt niet (bijv. Mijn kind gaat het huis uit). In het mutatiebericht wordt er geen gezinslid meegegeven, terwijl deze meegegeven zou moeten worden met een verwerkingscode 'V'
- Waarom verschijnt er een I in het bericht om een relatie aan te maken?

Nog toe te voegen:

- Werk
- Zaak
- DVO - Dienstverleningsovereenkomst
- Gekoppelde relaties
- Machtigingen
- Incasso via
- VP_FISHJN?? Waarom zit dit er niet in?
- VP_VOLGNUM (Wordt dit teruggeschreven? revisisienummer?)
