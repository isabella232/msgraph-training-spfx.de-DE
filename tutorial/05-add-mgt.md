---
ms.openlocfilehash: ee9addcbcf58fa971b3e67fb3d84cfb36bf275dd
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823374"
---
<!-- markdownlint-disable MD002 MD041 -->

In diesem Abschnitt verwenden Sie das [Microsoft Graph-Toolkit](https://docs.microsoft.com/graph/toolkit/overview) , um die einfache Liste der Ereignisse durch eine umfangreiche Benutzeroberfläche zu ersetzen.

Das Toolkit enthält eine [Agenda-Komponente](https://docs.microsoft.com/graph/toolkit/components/agenda), die für die Darstellung unserer Liste von Ereignissen geeignet ist.

## <a name="update-the-web-part"></a>Aktualisieren des Webparts

1. Öffnen Sie **./src/Webparts/graphTutorial/GraphTutorialWebPart.Module.scss**. Ändern Sie den Wert des `background-color` Attributs im `.row` Eintrag in `$ms-color-white` .

    :::code language="css" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.module.scss" id="rowScssSnippet" highlight="4":::

1. Fügen Sie den folgenden Eintrag in den `.graphTutorial` Eintrag ein.

    :::code language="css" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.module.scss" id="addSocialBtnSnippet":::

1. Öffnen Sie **/src/Webparts/graphTutorial/GraphTutorialWebPart.TS** , und fügen Sie die folgende `import` Anweisung am Anfang der Datei hinzu.

    ```typescript
    import { Providers, SharePointProvider, MgtAgenda } from '@microsoft/mgt';
    ```

1. Fügen Sie die folgende Funktion zur **GraphTutorialWebPart** -Klasse hinzu, um das Toolkit zu initialisieren.

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="onInitSnippet":::

1. Ersetzen Sie die vorhandene `renderCalendarView`-Funktion durch Folgendes.

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="renderCalendarViewSnippet":::

    Dadurch wird die Grundliste durch die **Agenda** -Komponente aus dem Toolkit ersetzt.

1. Erstellen Sie das Webpart, packen Sie es erneut hoch, und aktualisieren Sie dann die Seite, auf der Sie getestet werden.

    ![Screenshot des Webparts mit der Agenda-Komponente](images/mgt-agenda.png)

## <a name="an-alternate-approach"></a>Ein alternativer Ansatz

Zu diesem Zeitpunkt haben Sie folgenden Code:

- Verwendet die **MSGraphClient** , um die Kalenderansicht des Benutzers für die aktuelle Woche aus Microsoft Graph abzurufen.
- Fügen Sie diese Ereignisse zur **Agenda** -Komponente aus dem Microsoft Graph-Toolkit hinzu.

Mit diesem Ansatz haben Sie Vollzugriff auf den Graph-API-Aufruf und können jede Verarbeitung der Ereignisse vor dem gewünschten Rendern durchführen. Wenn dies jedoch nicht erforderlich ist, können Sie dies vereinfachen, indem Sie der **Agenda** -Komponente die Arbeit für Sie erledigen lassen.

Alle Microsoft Graph Toolkit-Komponenten können alle relevanten API-Aufrufe an Microsoft Graph vornehmen. Wenn Sie beispielsweise nur die **Agenda** -Komponente zum Webpart hinzufügen und keine Eigenschaften festlegen, verwendet das Webpart die Standardeinstellungen, um Ereignisse für den aktuellen Tag abzurufen. Schauen wir uns an, wie wir die gleichen Ergebnisse erzielen können, die wir derzeit haben (Ereignisse für die aktuelle Woche).

1. Ersetzen Sie die vorhandene `render` Methode durch Folgendes.

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="alternateRenderSnippet":::

    Anstatt einen API-Aufruf vorzunehmen `render` , fügen Sie nun einfach ein- `mgt-agenda` Element direkt in den HTML-Code ein. Durch Festlegen `date` auf den Anfang der Woche und `days` auf 7 wird durch die Komponente derselbe API-Aufruf wie in der vorherigen Version von vorgenommen `render` .

1. Fügen Sie der **GraphTutorialWebPart** -Klasse die folgende leere Funktion hinzu.

    ```typescript
    private async addSocialToCalendar() {}
    ```

    > [!NOTE]
    > Wir haben auch eine Schaltfläche **Team Soziales hinzufügen** zum Webpart hinzugefügt und die `addSocialToCalendar` Methode als Ereignis-Listener hinzugefügt.  Sie implementieren den Code dahinter im nächsten Abschnitt. Im Moment möchten wir lediglich, dass der Code kompiliert wird.

1. Erstellen Sie das Webpart, packen Sie es erneut hoch, und aktualisieren Sie dann die Seite, auf der Sie getestet werden. Die Ansicht sollte mit dem vorherigen Test übereinstimmen.

### <a name="using-the-toolkit-vs-making-api-calls"></a>Verwenden des Toolkits vs Making API Calls

An diesem Ort Fragen Sie sich vielleicht, warum Sie die Probleme bei der Verwendung der **MSGraphClient** überhaupt durchlaufen haben, wenn das Toolkit die Arbeit für Sie erledigt. Das Toolkit ist für das Rendern von Ergebnissen konzipiert, die Sie von Microsoft Graph Abfragen, beispielsweise eine Liste von Ereignissen. Es gibt jedoch Szenarien, in denen die Erstellung von API-Aufrufen selbst erforderlich ist.

- Alle API-Aufrufe, die keine `GET` Anforderung sind. Beispielsweise Erstellen eines neuen Ereignisses im Kalender oder Aktualisieren der Telefonnummer eines Benutzers.
- API-Aufrufe zum Abrufen von Daten, die als "hinter den Kulissen" verwendet und nicht direkt gerendert werden sollen.
