---
title: AEM Document Security för Microsoft Office - versionsinformation
description: Läs versionsinformationen innan du installerar AEM Document Security 6.2 Extension for Microsoft Office.
uuid: f6ab73d4-ac4e-4fff-9bb8-917b75401653
content-type: reference
topic-tags: installing
discoiquuid: c9342c28-8289-4831-a613-4bc03431f557
exl-id: 582f10bb-60d2-46ed-b81d-5818a040edc6
source-git-commit: 28137f26afc024d411857d44887bf69fe1ee2b81
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---

# AEM Document Security för Microsoft Office - versionsinformation{#aem-document-security-for-microsoft-office-release-notes}

## Nyheter i AEM Document Security för Microsoft Office {#whats-new-in-aem-document-security-for-microsoft-office}

* **Stöd för Office 2019**: Document Security Extension för Microsoft Office har lagt till stöd för Microsoft Office 2019. Det förväntas också fungera med Microsoft Office 2019-skrivbordsprogram som installeras som en del av Office 365.

>[!NOTE]
>
>Dokumentet använder termerna Adobe Experience Manager Document Security för Microsoft Office, Adobe Experience Manager Document Security Extension för Microsoft Office och Document Security Extension för Microsoft Office.

## Installera och konfigurera AEM Document Security Extension for Microsoft Office {#installing-and-configuring-aem-document-security-extension-for-microsoft-office}

Den här versionen av Document Security Extension för Microsoft Office är kompatibel med Adobe LiveCycle Rights Management ES2 och senare samt Document Security för AEM formulär.

Granska informationen i det här dokumentet innan du installerar AEM Document Security Extension för Microsoft Office. Detaljerade installationsanvisningar finns i [Installera och konfigurera AEM Document Security Extension for Microsoft Office](installing-configuring-aemdsext.md) artikel.

## Åtgärdade problem {#fixed-issues}

* Strängar visas lodrätt och fel radbrytningar läggs till i innehållet. (Referensnummer CQ-4201054)

## Kända fel {#known-issues}

### Plugin-program från tredje part stöds inte {#third-party-plug-ins-not-supported}

AEM Document Security Extension för Microsoft Office fungerar inte med plugin-program från tredje part. Avinstallera eventuella plugin-program från tredje part för Microsoft Office innan du installerar Document Security Extension för Microsoft Office.

### Inaktiverade menyalternativ i Microsoft Word, Excel och PowerPoint {#disabled-menu-options-in-microsoft-word-excel-and-powerpoint}

AEM Document Security Extension för Microsoft Office använder inbyggda skyddsfunktioner för att skydda dokument, kalkylblad och presentationer. Det inaktiverar ett fåtal menyalternativ för Excel, Word och PowerPoint.

### Begränsningar för Microsoft Office 2013, 2016 och 2019 {#restrictions-for-microsoft-office}

I Microsoft Office är följande alternativ inte tillgängliga under en skyddad session:

* Microsoft Office 2016 eller Microsoft Office 2019

   * Arkiv > Spara som
   * Arkiv > Historik
   * Arkiv > Dela
   * Arkiv > Exportera
   * Arkiv > Publicera
   * Arkiv > Konto
   * Arkiv > Info > Protect Document/Workbook/Presentation > Kryptera med lösenord
   * Arkiv > Info > Protect-dokument >Lägg till en digital signatur
   * Arkiv > Info > Protect-dokument > Markera som slutgiltigt
   * Alternativet Dela överst till höger

* Microsoft Office 2013

   * Arkiv > Spara som
   * Arkiv > Dela
   * Arkiv > Exportera
   * Arkiv > Konto
   * Arkiv > Info > Protect Document/Workbook/Presentation > Kryptera med lösenord
   * Arkiv > Info > Protect-dokument >Lägg till en digital signatur
   * Arkiv > Info > Protect-dokument > Markera som slutgiltigt

### Öppna ett skyddat dokument från SharePoint Server {#opening-a-protected-document-from-sharepoint-server}

Öppna det skyddade dokumentet: Om du försöker öppna ett skyddat dokument i Document Security Extension för Microsoft Office från SharePoint Server utan att först öppna det Microsoft Office-program som är kopplat till filtypen, t.ex. Microsoft Word, Microsoft Excel eller Microsoft PowerPoint, kanske dokumentet inte öppnas. Ett felmeddelande visas som anger att du har installerat det tillämpliga plugin-programmet. Därför rekommenderar vi att du öppnar det tillhörande Microsoft Office-programmet innan du öppnar ett skyddat dokument i Document Security Extension för Microsoft Office från SharePoint Server.

(Valfritt) Du bör rensa cachemappen innan du öppnar ett skyddat dokument i Document Security Extension för Microsoft Office från SharePoint Server.

När du öppnar ett skyddat dokument från SharePoint Server inaktiveras alla behörigheter i dokumentet, oavsett vilken princip som tillämpades.

### Använd en profil med en dynamisk vattenstämpel på Microsoft Excel 2013-, Microsoft Excel 2016- och Microsoft Excel 2019-filer utan någon skrivare installerad {#apply-a-policy-with-a-dynamic-watermark-to-microsoft-excel-microsoft-excel-and-microsoft-excel-file-with-no-printer-installed}

När du tillämpar en profil med dynamisk vattenstämpel på en Microsoft Excel 2013-, Microsoft Excel 2016- och Microsoft Excel 2019-fil på en dator som inte har några skrivare installerade och sedan sparar filen, visas följande fel: &quot;Internt fel vid användning av dynamisk vattenstämpel.&quot; Det här felet visas också när du öppnar den skyddade filen igen. Vattenstämpeln används inte och den visas inte i Visa > Sidlayout.

### Inaktivera Windows Data Execution Prevention för Office-program som stöds {#disable-windows-data-execution-prevention-for-supported-office-applications}

Vi rekommenderar att du inaktiverar inställningen Windows Data Execution Prevention (DEP) när du använder Document Security Extension för Microsoft Office-program.

### Delade Microsoft Office-filer kan inte skyddas med Document Security Extension {#shared-microsoft-office-files-cannot-be-protected-using-document-security-extension}

När du skyddar en delad Microsoft Office-fil med Document Security Extension inträffar ett fel och den delade filen skyddas inte.

### Starta Office-program på en dator som innehåller Document Security Extension för Microsoft Office och McAfee VirusScan {#starting-office-applications-on-a-machine-containing-document-security-extension-for-microsoft-office-and-mcafee-virusscan}

För att Office-programmen ska kunna startas smidigt på en dator där Document Security är installerat och McAfee VirusScan med On-Access Scan aktiverat, inaktiverar du alternativet Buffer Overflow Protection i McAfee VirusScan Console.

### Installera Document Security Extension för Microsoft Office på en dator med ett Microsoft Office-språk som inte stöds {#installing-document-security-extension-for-microsoft-office-on-a-machine-with-an-unsupported-microsoft-office-language}

Innan du installerar Document Security Extension för Microsoft Office på en dator som har ett Microsoft Office-program med ett språk som inte stöds måste du öppna Office-programmet minst en gång.

### Knappen Synkronisera offline är aktiverad även när en användare inte har offlinebehörigheter {#synchronize-offline-button-is-enabled-even-when-a-user-does-not-have-offline-permissions}

Knappen Synkronisera offline är tillgänglig även om användaren inte har offlinebehörighet för dokumentet. Men om du markerar knappen händer ingenting.

### Inget stöd för testversioner av Microsoft Office {#no-support-for-trial-versions-of-microsoft-office}

Dokumentsäkerhetstillägget för Microsoft Office stöder inte spårversioner av Microsoft Office. Innan du installerar tillägget måste du kontrollera att du har installerat en licensierad version av Microsoft Office och att den är aktiverad.

### Det går inte att öppna skyddade Microsoft Office-filer {#unable-to-open-a-protected-microsoft-office-files}

Om den skyddade vyn i Microsoft Office är aktiverad kan inte Right Management Extension öppna skyddade Microsoft Excel-filer (XLS, XLSX) och skyddade Microsoft PowerPoint-filer (PPT) från en fjärrplats.

### Celler från Microsoft Excel-dokument som innehåller en bild eller bakgrundsfärg visas ovanpå vattenstämpeln {#cells-of-microsoft-excel-document-containing-an-image-or-background-color-appear-on-top-of-watermark}

Om en cell i ett Microsoft Excel-dokument innehåller en bild eller är fylld med bakgrundsfärg och en dynamisk vattenstämpelpolicy används i dokumentet, visas bilden eller bakgrundsfärgen som är ifylld i cellen ovanpå vattenstämpeln och täcker vattenstämpeln.

### Användbarhetsproblem med flera certifikat {#usability-issue-with-multiple-certificates}

Om det finns flera certifikat på klientdatorn och användaren avbryter dialogrutan för val av certifikat visas dialogrutan igen och användaren måste avbryta dialogrutan två gånger.

### Microsoft PowerPoint tillåter redigering av skyddade dokument {#microsoft-powerpoint-allows-editing-protected-documents}

När du försöker redigera ett skyddat dokument visas meddelandet&quot;Du har inte behörighet att ändra det här dokumentet. Du kommer inte att kunna spara ändringarna.&quot; När du har stängt meddelandet kan användarna fortsätta lägga till text eller redigera dokumentet. Men ändringarna som gjorts i de skyddade dokumenten sparas inte.

Ovannämnda beteende är som väntat i PowerPoint 2013, PowerPoint 2016 och PowerPoint 2019.
