---
title: Använda AEM Document Security Extension för Microsoft Office
description: Du kan styra hur mottagarna använder dina profilskyddade filer, oavsett hur mycket du distribuerar dem. Dokumentet förklarar hur du skyddar filer och hur du arbetar med skyddade filer.
uuid: db4abbc8-eb21-4f4a-9950-224ada95ce66
content-type: reference
topic-tags: using
discoiquuid: f4c2460c-174f-4e4d-b804-1eb051d2781e
translation-type: tm+mt
source-git-commit: 21288f7f1c8f786d3c4c363986226038bdb03e26
workflow-type: tm+mt
source-wordcount: '6270'
ht-degree: 0%

---


# Använda AEM dokumentsäkerhetstillägg för Microsoft Office{#using-aem-document-security-extension-for-microsoft-office}

## Protect-filer med AEM Document Security Extension {#usingaemdocumentsecurityextensiontoprotectfiles}

Du kan styra hur mottagarna använder dina profilskyddade filer, oavsett hur mycket du distribuerar dem.

Med Document Security Extension för Microsoft Office kan du utföra följande uppgifter:

* Konfigurera anslutningen till dokumentsäkerhet
* Tillämpa en profil på en fil
* Öppna webbsidorna Dokumentsäkerhet för att skapa och hantera användarprofiler
* Ta bort principskydd från en fil
* Ändra vilken profil som ska tillämpas på en fil
* Öppna webbsidorna Dokumentsäkerhet om du vill återkalla åtkomst till filer eller ändra profilen för filen
* Öppna webbsidorna Dokumentsäkerhet för att visa filens granskningshistorik

### Anslut till en dokumentsäkerhetsserver {#connect-to-a-document-security-server}

Om du tänker tillämpa profiler på filer måste du konfigurera anslutningsinställningarna för dokumentsäkerhet. Beroende på hur Document Security Extension for Microsoft Office installerades kanske du redan har standardanslutningsinställningar. Du kan lägga till anslutningsinställningar för en eller flera instanser av dokumentsäkerhet. Du kan hämta serverinformation från dokumentsäkerhetsadministratören.

Du måste ange den server som du vill använda för att skydda filer eller hantera skyddade filer som standardserver. När du tillämpar en profil på en ny fil eller öppnar webbsidorna Dokumentsäkerhet ansluter Document Security Extension för Microsoft Office till standardservern. Om du skyddar filer med mer än en instans av Dokumentskydd måste du ändra standardserverinställningen när du växlar mellan servrar. Du kan öppna filer som är skyddade av alla instanser av Dokumentskydd så länge du har behörighet att öppna filen.

Om dokumentsäkerhetsservern använder certifikatbaserad autentisering måste du installera certifikatet som du fick på den lokala datorn. Du måste välja certifikatautentisering och ange det certifikat som du vill använda för att autentisera.

När du har konfigurerat anslutningsinställningarna för en instans av Dokumentsäkerhet i ett Microsoft Office-program konfigureras den för alla Word, Excel och PowerPoint.

#### Installera klientcertifikatet {#install-the-client-side-certificate}

Om du måste få åtkomst till webbsidorna Dokumentsäkerhet via certifikatautentisering eller tvåvägsautentisering får du det certifikat som du måste installera på din lokala dator. Du får en certifikatfil (.PFX- eller .P12-fil) och dess lösenord.

1. Spara certifikatfilen på den lokala datorn.
1. Dubbelklicka på certifikatfilen för att öppna guiden Importera certifikat och klicka på **Nästa**.
1. Klicka på **Nästa** om certifikatfilen visas i filnamnsrutan. Klicka på **Bläddra** om du vill hitta ett annat certifikat.
1. Ange lösenordet som du fick och klicka på **Nästa**.
1. I dialogrutan Certifikatarkiv väljer du Placera alla certifikat i följande arkiv och klickar på **Bläddra**.
1. Välj Personal i dialogrutan Välj certifikatarkiv, klicka på **OK**, klicka på **Nästa** och klicka sedan på **Slutför**.

#### Konfigurera anslutningsinställningar {#configure-connection-settings}

1. Välj **Välj Server** på fliken **Dokumentsäkerhet** i Dokumentsäkerhetstillägg för Microsoft Office 2010 och Office 2013.
1. Klicka antingen på **Nytt** om du vill skapa nya anslutningsinställningar eller markera en befintlig anslutning och klicka på **Redigera**.
1. Skriv ett namn för anslutningen i rutan **Namn**. Du kan använda vilket namn som helst.
1. Skriv serveradressen i rutan **Serveradress**.
1. Skriv serverporten i rutan **Port**.
1. (Valfritt) Om du vill komma ihåg ditt användarnamn och lösenord väljer du **Kom ihåg lösenordet på den här datorn** och anger ditt användarnamn och lösenord i lämpliga rutor. Vi rekommenderar att du inte väljer det här alternativet om andra personer har åtkomst till datorn.
1. Klicka på **Anslut till den här servern**. Dokumentsäkerhetstillägget för Microsoft Office försöker ansluta till den angivna servern. Beroende på vilken autentiseringstyp som har angetts gör du något av följande:

   **Användarnamn och lösenord**

   Ange det användarnamn och lösenord som du fick från administratören för dokumentsäkerhet.

   **Certifikatautentisering**

   Välj det här alternativet om du vill välja det certifikat som du har tagit emot och installerat i ditt personliga certifikatarkiv.

   Om bara en autentiseringstyp är konfigurerad för dokumentsäkerhet visas bara det alternativet.

>[!NOTE]
>
>Om du inte kan ansluta till servern kan du försöka öppna webbsidorna Dokumentsäkerhet i Internet Explorer. Om du inte kan ansluta till servern med Internet Explorer, eller om en dialogruta visar en varning om servercertifikatet, kan inte Document Security Extension för Microsoft Office ansluta till servern. Kontakta serveradministratören om du behöver hjälp.

>[!NOTE]
>
>Om du inte kan ansluta till dokumentsäkerhet visas ett meddelande om att användarnamnet och lösenordet är felaktiga. Kontrollera konfigurationsinställningarna och försök igen. Det här meddelandet kan visas om du inte kan ansluta av någon annan anledning. Om du ansluter till servern för första gången kontrollerar du att du har angett servernamnet och porten korrekt.

#### Ange standardservern {#specify-the-default-server}

1. Gör följande:

   * Välj **Välj Server** i Dokumentsäkerhetstillägg för Microsoft Office 2010 och Office 2013 på fliken **Dokumentsäkerhet**.

1. Välj en server som ska anges som standard och klicka på **Ange standard**. En stjärna visas bredvid standardservern.

### Använda autentiseringsproviders från tredje part {#using-third-party-authentication-providers}

Du kan använda autentiseringsleverantörer från tredje part med AEM Forms Document Security. Dessa autentiseringsleverantörer hjälper dig att lägga till ytterligare ett åtkomstlager till de skyddade dokumenten. AEM Forms Document Security har stöd för följande utökade autentiseringsarbetsflöden:

* Utökad autentisering med AEM Forms-standardwebbadress
* Utökad autentisering med en anpassad URL
* Standardarbetsflöde för utökad autentisering med tredjepartsidentitetsleverantörer konfigurerade på AEM Forms på JEE-servern
* Anpassat arbetsflöde för utökad autentisering med tredjepartsidentitetsleverantörer konfigurerade på AEM Forms på JEE-servern
* Utökad autentisering med anpassad sida för att lista SAML-autentiseringar

#### Utökad autentisering med AEM Forms-standardwebbadress {#extended-authentication-using-default-aem-forms-url}

Du kan använda AEM Forms-standardwebbadressen för utökad autentisering. Standardlandningssidan innehåller Adobe-branding. Dessutom används standardinställningarna för AEM Forms när AEM Forms-URL används som standard för utökad autentisering.

Utför följande steg för att aktivera utökad autentisering med standardURL för landning i Adobe:

1. Öppna användargränssnittet för AEM Forms Admin.
1. Navigera till Tjänster > Dokumentsäkerhet > Konfiguration > Serverkonfiguration.
1. Aktivera alternativet Tillåt utökad autentisering.
1. Ange URL:en för utökad autentisering. Standardwebbadressen är http://localhost:8080/edc/extendedauthentication/welcome.jsp.

   Klicka på **[!UICONTROL Spara]**.

   >[!NOTE]
   >
   >Använd ett fullständigt kvalificerat värdnamn i URL:en. Vi rekommenderar att du använder HTTPS-protokollet.

   Nu är AEM Forms dokumentsäkerhet konfigurerat att använda utökad autentisering med AEM Forms standardstartadress.

   ![](assets/third-party-authentication.png)

#### Utökad autentisering med en anpassad landnings-URL {#extended-authentication-with-a-custom-landing-url}

Du kan använda en anpassad URL för utökad autentisering. Det ger flexibilitet att visa en anpassad autentiseringssida med anpassad varumärkning. Exempel: varumärkning för din organisation.

Du kan paketera den anpassade autentiseringssidan i en krigsfil och distribuera krigsfilen till AEM Forms-servern. Krigsfilen innehåller fullständig logik för att godkänna inloggningsuppgifter och autentisera mot AEM Forms-servern. AEM Forms Document Security har följande krav för den anpassade autentiseringssidan:

* Autentiseringssidan ska skicka användarnamn som j_username och password som j_password. Sidan ska också skicka source_url och login_url som dolda parametrar.
* När autentiseringen är klar bör sidan stängas automatiskt.

Utför följande steg för att aktivera utökad autentisering med en anpassad landnings-URL:

1. Distribuera den anpassade autentiserings-krigsfilen till AEM Forms-servern.
1. Öppna användargränssnittet för AEM Forms Admin.
1. Navigera till Tjänster > Dokumentsäkerhet > Konfiguration > Serverkonfiguration.
1. Aktivera alternativet Tillåt utökad autentisering och ange en anpassad URL för utökad autentisering.
1. Lägg till följande poster i filen config.xml under SSO-noden efter posten *&lt;node name=&quot;AllowedUrls&quot;>*:

   >[!NOTE]
   >
   >&lt;entry>!discoiqbr!&lt;entry>!discoiqbr!&lt;entry>!discoiqbr!

   Stegvis information om hur du uppdaterar filen config.xml finns i [Redigera konfigurationsfilen för dokumentsäkerhet manuellt](https://helpx.adobe.com/aem-forms/6-3/admin-help/configuring-client-server-options.html#manually_editing_the_document_security_configuration_file).

   Nu är AEM Forms dokumentsäkerhet konfigurerat att använda utökad autentisering med en anpassad landnings-URL

#### Standardarbetsflöde för utökad autentisering med identitetsleverantörer från tredje part konfigurerade på AEM Forms-servern {#default-extended-authentication-workflow-with-third-party-identity-providers-configured-on-aem-forms-server}

Utökad autentisering kan använda olika typer av autentisering som är tillgängliga på AEM Forms-servern. Exempel: SAML, [Fler exempel].

Obs! Om SAML-providers är konfigurerade på AEM Forms-servern visas en sida med alla identitetsleverantörer som konfigurerats för SAML-autentisering innan landnings-URL:en visas.

Följande skärm visas när ett skyddat dokument öppnas i Acrobat.

#### Anpassat arbetsflöde för utökad autentisering när SAML-providers konfigureras på AEM Forms-servern {#custom-extended-authentication-workflow-when-saml-providers-are-configured-on-aem-forms-server}

Om SAML-providers är konfigurerade på AEM Forms-servern visas en sida med alla identitetsleverantörer som konfigurerats för SAML-autentisering innan landnings-URL:en visas.

Krävs för att konfigurera ett anpassat, utökat autentiseringsarbetsflöde när SAML-providers har konfigurerats på AEM Forms-servern:

* SAML-autentiseringar har konfigurerats på AEM Forms-servern
* Anpassat krig, som innehåller en anpassad autentiseringssida och fullständig logik för att acceptera inloggningsuppgifter och autentisera mot AEM Forms-servern, distribueras till AEM Forms-servern.

#### Använda anpassad sida för att lista SAML-autentiseringar {#using-custom-page-for-listing-saml-authentications}

Du kan också visa en anpassad sida som innehåller alla autentiseringsproviders som är konfigurerade på AEM Forms-servern. Så här skapar du en sådan sida:

1. Paketera den anpassade autentiseringssidan i en krigsfil och distribuera krigsfilen till AEM Forms-servern. Krigsfilen innehåller fullständig logik för att godkänna inloggningsuppgifter och autentisera mot AEM Forms-servern.
1. Öppna användargränssnittet för AEM Forms Admin och gå till **[!UICONTROL Inställningar]** **[!UICONTROL Användarhantering]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Inställningar för SAML-tjänstleverantör]**.
1. Lägg till följande i fältet Egna egenskaper och klicka på **[!UICONTROL Spara]**.

   *saml.sp.discovery.url=/demoJSP/saml_discovery.jsp*

   Nu är AEM Forms dokumentsäkerhet konfigurerad att visa en anpassad sida som innehåller alla konfigurerade autentiseringsproviders.

### Hämta ett användarkonto {#obtaining-a-user-account}

Om du inte redan har ett Document Security-konto kan Document Security starta registreringsprocessen när dessa händelser inträffar:

* En dokumentsäkerhetsanvändare som vill skicka en principskyddad fil till dig lägger till dig i en profil.
* Dokumentsäkerhetsadministratören skapar ett konto åt dig.

När du har registrerat och aktiverat ditt konto kan du använda principskyddade filer som du har fått behörighet att använda via en profil.

>[!NOTE]
Om du får en profilskyddad fil och inte har något dokumentskyddskonto, eller om du får en inbjudan att registrera dig, kontaktar du den person som skickade filen till dig för att få hjälp.

Om du får en e-postregistreringsinbjudan från Document Security kan du registrera dig genom att använda URL:en i e-postmeddelandet för att öppna onlineregistreringssidan. När du har registrerat dig får du ett andra meddelande om hur du aktiverar ditt konto.

#### Hämta ett externt användarkonto {#obtain-an-external-user-account}

1. Öppna e-postmeddelandet om registrering av dokumentsäkerhet. Den URL som meddelandet innehåller är en länk till dokumentsäkerhetssidan för registrering av externa användare. Om du inte får något registreringsmeddelande kontaktar du den person som skickade filen.
1. Klicka på URL:en eller kopiera den och klistra in den i webbläsaren.
1. Skriv ditt namn, organisation och lösenord i rutorna. Lösenordet kan bestå av en kombination av åtta tecken.

   >[!NOTE]
   Se till att du väljer ett lösenord som är enkelt att komma ihåg; ingen metod finns för att hitta glömda lösenord.

1. Klicka på **Registrera**. Ett meddelande visas som informerar dig om att du kan söka efter ett aktiveringsmeddelande via e-post.
1. Öppna bekräftelsemeddelandet om registrering av dokumentsäkerhet.
1. Klicka på den URL som visas i meddelandet.
1. Klicka på länken till inloggningssidan.
1. I rutan **Användarnamn** skriver du den e-postadress du registrerade under med Dokumentsäkerhet. Den här e-postadressen är ditt standardanvändarnamn för dokumentsäkerhet.
1. I rutan **Lösenord** skriver du lösenordet som du skapade när du registrerade dig.
1. Klicka på **Logga in**.

### Skapa och hantera profiler {#creating-and-managing-policies}

Om du har behörighet från administratören för dokumentsäkerhet kan du skapa profiler som ska tillämpas på dina egna filer på sidan Profiler på webbsidorna Dokumentsäkerhet.

Vissa principinställningar som är tillgängliga för att skapa profiler på webbsidorna Dokumentsäkerhet stöds inte för Word-, Excel- och PowerPoint-filer. Följande tabeller beskriver hur principbehörigheterna mappar till Word-, Excel- och PowerPoint-funktioner.

<table>
 <thead>
  <tr>
   <th><p>Behörigheter</p></th>
   <th><p>Stöd för Word, Excel och PowerPoint</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Skriv ut &gt; Inte tillåtet</p></td>
   <td><p>Det är inte tillåtet att skriva ut filen.</p></td>
  </tr>
  <tr>
   <td><p>Skriv ut &gt; Tillåtet</p></td>
   <td><p>Det är tillåtet att skriva ut filen.</p><p><strong>Obs</strong>:  <i>Om en profil ger behörigheten Kopiera men inte behörigheten Skriv ut, kan innehåll som kopieras till en annan fil skrivas ut.</i></p></td>
  </tr>
  <tr>
   <td><p>Skriv ut &gt; Låga rader. Endast</p></td>
   <td><p>Ej relevant.</p></td>
  </tr>
  <tr>
   <td><p>Ändra &gt; Alla</p></td>
   <td><p>Filen kan ändras.</p><p>När den här behörigheten inte ges kan du inte ändra skyddade Word- och Excel-filer. Du kan ändra PowerPoint-filer men inte spara ändringarna eller visa bildspel för ändrade filer.</p></td>
  </tr>
  <tr>
   <td><p>Ändra &gt; Inte tillåtet</p></td>
   <td><p>Användare kan inte ändra skyddade filer.</p></td>
  </tr>
  <tr>
   <td><p>Ändra &gt; Ändra sidor</p></td>
   <td><p>Ej relevant.</p><p>Inkluderar infogning, borttagning och rotering av sidor.</p></td>
  </tr>
  <tr>
   <td><p>Ändra &gt; Fill &amp; Sign</p></td>
   <td><p>Ej relevant.</p></td>
  </tr>
  <tr>
   <td><p>Offline</p></td>
   <td><p>Filen kan öppnas offline.</p></td>
  </tr>
  <tr>
   <td><p>Kopiera</p></td>
   <td><p>Filinnehåll kan kopieras till andra filer.</p></td>
  </tr>
  <tr>
   <td><p>Skärm Reader </p></td>
   <td><p>Skärmläsare (enheter för användare med nedsatt syn) kan läsa filinnehållet.</p></td>
  </tr>
  <tr>
   <td><p>Giltighet för behörighet</p></td>
   <td><p>Stöds.</p></td>
  </tr>
 </tbody>
</table>

<table>
 <thead>
  <tr>
   <th><p>Allmänna inställningar</p></th>
   <th><p>Stöd för Word, Excel och PowerPoint</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Giltighetsperiod</p></td>
   <td><p>Stöds.</p></td>
  </tr>
  <tr>
   <td><p>Granskningsdokument</p></td>
   <td><p>Stöds.</p></td>
  </tr>
  <tr>
   <td><p>Automatisk offlinelåneperiod</p></td>
   <td><p>Stöds.</p></td>
  </tr>
  <tr>
   <td><p>Externa auktoriseringsleverantörer</p></td>
   <td><p>Stöds.</p></td>
  </tr>
 </tbody>
</table>

<table>
 <thead>
  <tr>
   <th><p>Avancerade inställningar</p></th>
   <th><p>Stöd för Word, Excel och PowerPoint</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Dynamiska vattenstämplar</p></td>
   <td><p>Stöds.</p></td>
  </tr>
  <tr>
   <td><p>Plugin-program för certifiering</p></td>
   <td><p>Ej relevant.</p></td>
  </tr>
  <tr>
   <td><p>Krypteringsalgoritm och nyckellängd </p></td>
   <td><p>Alla alternativ stöds.</p></td>
  </tr>
  <tr>
   <td><p>Dokumentbegränsning</p></td>
   <td><p>Allt filinnehåll krypteras alltid oavsett inställningen i profilen.</p></td>
  </tr>
  <tr>
   <td><p>Felmeddelande vid nekad åtkomst</p></td>
   <td><p>Stöds.</p></td>
  </tr>
 </tbody>
</table>

Mer information om hur du skapar och hanterar profiler finns i [Slutanvändarhjälpen för dokumentsäkerhet](http://help.adobe.com/en_US/AEMForms/6.1/RMHelp/).

### Använd profiler {#applying-policies}

Du kan tillämpa alla tillgängliga profiler på en fil, inklusive profiler som du har skapat och profiler som är en del av principuppsättningar som du har tillgång till. Innan du tillämpar en profil måste du spara filen.

När du har tillämpat en profil läggs den till i listan Senast använda på menyn AEM dokumentsäkerhet för att göra det enklare för dig att tillämpa de profiler som du använder oftast. Om du använder mer än en instans av Dokumentskydd visar listan Senast använda bara profiler för den server som du för närvarande är ansluten till eller för standardservern om du ännu inte har loggat in på en instans av Dokumentsäkerhet.

>[!NOTE]
Du kan bara tillämpa profiler på Word-dokumentfiler (.doc, även.docx och .docm i Microsoft Office 2010 och 2013), Excel-arbetsboksfiler (.xls, även .xlsx och .xlsm i Microsoft Office 2010 och 2013) och PowerPoint-presentationsfiler (.ppt, även .pptx, och .pptm i Microsoft Office 2010 och 2013). Du kan inte använda profiler på Word-mallfiler (.dot), Excel-mallfiler (.xlt) och PowerPoint-designmallfiler (.pot).

#### Använd en profil {#apply-a-policy}

1. Välj **Skydda > Välj profil** i Dokumentsäkerhetstillägg för Microsoft Office 2010 och 2013 på fliken **Dokumentsäkerhet**.

   Om du har valt användarnamn och lösenord som autentiseringsmetod på servern och ännu inte har angett inloggningsinformation för dokumentsäkerhet visas en dialogruta med ditt användarnamn och lösenord.

1. Välj en profil i listan och klicka på **Använd**.
1. Spara filen.

#### Använd en nyligen använd princip {#apply-a-recently-used-policy}

1. I Document Security Extension för Microsoft Office 2010 och 2013 väljer du **Skydda > ***[Principnamn]* på fliken **Dokumentsäkerhet**.
1. Spara filen.

## Arbeta med skyddsskyddade filer {#usingaemdocumentsecurityextensionpolicyprotectedfiles}

Policyskyddade filer innehåller immateriell egendom som ägs av filutgivaren och skyddas av Dokumentsäkerhet.

Du kan använda principskyddade filer oavsett om du är intern eller extern i förhållande till filutgivarens organisation. Om du vill öppna principskyddade filer måste du känna igen dig genom Document Security, antingen genom att inkludera dem i en länkad LDAP- eller Active Directory-lista, läggas till som lokal användare för LiveCycle eller AEM formulär i JEE, eller genom att registrera dig med Document Security efter att ha bjudits in som användare.

Om du får en profilskyddad fil och inte har något dokumentskyddskonto, eller om du får en inbjudan att registrera dig, kontaktar du den person som skickade filen till dig för att få hjälp.

### Arbeta med principskyddade filer i Microsoft Office {#working-with-policy-protected-files-in-microsoft-office}

Document Security Extension för Microsoft Office begränsar vissa funktioner i Word, Excel och PowerPoint för att skydda filutgivarens immateriella egendom. Om du inte har behörighet att ändra filen kan du inte spara ändringar i den.

Om du arbetar med en principskyddad fil kanske vissa produktfunktioner inte är tillgängliga eller inte fungerar som vanligt. Om du även har en oskyddad fil öppen aktiveras de flesta funktioner för den oskyddade filen, förutom de som gör att du kan importera eller kopiera innehåll från en principskyddad fil som du inte har kopierings- eller exportbehörighet för.

>[!NOTE]
När du använder Office-program som stöder Document Security Extension rekommenderar vi att du inaktiverar inställningen Windows DEP. För att Office-programmen ska kunna startas smidigt på en dator där Document Security Extension är installerat och McAfee VirusScan med On Access Scan aktiverat, inaktiverar du alternativet Buffer Overflow Protection i McAfee VirusScan Console.

Om en funktion inte är tillgänglig är kommandonamnet på menyn och den relaterade verktygsfältsknappen inte tillgängliga. När du håller muspekaren över kommandot eller knappen i dokumentsäkerhetstillägget för Microsoft Office visas ett verktygstips som anger att kommandot inte är tillgängligt av Dokumentsäkerhet.

### Öppnar principskyddade filer {#opening-policy-protected-files}

Du kan öppna principskyddade filer på samma sätt som du använder för att öppna andra filer. Om du inte redan är inloggad på Dokumentsäkerhet uppmanas du att göra det, såvida du inte inte är ansluten till Internet och kan öppna filen offline. Om du avbryter inloggningen nekas åtkomst.

Om du inte har behörighet att öppna filen informeras du om att åtkomst nekas. Om filåtkomsträttigheterna har återkallats kan du även dirigeras till en uppdaterad version av filen om en sådan finns tillgänglig. Om du inte kan öppna en principskyddad fil kontaktar du filutgivaren.

När en skyddad fil är öppen anges det i texten i namnlisten att filen är skyddad AEM dokumentsäkerhet.

När du öppnar ett skyddat dokument i Document Security Extension för Microsoft Office från SharePoint Server kontrollerar du att det Microsoft Office-program som är kopplat till filtypen, t.ex. Microsoft Word, Microsoft Excel eller Microsoft PowerPoint, är öppet. Om du försöker öppna filen utan att öppna det associerade programmet kanske inte dokumentet öppnas och ett felmeddelande om att du måste installera det tillämpliga plugin-programmet visas. Förutom att öppna det program som krävs bör du rensa cachemappen innan du öppnar ett skyddat dokument i Document Security Extension för Microsoft Office från SharePoint Server. När du öppnar ett skyddat dokument från SharePoint Server inaktiveras dessutom alla behörigheter i dokumentet, oavsett vilken princip som tillämpades.

Beroende på vilken autentiseringsmetod som har implementerats för dokumentsäkerhet kan du uppmanas att välja autentiseringsmetod när du öppnar ett skyddat dokument. Om Dokumentsäkerhet har stöd för mer än en autentiseringsmetod visas autentiseringsalternativen för dig. Om t.ex. Document Security-servern tillhandahåller både användarnamn/lösenord och certifikatautentisering kan du välja lämplig autentiseringsmetod. Om certifikatbaserad autentisering är aktiverat uppmanas du att använda certifikatet som du har tagit emot och installerat.

Användarupplevelsen när skyddade filer öppnas beror på konfigurationen för ömsesidig autentisering på servern. Om bara ett giltigt klientcertifikat är installerat visas ingen autentiseringsdialogruta och filerna öppnas. Om flera klientcertifikat är installerade på en dator visas en autentiseringsdialogruta. Användaren måste välja ett giltigt certifikat för att kunna öppna den skyddade filen.

### Ta bort principskydd från en fil {#removing-policy-protection-from-a-file}

Om du får ta bort skyddsprofiler från filer som du har skyddat. Om du gör det skyddas filen inte längre av Dokumentsäkerhet.

1. Välj **Ta bort** på fliken **Dokumentsäkerhet** i Dokumentsäkerhetstillägg för Microsoft Office 2010 och 2013.

   Om du ännu inte har angett någon inloggningsinformation för dokumentsäkerhet visas en dialogruta med ditt användarnamn och lösenord.

>[!NOTE]
Om du inte kan ta bort en profil från en fil som du har skyddat kontaktar du en säkerhetsadministratör för dokumentet.

### Visa säkerhetsinställningar {#viewing-security-settings}

Du kan visa de behörigheter som du har för den aktuella filen för utskrift, kopiering från, ändring och åtkomst offline, tillsammans med filens giltighetsperiod.

I Document Security Extension för Microsoft Office 2010 visas din behörighet för filen i gruppen Security Status på fliken Document Security.

Gör följande:

* I Document Security Extension för Microsoft Office 2010 och 2013 klickar du på ett objekt på fliken **Dokumentsäkerhet** i gruppen **Säkerhetsstatus**.

### Spara dokument när principen för automatisk tillämpning är aktiverad {#saving-documents-when-auto-apply-policy-is-enabled}

Om administratören har aktiverat funktionen för att tillämpa automatiskt, skyddas alla dokument som du skapar eller redigerar automatiskt när du sparar dokumentet.

Om Automatiskt tillämpad profil är aktiverad uppmanas du att logga in på dokumentsäkerhetsservern. Du måste ange ditt användarnamn och lösenord för att kunna autentiseras av servern. Om du har angett rätt inloggningsuppgifter sparas och skyddas dokumentet.

>[!NOTE]
Om du inte kan logga in på Dokumentskydd kan det hända att dokumentet inte sparas. Detta beror på hur administratören har konfigurerat principen för autotillämpning. Fråga administratören om hur dokument hanteras i den här situationen.

### Synkroniserar för offlineåtkomst {#synchronizing-for-offline-access}

Med hjälp av profiler kan du öppna filer när du är offline och inte är ansluten till Dokumentsäkerhet. Du måste tidigare ha loggat in på Dokumentsäkerhet för att kunna upprätta dina autentiseringsuppgifter med servern innan du kan arbeta offline. Om du tänker arbeta med filer offline rekommenderar vi att du synkroniserar med dokumentskyddet innan du kopplar från för att säkerställa att principinställningarna för filerna är uppdaterade med servern. Vi rekommenderar att du även öppnar filen online en gång innan du öppnar den offline. Om du inte öppnar filen online eller synkroniserar med servern kan du fortfarande använda profilskyddade filer offline. Låneperioden för offlinelån får dock inte ha gått ut och principinställningarna för filen får inte ha ändrats sedan du senast synkroniserade manuellt eller automatiskt med servern.

Gör följande:

* Välj **Synkronisera offline** på fliken **Dokumentsäkerhet** i Document Security Extension för Microsoft Office 2010 och 2013.

   ***Obs!**: Knappen Synkronisera offline är tillgänglig även om användaren inte har offlinebehörighet för dokumentet. Men om du markerar knappen händer ingenting. *

### Arbeta med dynamiska vattenstämplar {#working-with-dynamic-watermarks}

Document Security Extension for Microsoft Office har stöd för dynamiska textbaserade vattenstämplar i policyskyddade dokument. En dynamisk vattenstämpel kan innehålla information som kan ändras, t.ex. datum, tid, användarnamn eller principens namn. Om en användare skriver ut en principskyddad fil och filen innehåller en dynamisk vattenstämpel och behörighet att skriva ut, visas vattenstämpeln i utdata.

Document Security Extension stöder inte avancerade vattenstämpelfunktioner som PDF-baserade vattenstämplar, flera element i en vattenstämpel, textformateringsalternativ och sidintervall.

Du skapar en dynamisk vattenstämpel med webbsidorna Dokumentsäkerhet. Mer information om hur du skapar och inkluderar dynamiska vattenstämplar i ett policyskyddat dokument finns i [Slutanvändarhjälpen för dokumentsäkerhet](http://www.adobe.com/go/learn_lc_euRightsMgmt_11).

Document Security Extension for Microsoft Office har stöd för följande vattenstämpelfunktioner:

<table>
 <thead>
  <tr>
   <th><p>Vattenstämpelalternativ för dokumentskydd</p></th>
   <th><p>Stöd för Word, Excel och PowerPoint</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Principnamn</p></td>
   <td><p>Stöds.</p></td>
  </tr>
  <tr>
   <td><p>Vattenstämpelnamn</p></td>
   <td><p>Stöds.</p></td>
  </tr>
  <tr>
   <td><p>Använd som bakgrund</p></td>
   <td><p>Visningsbeteendet för en dynamisk vattenstämpel är detsamma oavsett om du väljer Använd som bakgrund eller inte.</p><p>För Word 2010 och 2013 visas dynamiska vattenstämplar bara i Utskriftslayout och Förhandsgranska. </p><p>För Excel 2010 och 2013 visas det också i vyerna Förhandsgranska och Sidlayout.</p></td>
  </tr>
  <tr>
   <td><p>Lodrät position</p></td>
   <td><p>Stöds</p></td>
  </tr>
  <tr>
   <td><p>Vågrät position</p></td>
   <td><p>Stöds</p><p>I Excel 2010 och 2013 fungerar inte den vågräta placeringen av vattenstämplar med punkter.</p></td>
  </tr>
  <tr>
   <td><p>Skala</p></td>
   <td><p>Stöds</p></td>
  </tr>
  <tr>
   <td><p>Position</p></td>
   <td><p>Stöds</p></td>
  </tr>
  <tr>
   <td><p>Opacitet</p></td>
   <td><p>Stöds</p></td>
  </tr>
 </tbody>
</table>

### Öppna webbsidorna för dokumentsäkerhet {#opening-the-document-security-web-pages}

Du kan öppna webbsidorna Dokumentsäkerhet för att skapa och uppdatera dina användarprofiler och visa status och granskningsinformation om dina profilskyddade filer. Du kan också använda webbsidorna Dokumentsäkerhet för att ändra profiler eller återkalla åtkomst för en profilskyddad fil.

Om du vill öppna webbsidorna Dokumentsäkerhet går du till Dokumentsäkerhetstillägg för Microsoft Office 2010 och 2013 och väljer **Dokumentsäkerhet** på fliken **Skapa och hantera profiler**. Om du ännu inte har angett någon inloggningsinformation öppnas webbläsaren på serverinloggningssidan.

### Ändrar profiler {#changing-policies}

Om du har behörighet, vanligtvis som dokumentsäkerhetsadministratör eller filutgivare, kan du senare tillämpa en annan profil på en fil eller ändra inställningarna för den profil som används för tillfället.

Om du vill ändra inställningarna för en profil använder du webbsidorna Dokumentsäkerhet.

1. Gör följande:

   * Välj **Skydda > Ändra säkerhet** på fliken **Dokumentsäkerhet** i Dokumentsäkerhetstillägg för Microsoft Office 2010 eller 2013.

1. Välj en profil i listan och klicka på **Använd**.

### Återkallar filåtkomstbehörighet {#revoking-file-access-privileges}

Du kan återkalla möjligheten att öppna filer som du har skyddat. När du återkallar åtkomsträttigheter för en fil kan du även ange det meddelande som visas för alla som försöker öppna filen och URL:en till en uppdaterad version av filen om du ersätter den med en ändrad kopia.

1. Gör följande:

   * Välj **Återkalla** på fliken **Dokumentsäkerhet** i Dokumentsäkerhetstillägg för Microsoft Office 2010 och 2013.

   Webbsidorna Dokumentsäkerhet öppnas på sidan Återkalla dokument.

1. Ange ett meddelande som ska visas och, om det är tillgängligt, en URL för den uppdaterade versionen och klicka på **OK**.

Mer information om hur du återkallar behörigheter för filåtkomst finns i [Slutanvändarhjälpen för dokumentsäkerhet](http://help.adobe.com/en_US/AEMForms/6.1/RMHelp/).

Åtkomstbehörigheterna kan återställas via webbsidorna Dokumentsäkerhet.

### Visa filgranskningshistoriken {#viewing-the-file-audit-history}

Dokumentsäkerhet kan spara granskningshistorik för principskyddade filer så att du kan granska de åtgärder som användarna utför på filerna.

Granskade händelser för Word-, Excel- och PowerPoint-filer innehåller följande:

**Skydda en ny** dokumentprincip som tillämpas på en fil

**Visa** dokumentfil öppnad

**Stäng** dokumentfilen stängd

**Återkalla** dokumentåtkomstbehörighet borttagen för fil

**Ångra** DocumentAccess-behörighet som returnerats till filen

**Ändra** DocumentFile ändrad och sparad lokalt

**Skriv ut högupplöst** fil utskriven

**Ändra skydd** för säkerhetshanterarprincip borttaget från fil

**Byt profil på** dokumentNy princip som tillämpas på filen från webbsidorna Dokumentsäkerhet

### Visa granskningshistorik för en fil {#view-the-audit-history-for-a-file}

Välj **Granskningshistorik** på fliken **Dokumentsäkerhet** i Dokumentsäkerhetstillägg för Microsoft Office 2010 och 2013.

Webbsidorna Dokumentsäkerhet öppnas på sidan Händelser där granskade händelser för den aktuella filen visas.

### Begränsade funktioner i Microsoft Office {#microsoft-office-restricted-features}

För att skydda din immateriella egendom är vissa Microsoft Office-funktioner inte tillgängliga när en principskyddad fil är öppen. Listan över funktioner som inte är tillgängliga beror på vilka behörigheter som ges till den aktuella användaren. Vissa funktioner är bara otillgängliga för skyddade filer och andra är inte tillgängliga för alla filer när du befinner dig i en skyddad session. Vanligtvis är du i en skyddad session från den tidpunkt du öppnar en principskyddad fil tills du stänger programmet eller sessionen förfaller.

De flesta profiler ger fullständig behörighet till filutgivaren. Andra användare kan lägga märke till ytterligare funktionsbegränsningar.

Om ett kommando inte är tillgängligt är kommandonamnet på menyn och den relaterade verktygsfältsknappen nedtonade.

>[!NOTE]
Om du tillämpar en princip på en fil som innehåller en länk till en inbäddad fil tillämpas inte principen på den länkade filen. Dokumentskydd för Microsoft Office ger inte skydd för länkade filer.

* Principskyddade Word-, Excel- och PowerPoint-filer kan inte öppnas i webbläsaren Internet Explorer.
* Användare som endast tilldelats behörigheten Ändra kan inte kopiera innehåll till en fil från ett annat program med hjälp av Urklipp i Windows. Användare kan kopiera innehåll till filer genom att aktivera alternativet Microsoft Office Clipboard.
* När du öppnar en principskyddad fil i Microsoft Office är inte Skriv ut skärm-tangenten tillgänglig förrän du stänger programmet eller sessionen förfaller.
* Dokumentsäkerhet för Microsoft Office stöder inte Web-based Distributed Authoring and Versioning (WebDAV). I de flesta fall kan du inte öppna en principskyddad fil från en WebDAV-mapp. Om du kan öppna en principskyddad fil har du inte behörighet att spara, skriva ut, ändra eller kopiera från filen.

Den allmänna säkerhet som gäller för principskyddade filer omfattar följande begränsningar:

Många vanliga funktioner kan begränsas i Word, Excel och PowerPoint under en skyddad session.

Om en principskyddad fil som inte tillåter användaren att göra ändringar är öppen är kommandon som ändrar filen på något sätt inte tillgängliga. Endast kommandon som öppnar eller skapar nya dokument och ändrar programinställningarna är tillgängliga.

#### Begränsningar för Word 2010 och Word 2013 {#word-2010-and-word-2013-restrictions}

Om du öppnar en principskyddad fil i Word blir det inte möjligt att spara automatisk filåterställningsinformation förrän du stänger och startar om Word. Dessutom är funktionerna nedan begränsade i de situationer som beskrivs:

**Arkiv > Nytt > Nytt från** befintligtTillgängligt, men filer som skapats med det här kommandot när en principskyddad fil är öppen går inte att spara. Innehåll i den nya filen kan inte kopieras till en annan fil.

**Arkiv >** Spara begränsad av behörigheten Ändra.

**Arkiv > Spara** som alla alternativ som begränsas av behörigheten Ändra.

**Arkiv >** Skriv utAlla alternativ som begränsas av utskriftsbehörigheten. Inte tillgängligt om inte principen tillåter utskrift med hög upplösning.

**Arkiv > Spara och** skickaAlla alternativ är inte tillgängliga under en skyddad session.

**Arkiv > Info > Protect-dokument > Kryptera med lösenord, Lägg till digital signatur, Markera som slutgiltig, Begränsa behörigheter för** personerInte tillgängligt under en skyddad session.

**Arkiv >** ArbetsflödenInte tillgängligt under en skyddad session.

***Obs **! Möjligheten att starta ett arbetsflöde från 2010 års Microsoft Office-systemversioner av Word, Excel och PowerPoint finns endast i Office Professional Plus 2010, Office Enterprise 2010 och Office Ultimate 2010 samt i den fristående Office 2010-versionen av dessa program.*

**Blogginlägg >** PublishUnavailable under en skyddad session.

**Arkiv > Server > Filserveraktiviteter** MenyInte tillgängligt under en skyddad session.

**Hem > Urklipp >** KopieraBegränsat av behörigheten Kopiera. Om kopiering inte tillåts går det inte att klistra in kopierat innehåll i någon annan fil eller i Office Clipboard. Innehåll kan kopieras inuti den skyddade filen om användaren har ändringsbehörighet.

**Hem > Urklipp >** Klistra in begränsad av behörigheten Ändra.

**Hem > Urklipp > Klistra in** special begränsad av behörigheten Ändra.

**Infoga > Text >** ObjectUnavailable under en skyddad session. Det går inte att infoga principskyddade filer när som helst.

**** MeddelandenDe flesta alternativen på den här fliken är inte tillgängliga under en skyddad session.

**Granska > Korrektur >** Forskning Begränsad av behörigheten Kopiera. Inte tillgängligt om kopiering inte tillåts.

**Granska > Korrektur >** SynonymordbokBegränsad av behörigheten Kopiera. Inte tillgängligt om kopiering inte tillåts.

**Review > Language > Translate > Translate** DocumentEnabled with the Copy permission.

**Review > Language > Translate > Translate Selected** TextEnabled with the Copy permission.

**Review > Language > Translate > Mini** TranslatorEnabled with the Copy permission.

**Granska > Jämför >** JämförInte tillgängligt under en skyddad session. Policyskyddade filer kan inte jämföras när som helst.

**Review > Protect > Block** AuthorsUnavailable during a protected session.

**Granska > Protect > Begränsa** redigeringInte tillgängligt under en skyddad session.

**Visa >** MakronVissa makron begränsas av behörigheten Kopiera och är inte tillgängliga om inte kopiering tillåts.

**TilläggDet** går inte att lägga till eller ta bort under en skyddad session.

**Onlinesamarbete** är inte tillgängligt under en skyddad session.

**Överordnad dokument och** deldokumentUnderdokument styrs av den överordnad dokumentprofilen när de öppnas i det överordnad dokumentet. Om de öppnas separat kan deldokument inte skrivas ut, kopieras från eller ändras.

**** SammanfattningEj tillgängligt under en skyddad session.

**Bildrutor (och alla relaterade kommandon)** är inte tillgängliga under en skyddad session.

**Dokumentpanelen** är inte tillgänglig under en skyddad session.

**Utvecklare > Dokumentmall** är inte tillgänglig under en skyddad session. Om du vill komma åt det här kommandot väljer du Arkiv > Alternativ > Anpassa > fliken Utvecklare > Mallar > Dokumentmall.

**Disposition > Överordnad dokument > Skapa underdokument, Infoga** underdokumentInte tillgängligt under en skyddad session.

#### Begränsningar för Excel 2010 och Excel 2013 {#excel-2010-and-excel-2013-restrictions}

De funktioner som anges nedan är begränsade i de situationer som beskrivs nedan:

**Arkiv > Nytt > Nytt från** befintligtTillgängligt, men det går inte att spara filer som skapats med det här kommandot under en skyddad session. Innehåll i den nya filen kan inte kopieras till en annan fil.

**Arkiv > Spara, Spara** som begränsad av behörigheten Ändra.

**Arkiv > Spara som >** PDFUnavailable during a protected session.

**Arkiv >** Skriv utBegränsat av utskriftsbehörighet. Inte tillgängligt om inte principen tillåter utskrift med hög upplösning.

**Arkiv > Info > Protect** DocumentUnavailable under en skyddad session.

**Arkiv > Info > Protect** WorkbookInte tillgängligt under en skyddad session.

**Arkiv > Spara och** skickaInte tillgängligt under en skyddad session.

**Arkiv > Alternativ > Tillägg** kan inte läggas till eller tas bort under en skyddad session.

**Arkiv >** ArbetsflödenInte tillgängligt under en skyddad session.

***Obs **! Möjligheten att starta ett arbetsflöde från 2010 års Microsoft Office-systemversioner av Word, Excel och PowerPoint finns endast i Office Professional Plus 2010, Office Enterprise 2010 och Office Ultimate 2010 samt i den fristående Office 2010-versionen av dessa program.*

**Arkiv > Server > Filserveraktiviteter** MenyInte tillgängligt under en skyddad session.

**Hem > Urklipp >** KopieraBegränsat av behörigheten Kopiera. Om kopiering inte tillåts går det inte att klistra in kopierat innehåll i någon annan fil eller i Microsoft Office Clipboard. Innehåll kan kopieras inuti den skyddade filen om användaren har ändringsbehörighet.

**Hem > Urklipp >** Klistra in begränsad av behörigheten Ändra.

**Hem > Urklipp > Klistra in** special begränsad av behörigheten Ändra.

**Hem > Celler > Format > Flytta eller Kopiera** bladInte tillgängligt under en skyddad session.

**Hem > Celler > Infoga > Infoga** bladInte tillgängligt under en skyddad session.

**Hem > Celler > Ta bort > Ta bort** bladInte tillgängligt under en skyddad session.

**Hem > Redigering > Fyllning > Över** kalkylbladBegränsat av behörigheten Ändra.

**Infoga > Tabeller >** TabellBegränsad av behörigheten Ändra.

**Det går inte att välja Infoga > Tabeller >** Pivottabellprincipskyddade filer i guiden Skapa.

**Infoga > Text >** ObjectUnavailable under en skyddad session. Det går inte att infoga principskyddade filer när som helst.

**Infoga > Text > Sidhuvud och** sidfot Begränsad av behörigheten Ändra. Inte tillgängligt för ett profilskyddat dokument.

**Data > Hämta externa** data från principskyddade filer kan inte importeras.

**Data > Kontur >** Delsummor Begränsat av behörigheten Ändra.

**Data > Dataverktyg > Dataverifiering** Begränsad av behörigheten Ändra.

**Granska > Korrektur >** Forskning Begränsad av behörigheten Kopiera.

**Granska > Korrektur >** SynonymordbokBegränsad av behörigheten Kopiera.

**Granska > Språk >** TranslateRestricted by the Copy permission.

**Granska > Ändringar > Protect** SheetUnavailable under en skyddad session.

**Review > Changes > Protect** WorkbookUnavailable during a protected session.

**Review > Changes > Share** WorkbookUnavailable during a protected session.

**Granska > Ändringar > Protect och Dela** arbetsbokInte tillgängligt under en skyddad session.

**Granska > Ändringar > Tillåt användare att redigera** intervall som inte är tillgängliga under en skyddad session.

**Review > Changes > Track Changes > Highlight** ChangesUnavailable for a policy protected file that contains a dynamic watermark.

**Visa >** Makron Begränsad av behörigheten Ändra.

**Visa > Spara** WorkspaceCommand fungerar inte.

**Utvecklare > XML >** ExpansionspaketVissa makron begränsas av behörigheten Kopiera och är inte tillgängliga om inte kopiering tillåts.

**Formler > Formelgranskning > Felkontroll** begränsad av behörigheten Ändra. Inte tillgängligt om inte ändring tillåts.

**Onlinesamarbete** är inte tillgängligt under en skyddad session.

**Spara** information för automatisk återställning är inte tillgänglig under en skyddad session.

***Obs **: Om du försöker ändra en cell i en principskyddad fil för vilken du inte har behörighet att göra ändringar, visas ett felaktigt varningsmeddelande som anger att du måste ta bort skyddet från filen med kommandot Ta bort bladets skydd. Kommandot Ta bort bladets skydd tar inte bort principskyddet från filen.*

#### Begränsningar för PowerPoint 2010 och PowerPoint 2013 {#powerpoint-2010-and-powerpoint-2013-restrictions}

De funktioner som anges nedan är begränsade i de situationer som beskrivs nedan:

**Arkiv > Nytt > Nytt från** befintligtTillgängligt, men det går inte att spara filer som skapats med det här kommandot under en skyddad session. Innehåll i den nya filen kan inte kopieras till en annan fil.

**Arkiv >** Spara begränsad av behörigheten Ändra.

**Arkiv > Spara** som alla alternativ som begränsas av behörigheten Ändra.

**Arkiv >** Skriv utAlla alternativ som begränsas av utskriftsbehörigheten. Inte tillgängligt om inte principen tillåter utskrift med hög upplösning.

**Arkiv > Spara och** skickaInte tillgängligt under en skyddad session.

**Arkiv > Info > Protect Presentation > Kryptera med lösenord, Lägg till en digital signatur, Markera som slutgiltig, Begränsa behörigheter för** personerInte tillgängligt under en skyddad session.

**Arkiv > PowerPoint-alternativ > Spara** information om automatisk återställning är inte tillgängligt under en skyddad session.

**Arkiv > Server > Filserveraktiviteter** MenyInte tillgängligt under en skyddad session.

**Hem > Urklipp >** KopieraBegränsat av behörigheten Kopiera. Om kopiering inte tillåts går det inte att klistra in kopierat innehåll i dokumentet, i någon annan fil eller i Office Clipboard. Innehåll kan kopieras inuti den skyddade filen om användaren har ändringsbehörighet.

**Hem > Urklipp >** Klistra in begränsad av behörigheten Ändra. Om kopiering inte tillåts går det inte att klistra in kopierat innehåll i dokumentet.

**Hem > Urklipp > Klistra in** special begränsad av behörigheten Ändra.

**Hem > Bilder > Nya bilder > Bilder från disposition, Återanvänd** bilderInte tillgängligt under skyddad session.

**Infoga > Text >** ObjectUnavailable under en skyddad session. Det går inte att infoga principskyddade filer när som helst.

**Design > Bakgrund > Bakgrundsformat, Dölj bakgrundsgrafik, Formatera** bakgrundInte tillgängligt för en principskyddad fil som innehåller en dynamisk vattenstämpel.

**Bildspel > Konfigurera > Spela in** bildspelBegränsat av ändringsbehörighet .

**Granska > Korrektur >** SynonymordbokBegränsad av behörigheten Kopiera.

**Granska > Språk >** TranslateRestricted by the Copy permission.

**Review > Language > Translate > Mini** TranslatorEnabled with the Copy permission.

**Visa > Presentationsvyer > Bildspel** Begränsat av behörigheten Ändra. Om ändringar inte tillåts kan bildspel inte visas om filen har ändrats.

**Visa >** MakronVissa makron begränsas av behörigheten Kopiera och är inte tillgängliga om inte kopiering tillåts.

**TilläggDet** går inte att lägga till eller ta bort under en skyddad session.

**Onlinesamarbete** är inte tillgängligt under en skyddad session.

## Använd autentiseringsproviders från tredje part {#use-third-party-authentication-providers}

Du kan använda autentiseringsleverantörer från tredje part med AEM Forms Document Security. Dessa autentiseringsleverantörer hjälper dig att lägga till ytterligare ett åtkomstlager till de skyddade dokumenten. AEM Forms Document Security har stöd för följande utökade autentiseringsarbetsflöden:

* Utökad autentisering med AEM Forms-standardwebbadress
* Utökad autentisering med en anpassad URL
* Standardarbetsflöde för utökad autentisering med tredjepartsidentitetsleverantörer konfigurerade på AEM Forms på JEE-servern
* Anpassat arbetsflöde för utökad autentisering med tredjepartsidentitetsleverantörer konfigurerade på AEM Forms på JEE-servern
* Utökad autentisering med anpassad sida för att lista SAML-autentiseringar

Detaljerade steg för att konfigurera utökade autentiseringsarbetsflöden finns i [artikeln Extended Authentication Scenarios](http://blogs.adobe.com/livecycle/2011/12/extended-authentication-scenarios.html)

## Ordlista {#glossary}

Mer information om LiveCycle och AEM formulär om JEE-terminologi finns i [Ordlista](http://www.adobe.com/go/learn_aemforms_designer_65).
