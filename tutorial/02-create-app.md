---
ms.openlocfilehash: 5164c68a78837c179636f685d28ddf61f93f8415
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823337"
---
<!-- markdownlint-disable MD002 MD041 -->

In diesem Lernprogramm erstellen Sie ein [clientseitiges SharePoint-Webpart](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts) , das Microsoft Graph verwendet, um den Kalender des Benutzers für die aktuelle Woche abzurufen, und dem Benutzer das Hinzufügen eines Ereignisses zu seinem Kalender gestatten kann.

## <a name="create-a-web-part-project"></a>Erstellen eines WebPart-Projekts

1. Öffnen Sie die Befehlszeilenschnittstelle (CLI) in einem leeren Verzeichnis, in dem Sie das Projekt erstellen möchten. Führen Sie den folgenden Befehl aus, um den SharePoint-Generator zu starten.

    ```Shell
    yo @microsoft/sharepoint
    ```

1. Antworten Sie wie folgt auf die Eingabeaufforderungen.

    - **Wie lautet Ihr Lösungsname?** `graph-tutorial`
    - **Welche Basisplanpakete möchten Sie für Ihre Komponente(n) als Ziel festlegen?** `SharePoint Online only (latest)`
    - **Wohin möchten Sie die Daten verschieben?** `Use the current folder`
    - **Möchten Sie den Mandantenadministratoren erlauben, festzulegen, ob die Lösungen unmittelbar für alle Websites bereitgestellt werden, ohne die Bereitstellung von Features oder das Hinzufügen von Apps zu Websites?** `Yes`
    - **Erfordern die Komponenten in der Lösung Berechtigungen für den Zugriff auf webapis, die eindeutig sind und nicht für andere Komponenten in der ten Ant freigegeben werden?** `No`
    - **Welches Typ von clientseitiger Komponente möchten Sie erstellen?** `WebPart`
    - **Wie lautet der Name Ihres Webparts?** `GraphTutorial`
    - **Wie lautet die Beschreibung Ihres Webparts?** `GraphTutorial description`
    - **Welches Framework möchten Sie verwenden?** `No JavaScript framework`

1. Führen Sie den folgenden Befehl aus, um die Version des Manuskripts im Projekt auf 3,7 zu aktualisieren.

    ```Shell
    npm install @microsoft/rush-stack-compiler-3.7 --save-dev
    ```

1. Öffnen Sie **./tsconfig.jsein** , und ersetzen Sie `rush-stack-compiler-3.3` durch `rush-stack-compiler-3.7` .

1. Öffnen Sie **./tslint.jsein** , und entfernen Sie die- `"no-use-before-declare": true,` Verbindung. Die `no-use-before-declare` Regel ist veraltet und verursacht während des Erstellungsprozesses einen Fehler.

## <a name="install-dependencies"></a>Installieren von Abhängigkeiten

Bevor Sie fortfahren, installieren Sie einige zusätzliche NPM-Pakete, die Sie später verwenden werden.

- [Microsoft Graph-Beschreibungen](https://github.com/microsoftgraph/msgraph-typescript-typings) zur Bereitstellung von IntelliSense für Microsoft Graph-Objekte.
- [Microsoft Graph-Toolkit](https://docs.microsoft.com/graph/toolkit/overview) , um Benutzeroberflächenkomponenten für das Webpart bereitzustellen.
- [Date-FNS](https://date-fns.org/) für hilfreiche Funktionen zum Arbeiten mit Datumsangaben.

```Shell
npm install @microsoft/microsoft-graph-types@1.17.0 --save-dev
npm install @microsoft/mgt@1.3.4 date-fns @2.16.0
```
