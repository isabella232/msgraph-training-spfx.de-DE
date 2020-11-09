---
ms.openlocfilehash: 0d7c9cc909e2f848cc9760d5862bb1863501f02b
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823322"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="11439-101">In diesem Abschnitt aktualisieren Sie das Webpart, um dem Benutzer das Hinzufügen eines Ereignisses zu seinem Kalender für die wöchentliche soziale Stunde des Teams zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="11439-101">In this section you'll update the web part to allow the user to add an event to their calendar for the team's weekly social hour.</span></span> <span data-ttu-id="11439-102">In diesem Szenario hat das Team eine wöchentliche soziale Stunde um 16.00 Uhr am Freitag.</span><span class="sxs-lookup"><span data-stu-id="11439-102">In this scenario, the team has a weekly social hour at 4 PM on Friday.</span></span>

1. <span data-ttu-id="11439-103">Öffnen Sie **./src/Webparts/graphTutorial/GraphTutorialWebPart.TS** , und ersetzen Sie die vorhandene `addSocialToCalendar()` Methode durch Folgendes.</span><span class="sxs-lookup"><span data-stu-id="11439-103">Open **./src/webparts/graphTutorial/GraphTutorialWebPart.ts** and replace the existing `addSocialToCalendar()` method with the following.</span></span>

    :::code language="typescript" source="../demo/graph-tutorial/src/webparts/graphTutorial/GraphTutorialWebPart.ts" id="addSocialToCalendarSnippet":::

    <span data-ttu-id="11439-104">Überprüfen Sie die Funktionsweise dieses Codes.</span><span class="sxs-lookup"><span data-stu-id="11439-104">Consider what this code does.</span></span>

    - <span data-ttu-id="11439-105">Er bestimmt den nächsten kommenden Freitag und konstruiert ein **Datum** für 16.00 Uhr an diesem Tag.</span><span class="sxs-lookup"><span data-stu-id="11439-105">It determines the next upcoming Friday and constructs a **Date** for 4 PM on that day.</span></span>
    - <span data-ttu-id="11439-106">Es wird ein neues **Microsoft Graph. Event** -Objekt erstellt, wobei der Anfang auf den Wert des **Datums** und das Ende eine Stunde später festzulegen ist.</span><span class="sxs-lookup"><span data-stu-id="11439-106">It constructs a new **MicrosoftGraph.Event** object, setting the start to the value of the **Date** , and the end for one hour later.</span></span>
    - <span data-ttu-id="11439-107">Es verwendet die **MSGraphClient** , um das neue Ereignis an den `/me/events` Endpunkt zu senden.</span><span class="sxs-lookup"><span data-stu-id="11439-107">It uses the **MSGraphClient** to POST the new event to the `/me/events` endpoint.</span></span>
    - <span data-ttu-id="11439-108">Das Webpart wird erneut gerendert, sodass die Ansicht mit dem neuen Ereignis aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="11439-108">It re-renders the web part so the view is updated with the new event.</span></span>

1. <span data-ttu-id="11439-109">Erstellen Sie das Webpart, packen Sie es erneut hoch, und aktualisieren Sie dann die Seite, auf der Sie getestet werden.</span><span class="sxs-lookup"><span data-stu-id="11439-109">Build, package, and re-upload the web part, then refresh the page where you are testing it.</span></span>

1. <span data-ttu-id="11439-110">Klicken Sie auf die Schaltfläche **Team soziale Netzwerke hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="11439-110">Click the **Add team social** button.</span></span> <span data-ttu-id="11439-111">Nachdem die Seite aktualisiert wurde, führen Sie einen Bildlauf nach unten bis Freitag durch, und suchen Sie nach dem neuen Ereignis.</span><span class="sxs-lookup"><span data-stu-id="11439-111">Once the page refreshes, scroll down to Friday and find the new event.</span></span>

    ![Ein Screenshot des neu erstellten Ereignisses, das im Webpart gerendert wurde.](images/new-event.png)
