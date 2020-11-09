---
ms.openlocfilehash: c239c1ea6daae99cc5a65b7b95508ccb2a1bf014
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823356"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="b8f43-101">Das SharePoint-Framework stellt die [MSGraphClient](https://docs.microsoft.com/javascript/api/sp-http/msgraphclient?view=sp-typescript-latest) für das tätigen von Anrufen an Microsoft Graph bereit.</span><span class="sxs-lookup"><span data-stu-id="b8f43-101">The SharePoint Framework provides the [MSGraphClient](https://docs.microsoft.com/javascript/api/sp-http/msgraphclient?view=sp-typescript-latest) for making calls to Microsoft Graph.</span></span> <span data-ttu-id="b8f43-102">Mit dieser Klasse wird die [Microsoft Graph-JavaScript-Client Bibliothek](https://github.com/microsoftgraph/msgraph-sdk-javascript)umgebrochen und mit dem aktuell angemeldeten Benutzer vorab authentifiziert.</span><span class="sxs-lookup"><span data-stu-id="b8f43-102">This class wraps the [Microsoft Graph JavaScript Client Library](https://github.com/microsoftgraph/msgraph-sdk-javascript), pre-authenticating it with the current logged on user.</span></span>

<span data-ttu-id="b8f43-103">Da die vorhandene JavaScript-Bibliothek umbrochen wird, ist die Verwendung identisch, und Sie ist vollständig kompatibel mit den Microsoft Graph-Beschreibungen.</span><span class="sxs-lookup"><span data-stu-id="b8f43-103">Because it wraps the existing JavaScript library, its usage is the same, and it's fully compatible with the Microsoft Graph TypeScript definitions.</span></span>

## <a name="get-the-users-calendar"></a><span data-ttu-id="b8f43-104">Abrufen des Kalenders des Benutzers</span><span class="sxs-lookup"><span data-stu-id="b8f43-104">Get the user's calendar</span></span>

1. <span data-ttu-id="b8f43-105">Öffnen Sie **/src/Webparts/graphTutorial/GraphTutorialWebPart.TS** , und fügen Sie die folgenden `import` Anweisungen am Anfang der Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="b8f43-105">Open **./src/webparts/graphTutorial/GraphTutorialWebPart.ts** and add the following `import` statements at the top of the file.</span></span>

    ```typescript
    import { MSGraphClient } from '@microsoft/sp-http';
    import * as MicrosoftGraph from '@microsoft/microsoft-graph-types';
    import { startOfWeek, endOfWeek, setDay, set } from 'date-fns';
    ```

1. <span data-ttu-id="b8f43-106">Fügen Sie die folgende Funktion zur **GraphTutorialWebPart** -Klasse hinzu, um einen Fehler zu rendern.</span><span class="sxs-lookup"><span data-stu-id="b8f43-106">Add the following function to the **GraphTutorialWebPart** class to render an error.</span></span>

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="renderGraphErrorSnippet":::

1. <span data-ttu-id="b8f43-107">Fügen Sie die folgende Funktion hinzu, um die Ereignisse im Kalender des Benutzers zu drucken.</span><span class="sxs-lookup"><span data-stu-id="b8f43-107">Add the following function to print out the events in the user's calendar.</span></span>

    ```typescript
    private renderCalendarView(events: MicrosoftGraph.Event[]) : void {
      const viewContainer = this.domElement.querySelector('#calendarView');
      let html = '';

      // Temporary: print events as a list
      for(const event of events) {
        html += `
          <p class="${ styles.description }">Subject: ${event.subject}</p>
          <p class="${ styles.description }">Organizer: ${event.organizer.emailAddress.name}</p>
          <p class="${ styles.description }">Start: ${event.start.dateTime}</p>
          <p class="${ styles.description }">End: ${event.end.dateTime}</p>
          `;
      }

      viewContainer.innerHTML = html;
    }
    ```

1. <span data-ttu-id="b8f43-108">Ersetzen Sie die vorhandene `render`-Funktion durch Folgendes.</span><span class="sxs-lookup"><span data-stu-id="b8f43-108">Replace the existing `render` function with the following.</span></span>

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="renderSnippet":::

    <span data-ttu-id="b8f43-109">Beachten Sie, was dieser Code tut.</span><span class="sxs-lookup"><span data-stu-id="b8f43-109">Notice what this code does.</span></span>

    - <span data-ttu-id="b8f43-110">Es wird verwendet `this.context.msGraphClientFactory.getClient` , um ein authentifiziertes **MSGraphClient** -Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b8f43-110">It uses `this.context.msGraphClientFactory.getClient` to get an authenticated **MSGraphClient** object.</span></span>
    - <span data-ttu-id="b8f43-111">Der `/me/calendarView` Endpunkt wird aufgerufen, und die `startDateTime` Parameter-und `endDateTime` Abfrageparameter werden auf den Anfang und das Ende der aktuellen Woche festgesetzt.</span><span class="sxs-lookup"><span data-stu-id="b8f43-111">It calls the `/me/calendarView` endpoint, setting the `startDateTime` and `endDateTime` query parameters to the start and end of the current week.</span></span>
    - <span data-ttu-id="b8f43-112">Es wird verwendet, `select` um die zurückgegebenen Felder zu begrenzen und nur die Felder anzufordern, die die APP verwendet.</span><span class="sxs-lookup"><span data-stu-id="b8f43-112">It uses `select` to limit which fields are returned, requesting only the fields the app uses.</span></span>
    - <span data-ttu-id="b8f43-113">Sie verwendet `orderby` , um die Ereignisse nach ihrer Startzeit zu sortieren.</span><span class="sxs-lookup"><span data-stu-id="b8f43-113">It uses `orderby` to sort the events by their start time.</span></span>
    - <span data-ttu-id="b8f43-114">Er verwendet `top` , um die Ergebnisse auf 25 Ereignisse zu begrenzen.</span><span class="sxs-lookup"><span data-stu-id="b8f43-114">It uses `top` to limit the results to 25 events.</span></span>

## <a name="deploy-the-web-part"></a><span data-ttu-id="b8f43-115">Bereitstellen des Webparts</span><span class="sxs-lookup"><span data-stu-id="b8f43-115">Deploy the web part</span></span>

1. <span data-ttu-id="b8f43-116">Führen Sie die folgenden beiden Befehle in der CLI aus, um das Webpart zu erstellen und zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="b8f43-116">Run the following two commands in your CLI to build and package your web part.</span></span>

    ```Shell
    gulp bundle --ship
    gulp package-solution --ship
    ```

1. <span data-ttu-id="b8f43-117">Öffnen Sie den Browser, und wechseln Sie zum SharePoint-App-Katalog des Mandanten.</span><span class="sxs-lookup"><span data-stu-id="b8f43-117">Open your browser and go to your tenant's SharePoint App Catalog.</span></span> <span data-ttu-id="b8f43-118">Wählen Sie auf der linken Seite das Menüelement **Apps für SharePoint** aus.</span><span class="sxs-lookup"><span data-stu-id="b8f43-118">Select the **Apps for SharePoint** menu item on the left-hand side.</span></span>

1. <span data-ttu-id="b8f43-119">Laden Sie die Datei **./SharePoint/Solution/Graph-Tutorial.sppkg** hoch.</span><span class="sxs-lookup"><span data-stu-id="b8f43-119">Upload the **./sharepoint/solution/graph-tutorial.sppkg** file.</span></span>

1. <span data-ttu-id="b8f43-120">Bestätigen Sie in der Aufforderung **Do You Trust...** , dass in der Aufforderung die vier Microsoft Graph-Berechtigungen aufgelistet sind, die Sie in der Datei **package-solution.jsfür** festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="b8f43-120">In the **Do you trust...** prompt, confirm that the prompt lists the 4 Microsoft Graph permissions you set in the **package-solution.json** file.</span></span> <span data-ttu-id="b8f43-121">Wählen Sie **Diese Lösung für alle Websites in der Organisation verfügbar machen** aus, und wählen Sie dann **Bereitstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="b8f43-121">Select **Make this solution available to all sites in the organization** , then select **Deploy**.</span></span>

1. <span data-ttu-id="b8f43-122">Wenn Sie die Graph-Berechtigungen für Ihr Webpart noch nicht genehmigt haben, müssen Sie dies jetzt tun.</span><span class="sxs-lookup"><span data-stu-id="b8f43-122">If you have not already approved the Graph permissions for your web part, do that now.</span></span>

    1. <span data-ttu-id="b8f43-123">Wechseln Sie zum [SharePoint Admin Center](https://admin.microsoft.com/sharepoint?page=classicfeatures&modern=true) mithilfe eines Mandanten Administrators.</span><span class="sxs-lookup"><span data-stu-id="b8f43-123">Go to the [SharePoint admin center](https://admin.microsoft.com/sharepoint?page=classicfeatures&modern=true) using a tenant administrator.</span></span>

    1. <span data-ttu-id="b8f43-124">Wählen Sie im Menü links die Option **erweitert** und dann **API-Zugriff** aus.</span><span class="sxs-lookup"><span data-stu-id="b8f43-124">In the left-hand menu, select **Advanced** , then **API access**.</span></span>

    1. <span data-ttu-id="b8f43-125">Wählen Sie die ausstehenden Anforderungen aus dem Paket **Graph-Tutorial-Client-Side-Solution** aus, und wählen Sie **genehmigen** aus.</span><span class="sxs-lookup"><span data-stu-id="b8f43-125">Select each of the pending requests from the **graph-tutorial-client-side-solution** package and choose **Approve**.</span></span>

        ![Ein Screenshot der API-Zugriffsseite von SharePoint Admin Center](images/api-access.png)

## <a name="test-the-web-part"></a><span data-ttu-id="b8f43-127">Testen des Webparts</span><span class="sxs-lookup"><span data-stu-id="b8f43-127">Test the web part</span></span>

1. <span data-ttu-id="b8f43-128">Wechseln Sie zu einer SharePoint-Website, auf der Sie das Webpart testen möchten.</span><span class="sxs-lookup"><span data-stu-id="b8f43-128">Go to a SharePoint site where you want to test the web part.</span></span> <span data-ttu-id="b8f43-129">Erstellen Sie eine neue Seite, auf der das Webpart getestet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b8f43-129">Create a new page to test the web part on.</span></span>

1. <span data-ttu-id="b8f43-130">Verwenden Sie die Webpart-Auswahl zum Suchen des **GraphTutorial** -Webparts und zum Hinzufügen des Webparts zur Seite.</span><span class="sxs-lookup"><span data-stu-id="b8f43-130">Use the web part picker to find the **GraphTutorial** web part and add it to the page.</span></span>

    ![Screenshot des GraphTutorial-Webparts in der Webpart-Auswahl](images/add-web-part.png)

1. <span data-ttu-id="b8f43-132">Eine Liste der Ereignisse für die aktuelle Woche wird im Webpart gedruckt.</span><span class="sxs-lookup"><span data-stu-id="b8f43-132">A list of events for the current week are printed in the web part.</span></span>

    ![Ein Screenshot des Webparts, in dem eine Liste der Ereignisse angezeigt wird](images/calendar-list.png)
