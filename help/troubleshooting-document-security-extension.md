---
title: Felsökning AEM Document Security Extension for Microsoft Office
description: Om du har problem med att installera, konfigurera eller använda AEM Document Security Extension för Microsoft Office följer du instruktionerna i det här dokumentet.
uuid: 61001ca8-a25a-4879-98ac-563a6eb126e7
contentOwner: khsingh
content-type: reference
topic-tags: using
discoiquuid: bdc3f174-e417-4d3e-b3af-972cdcc10133
translation-type: tm+mt
source-git-commit: ac26ec61f62d7a3db2429c8a9d3f68b82ba8f77a
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Felsökning AEM dokumentsäkerhetstillägg för Microsoft Office{#troubleshooting-aem-document-security-extension-for-microsoft-office}

## Felsökning av installations- och konfigurationsproblem {#troubleshootinginstallationandconfiguration}

Om du har problem med att installera och konfigurera AEM Document Security Extension för Microsoft Office måste du följa instruktionerna i [installationsartikeln](installing-configuring-aemdsext.md) innan du installerar.

Om du har installerat och konfigurerat allt enligt dokumentationen kan du läsa följande avsnitt för att se om det finns problem som liknar dem du upplever.

### Dokumentsäkerhetstillägget kan inte läsas in för Microsoft Office-program {#document-security-extension-fails-to-load-for-microsoft-office-applications}

LoadBehavior-egenskapen i Windows-registret anger körningsbeteendet för plugin-programmet för dokumentsäkerhet. Om egenskapen LoadBehavior är inställd på 3 läses alla plugin-program in automatiskt. Innan du installerar dokumentsäkerhetstillägget för Microsoft Office kontrollerar du att värdet för LoadBehavior-egenskapen är 3.

1. Säkerhetskopiera Windows-registret innan du ändrar det. Mer information finns i [Ändra Windows-registret](https://support.microsoft.com/en-us/kb/136393).
1. Gå till toHKEY_CURRENT_USER\Software\Microsoft\Office\Word\Addins\Adobe.DRMIntegration.WordAddin eller HKEY_LOCAL_MACHINE\Software\Microsoft\Office\Word\Addins\Adobe.DRM i Registereditorn.
1. Ange värdet för egenskapen **LoadBehavior** till 3.

1. Stäng Registereditorn.

Mer information om LoadBehavior finns i artikeln [Registerposter för VSTO-tillägg](https://msdn.microsoft.com/en-us/library/bb386106.aspx#LoadBehavior).

## Felsöka administrativa uppgifter {#admintasks}

I det här avsnittet beskrivs möjliga problem med det installerade AEM Document Security Extension.

### Microsoft Office-program startar inte korrekt när Document Security Extension {#microsoft-office-applications-dont-start-smoothly-on-installing-document-security-extension} installeras

För att Office-programmen ska kunna startas smidigt på en dator som har Document Security Extension installerat och McAfee VirusScan med On Access Scan aktiverat, inaktiverar du alternativet Buffer Overflow Protection i McAfee VirusScan Console.
