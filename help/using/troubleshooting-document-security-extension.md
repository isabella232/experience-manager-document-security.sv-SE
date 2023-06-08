---
title: Felsökning AEM Document Security Extension for Microsoft Office
description: Om du har problem med att installera, konfigurera eller använda AEM Document Security Extension för Microsoft Office följer du instruktionerna i det här dokumentet.
uuid: 61001ca8-a25a-4879-98ac-563a6eb126e7
contentOwner: khsingh
content-type: reference
topic-tags: using
discoiquuid: bdc3f174-e417-4d3e-b3af-972cdcc10133
exl-id: 98f24032-0774-47f8-bcc5-1ee37b417833
source-git-commit: 28137f26afc024d411857d44887bf69fe1ee2b81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Felsökning AEM Document Security Extension for Microsoft Office{#troubleshooting-aem-document-security-extension-for-microsoft-office}

## Felsökning av installations- och konfigurationsproblem {#troubleshootinginstallationandconfiguration}

Om du har problem med att installera och konfigurera AEM Document Security Extension för Microsoft Office måste du följa instruktionerna som listas i - innan du installerar - avsnittet i [installation](installing-configuring-aemdsext.md) artikel.

Om du har installerat och konfigurerat allt enligt dokumentationen kan du läsa följande avsnitt för att se om det finns problem som liknar dem du upplever.

### Document Security Extension kan inte läsas in för Microsoft Office-program {#document-security-extension-fails-to-load-for-microsoft-office-applications}

LoadBehavior-egenskapen i Windows-registret anger körningsbeteendet för plugin-programmet för dokumentsäkerhet. Om egenskapen LoadBehavior är inställd på 3 läses alla plugin-program in automatiskt. Innan du installerar Document Security Extension för Microsoft Office bör du kontrollera att värdet för LoadBehavior-egenskapen är 3.

1. Säkerhetskopiera Windows-registret innan du ändrar det. Detaljerade anvisningar finns i [Så här ändrar du Windows-registret](https://support.microsoft.com/en-us/kb/136393).
1. Gå till toHKEY_CURRENT_USER\Software\Microsoft\Office\Word\Addins\Adobe.DRMIntegration.WordAddin eller HKEY_LOCAL_MACHINE\Software\Microsoft\Office\Word\Addins\Adobe.DRM i Registereditorn.
1. Ange värdet för **LoadBehavior** till 3.

1. Stäng Registereditorn.

Mer information om LoadBehavior finns i [Registerposter för VSTO-tillägg](https://msdn.microsoft.com/en-us/library/bb386106.aspx#LoadBehavior) artikel.

## Felsöka administrativa uppgifter {#admintasks}

I det här avsnittet beskrivs möjliga problem med det installerade AEM Document Security Extension.

### Microsoft Office-program startar inte korrekt när Document Security Extension installeras {#microsoft-office-applications-dont-start-smoothly-on-installing-document-security-extension}

För att Office-programmen ska kunna startas smidigt på en dator som har Document Security Extension installerat och McAfee VirusScan med On Access Scan aktiverat, inaktiverar du alternativet Buffer Overflow Protection i McAfee VirusScan Console.
