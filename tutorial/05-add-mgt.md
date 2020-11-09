---
ms.openlocfilehash: ee9addcbcf58fa971b3e67fb3d84cfb36bf275dd
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823374"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="db691-101">In diesem Abschnitt verwenden Sie das [Microsoft Graph-Toolkit](https://docs.microsoft.com/graph/toolkit/overview) , um die einfache Liste der Ereignisse durch eine umfangreiche Benutzeroberfläche zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="db691-101">In this section, you'll use the [Microsoft Graph Toolkit](https://docs.microsoft.com/graph/toolkit/overview) to replace the simple list of events with rich UI.</span></span>

<span data-ttu-id="db691-102">Das Toolkit enthält eine [Agenda-Komponente](https://docs.microsoft.com/graph/toolkit/components/agenda), die für die Darstellung unserer Liste von Ereignissen geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="db691-102">The toolkit provides an [Agenda component](https://docs.microsoft.com/graph/toolkit/components/agenda), which is well-suited to render our list of events.</span></span>

## <a name="update-the-web-part"></a><span data-ttu-id="db691-103">Aktualisieren des Webparts</span><span class="sxs-lookup"><span data-stu-id="db691-103">Update the web part</span></span>

1. <span data-ttu-id="db691-104">Öffnen Sie **./src/Webparts/graphTutorial/GraphTutorialWebPart.Module.scss**.</span><span class="sxs-lookup"><span data-stu-id="db691-104">Open **./src/webparts/graphTutorial/GraphTutorialWebPart.module.scss**.</span></span> <span data-ttu-id="db691-105">Ändern Sie den Wert des `background-color` Attributs im `.row` Eintrag in `$ms-color-white` .</span><span class="sxs-lookup"><span data-stu-id="db691-105">Change the value of the `background-color` attribute in the `.row` entry to `$ms-color-white`.</span></span>

    :::code language="css" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.module.scss" id="rowScssSnippet" highlight="4":::

1. <span data-ttu-id="db691-106">Fügen Sie den folgenden Eintrag in den `.graphTutorial` Eintrag ein.</span><span class="sxs-lookup"><span data-stu-id="db691-106">Add the following entry inside the `.graphTutorial` entry.</span></span>

    :::code language="css" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.module.scss" id="addSocialBtnSnippet":::

1. <span data-ttu-id="db691-107">Öffnen Sie **/src/Webparts/graphTutorial/GraphTutorialWebPart.TS** , und fügen Sie die folgende `import` Anweisung am Anfang der Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="db691-107">Open **./src/webparts/graphTutorial/GraphTutorialWebPart.ts** and add the following `import` statement at the top of the file.</span></span>

    ```typescript
    import { Providers, SharePointProvider, MgtAgenda } from '@microsoft/mgt';
    ```

1. <span data-ttu-id="db691-108">Fügen Sie die folgende Funktion zur **GraphTutorialWebPart** -Klasse hinzu, um das Toolkit zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="db691-108">Add the following function to the **GraphTutorialWebPart** class to initialize the toolkit.</span></span>

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="onInitSnippet":::

1. <span data-ttu-id="db691-109">Ersetzen Sie die vorhandene `renderCalendarView`-Funktion durch Folgendes.</span><span class="sxs-lookup"><span data-stu-id="db691-109">Replace the existing `renderCalendarView` function with the following.</span></span>

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="renderCalendarViewSnippet":::

    <span data-ttu-id="db691-110">Dadurch wird die Grundliste durch die **Agenda** -Komponente aus dem Toolkit ersetzt.</span><span class="sxs-lookup"><span data-stu-id="db691-110">This replaces the basic list with the **Agenda** component from the toolkit.</span></span>

1. <span data-ttu-id="db691-111">Erstellen Sie das Webpart, packen Sie es erneut hoch, und aktualisieren Sie dann die Seite, auf der Sie getestet werden.</span><span class="sxs-lookup"><span data-stu-id="db691-111">Build, package, and re-upload the web part, then refresh the page where you are testing it.</span></span>

    ![Screenshot des Webparts mit der Agenda-Komponente](images/mgt-agenda.png)

## <a name="an-alternate-approach"></a><span data-ttu-id="db691-113">Ein alternativer Ansatz</span><span class="sxs-lookup"><span data-stu-id="db691-113">An alternate approach</span></span>

<span data-ttu-id="db691-114">Zu diesem Zeitpunkt haben Sie folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="db691-114">At this point, you have code that:</span></span>

- <span data-ttu-id="db691-115">Verwendet die **MSGraphClient** , um die Kalenderansicht des Benutzers für die aktuelle Woche aus Microsoft Graph abzurufen.</span><span class="sxs-lookup"><span data-stu-id="db691-115">Uses the **MSGraphClient** to get the user's calendar view for the current week from Microsoft Graph.</span></span>
- <span data-ttu-id="db691-116">Fügen Sie diese Ereignisse zur **Agenda** -Komponente aus dem Microsoft Graph-Toolkit hinzu.</span><span class="sxs-lookup"><span data-stu-id="db691-116">Add those events to the **Agenda** component from the Microsoft Graph Toolkit.</span></span>

<span data-ttu-id="db691-117">Mit diesem Ansatz haben Sie Vollzugriff auf den Graph-API-Aufruf und können jede Verarbeitung der Ereignisse vor dem gewünschten Rendern durchführen.</span><span class="sxs-lookup"><span data-stu-id="db691-117">With this approach, you have full control over the Graph API call and can do any processing of the events prior to rendering that you want.</span></span> <span data-ttu-id="db691-118">Wenn dies jedoch nicht erforderlich ist, können Sie dies vereinfachen, indem Sie der **Agenda** -Komponente die Arbeit für Sie erledigen lassen.</span><span class="sxs-lookup"><span data-stu-id="db691-118">However, if that isn't required, you can simplify by letting the **Agenda** component do the work for you.</span></span>

<span data-ttu-id="db691-119">Alle Microsoft Graph Toolkit-Komponenten können alle relevanten API-Aufrufe an Microsoft Graph vornehmen.</span><span class="sxs-lookup"><span data-stu-id="db691-119">All Microsoft Graph Toolkit components are capable of making all of the relevant API calls to the Microsoft Graph.</span></span> <span data-ttu-id="db691-120">Wenn Sie beispielsweise nur die **Agenda** -Komponente zum Webpart hinzufügen und keine Eigenschaften festlegen, verwendet das Webpart die Standardeinstellungen, um Ereignisse für den aktuellen Tag abzurufen.</span><span class="sxs-lookup"><span data-stu-id="db691-120">For example, by just adding the **Agenda** component to the web part, and not setting any properties, the web part would use its default settings to get events for the current day.</span></span> <span data-ttu-id="db691-121">Schauen wir uns an, wie wir die gleichen Ergebnisse erzielen können, die wir derzeit haben (Ereignisse für die aktuelle Woche).</span><span class="sxs-lookup"><span data-stu-id="db691-121">Let's look at how we can achieve the same results we currently have (events for the current week).</span></span>

1. <span data-ttu-id="db691-122">Ersetzen Sie die vorhandene `render` Methode durch Folgendes.</span><span class="sxs-lookup"><span data-stu-id="db691-122">Replace the existing `render` method with the following.</span></span>

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="alternateRenderSnippet":::

    <span data-ttu-id="db691-123">Anstatt einen API-Aufruf vorzunehmen `render` , fügen Sie nun einfach ein- `mgt-agenda` Element direkt in den HTML-Code ein.</span><span class="sxs-lookup"><span data-stu-id="db691-123">Now, instead of making an API call in `render`, you simply add an `mgt-agenda` element directly into the HTML.</span></span> <span data-ttu-id="db691-124">Durch Festlegen `date` auf den Anfang der Woche und `days` auf 7 wird durch die Komponente derselbe API-Aufruf wie in der vorherigen Version von vorgenommen `render` .</span><span class="sxs-lookup"><span data-stu-id="db691-124">By setting `date` to the start of the week, and `days` to 7, the component will make the same API call the previous version of `render` was making.</span></span>

1. <span data-ttu-id="db691-125">Fügen Sie der **GraphTutorialWebPart** -Klasse die folgende leere Funktion hinzu.</span><span class="sxs-lookup"><span data-stu-id="db691-125">Add the following empty function to the **GraphTutorialWebPart** class.</span></span>

    ```typescript
    private async addSocialToCalendar() {}
    ```

    > [!NOTE]
    > <span data-ttu-id="db691-126">Wir haben auch eine Schaltfläche **Team Soziales hinzufügen** zum Webpart hinzugefügt und die `addSocialToCalendar` Methode als Ereignis-Listener hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="db691-126">We also added an **Add team social** button to the web part, and added the `addSocialToCalendar` method as an event listener.</span></span>  <span data-ttu-id="db691-127">Sie implementieren den Code dahinter im nächsten Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="db691-127">You'll implement the code behind that in the next section.</span></span> <span data-ttu-id="db691-128">Im Moment möchten wir lediglich, dass der Code kompiliert wird.</span><span class="sxs-lookup"><span data-stu-id="db691-128">For now, we just want the code to compile.</span></span>

1. <span data-ttu-id="db691-129">Erstellen Sie das Webpart, packen Sie es erneut hoch, und aktualisieren Sie dann die Seite, auf der Sie getestet werden.</span><span class="sxs-lookup"><span data-stu-id="db691-129">Build, package, and re-upload the web part, then refresh the page where you are testing it.</span></span> <span data-ttu-id="db691-130">Die Ansicht sollte mit dem vorherigen Test übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="db691-130">The view should be the same as your previous test.</span></span>

### <a name="using-the-toolkit-vs-making-api-calls"></a><span data-ttu-id="db691-131">Verwenden des Toolkits vs Making API Calls</span><span class="sxs-lookup"><span data-stu-id="db691-131">Using the toolkit vs making API calls</span></span>

<span data-ttu-id="db691-132">An diesem Ort Fragen Sie sich vielleicht, warum Sie die Probleme bei der Verwendung der **MSGraphClient** überhaupt durchlaufen haben, wenn das Toolkit die Arbeit für Sie erledigt.</span><span class="sxs-lookup"><span data-stu-id="db691-132">At this point you may be wondering why you went through the trouble of using the **MSGraphClient** at all, when the toolkit does the work for you.</span></span> <span data-ttu-id="db691-133">Das Toolkit ist für das Rendern von Ergebnissen konzipiert, die Sie von Microsoft Graph Abfragen, beispielsweise eine Liste von Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="db691-133">The toolkit is designed for rendering results that you query from Microsoft Graph, such as a list of events.</span></span> <span data-ttu-id="db691-134">Es gibt jedoch Szenarien, in denen die Erstellung von API-Aufrufen selbst erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="db691-134">However, there are scenarios where making API calls yourself is necessary.</span></span>

- <span data-ttu-id="db691-135">Alle API-Aufrufe, die keine `GET` Anforderung sind.</span><span class="sxs-lookup"><span data-stu-id="db691-135">Any API calls that are not a `GET` request.</span></span> <span data-ttu-id="db691-136">Beispielsweise Erstellen eines neuen Ereignisses im Kalender oder Aktualisieren der Telefonnummer eines Benutzers.</span><span class="sxs-lookup"><span data-stu-id="db691-136">For example, creating a new event on the calendar, or updating a user's phone number.</span></span>
- <span data-ttu-id="db691-137">API-Aufrufe zum Abrufen von Daten, die als "hinter den Kulissen" verwendet und nicht direkt gerendert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="db691-137">API calls to get data that's intended to be used "behind the scenes" and not rendered directly.</span></span>
