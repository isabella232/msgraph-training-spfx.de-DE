---
ms.openlocfilehash: ca72a0d6047d3cd275d34e2d0b4e3c54dbab5375
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48831352"
---
# <a name="how-to-run-the-completed-project"></a><span data-ttu-id="be346-101">Vorgehensweise Ausführen des abgeschlossenen Projekts</span><span class="sxs-lookup"><span data-stu-id="be346-101">How to run the completed project</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be346-102">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="be346-102">Prerequisites</span></span>

<span data-ttu-id="be346-103">Um das abgeschlossene Projekt in diesem Ordner auszuführen, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="be346-103">To run the completed project in this folder, you need the following:</span></span>

- <span data-ttu-id="be346-104">[Node.js](https://nodejs.org/en/download/releases/) Version 10. x</span><span class="sxs-lookup"><span data-stu-id="be346-104">[Node.js](https://nodejs.org/en/download/releases/) version 10.x</span></span>
- [<span data-ttu-id="be346-105">Gulp</span><span class="sxs-lookup"><span data-stu-id="be346-105">Gulp</span></span>](https://gulpjs.com/)
- <span data-ttu-id="be346-106">Ein Microsoft-Arbeits-oder Schulkonto mit Zugriff auf ein globales Administratorkonto in derselben Organisation.</span><span class="sxs-lookup"><span data-stu-id="be346-106">A Microsoft work or school account, with access to a global administrator account in the same organization.</span></span> <span data-ttu-id="be346-107">Wenn Sie kein Microsoft-Konto haben, können Sie [sich für das Office 365 Entwicklerprogramm registrieren](https://developer.microsoft.com/office/dev-program) , um ein kostenloses Office 365-Abonnement zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="be346-107">If you don't have a Microsoft account, you can [sign up for the Office 365 Developer Program](https://developer.microsoft.com/office/dev-program) to get a free Office 365 subscription.</span></span>
- <span data-ttu-id="be346-108">Ihr Microsoft 365-Mandant sollte [für die SharePoint Framework-Entwicklung eingerichtet](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-developer-tenant)sein, wobei ein App-Katalog und eine TestWebsite erstellt wurden, bevor Sie mit diesem Lernprogramm beginnen.</span><span class="sxs-lookup"><span data-stu-id="be346-108">Your Microsoft 365 tenant should be [setup for SharePoint Framework development](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-developer-tenant), with an app catalog and testing site created before you start this tutorial.</span></span>

### <a name="deploy-the-web-part"></a><span data-ttu-id="be346-109">Bereitstellen des Webparts</span><span class="sxs-lookup"><span data-stu-id="be346-109">Deploy the web part</span></span>

1. <span data-ttu-id="be346-110">Führen Sie die folgenden beiden Befehle in der CLI aus, um das Webpart zu erstellen und zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="be346-110">Run the following two commands in your CLI to build and package your web part.</span></span>

    ```Shell
    gulp bundle --ship
    gulp package-solution --ship
    ```

1. <span data-ttu-id="be346-111">Öffnen Sie den Browser, und wechseln Sie zum SharePoint-App-Katalog des Mandanten.</span><span class="sxs-lookup"><span data-stu-id="be346-111">Open your browser and go to your tenant's SharePoint App Catalog.</span></span> <span data-ttu-id="be346-112">Wählen Sie auf der linken Seite das Menüelement **Apps für SharePoint** aus.</span><span class="sxs-lookup"><span data-stu-id="be346-112">Select the **Apps for SharePoint** menu item on the left-hand side.</span></span>

1. <span data-ttu-id="be346-113">Laden Sie die Datei **./SharePoint/Solution/Graph-Tutorial.sppkg** hoch.</span><span class="sxs-lookup"><span data-stu-id="be346-113">Upload the **./sharepoint/solution/graph-tutorial.sppkg** file.</span></span>

1. <span data-ttu-id="be346-114">Bestätigen Sie in der Aufforderung **Do You Trust...** , dass in der Aufforderung die vier Microsoft Graph-Berechtigungen aufgelistet sind, die Sie in der Datei **package-solution.jsfür** festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="be346-114">In the **Do you trust...** prompt, confirm that the prompt lists the 4 Microsoft Graph permissions you set in the **package-solution.json** file.</span></span> <span data-ttu-id="be346-115">Wählen Sie **Diese Lösung für alle Websites in der Organisation verfügbar machen** aus, und wählen Sie dann **Bereitstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="be346-115">Select **Make this solution available to all sites in the organization** , then select **Deploy**.</span></span>

1. <span data-ttu-id="be346-116">Wechseln Sie zum [SharePoint Admin Center](https://admin.microsoft.com/sharepoint?page=classicfeatures&modern=true) mithilfe eines Mandanten Administrators.</span><span class="sxs-lookup"><span data-stu-id="be346-116">Go to the [SharePoint admin center](https://admin.microsoft.com/sharepoint?page=classicfeatures&modern=true) using a tenant administrator.</span></span>

1. <span data-ttu-id="be346-117">Wählen Sie im Menü links die Option **erweitert** und dann **API-Zugriff** aus.</span><span class="sxs-lookup"><span data-stu-id="be346-117">In the left-hand menu, select **Advanced** , then **API access**.</span></span>

1. <span data-ttu-id="be346-118">Wählen Sie die ausstehenden Anforderungen aus dem Paket **Graph-Tutorial-Client-Side-Solution** aus, und wählen Sie **genehmigen** aus.</span><span class="sxs-lookup"><span data-stu-id="be346-118">Select each of the pending requests from the **graph-tutorial-client-side-solution** package and choose **Approve**.</span></span>

    ![Ein Screenshot der API-Zugriffsseite von SharePoint Admin Center](../tutorial/images/api-access.png)

### <a name="test-the-web-part"></a><span data-ttu-id="be346-120">Testen des Webparts</span><span class="sxs-lookup"><span data-stu-id="be346-120">Test the web part</span></span>

1. <span data-ttu-id="be346-121">Wechseln Sie zu einer SharePoint-Website, auf der Sie das Webpart testen möchten.</span><span class="sxs-lookup"><span data-stu-id="be346-121">Go to a SharePoint site where you want to test the web part.</span></span> <span data-ttu-id="be346-122">Erstellen Sie eine neue Seite, auf der das Webpart getestet werden soll.</span><span class="sxs-lookup"><span data-stu-id="be346-122">Create a new page to test the web part on.</span></span>

1. <span data-ttu-id="be346-123">Verwenden Sie die Webpart-Auswahl zum Suchen des **GraphTutorial** -Webparts und zum Hinzufügen des Webparts zur Seite.</span><span class="sxs-lookup"><span data-stu-id="be346-123">Use the web part picker to find the **GraphTutorial** web part and add it to the page.</span></span>

    ![Screenshot des GraphTutorial-Webparts in der Webpart-Auswahl](../tutorial/images/add-web-part.png)
