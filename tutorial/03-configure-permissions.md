---
ms.openlocfilehash: 19bd57df9f349d67e9f10e7dd70f02231950b010
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823368"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="08560-101">Das SharePoint-Framework entfällt die Notwendigkeit, eine Anwendung in Azure AD für das Abrufen von Zugriffstoken für den Zugriff auf Microsoft Graph zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="08560-101">The SharePoint Framework eliminates the need to register an application in Azure AD for getting access tokens to access Microsoft Graph.</span></span> <span data-ttu-id="08560-102">Er behandelt die Authentifizierung für den Benutzer, der bei SharePoint angemeldet ist, sodass das Webpart Benutzertoken erhalten kann.</span><span class="sxs-lookup"><span data-stu-id="08560-102">It handles the authentication for the user that is logged into SharePoint, allowing your web part to get user tokens.</span></span> <span data-ttu-id="08560-103">Das Webpart muss angeben, welche [Graph-Berechtigungs Bereiche](https://docs.microsoft.com/graph/permissions-reference) benötigt werden, und ein mandantenadministrator kann diese Berechtigungen während der Installation genehmigen.</span><span class="sxs-lookup"><span data-stu-id="08560-103">Your web part needs to indicate which [Graph permission scopes](https://docs.microsoft.com/graph/permissions-reference) it requires, and a tenant admin can approve those permissions during installation.</span></span>

## <a name="configure-permissions"></a><span data-ttu-id="08560-104">Konfigurieren von Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="08560-104">Configure permissions</span></span>

1. <span data-ttu-id="08560-105">Öffnen Sie **./config/package-solution.jsein**.</span><span class="sxs-lookup"><span data-stu-id="08560-105">Open **./config/package-solution.json**.</span></span>

1. <span data-ttu-id="08560-106">Fügen Sie der-Eigenschaft den folgenden Code hinzu `solution` .</span><span class="sxs-lookup"><span data-stu-id="08560-106">Add the following code to the `solution` property.</span></span>

    ```json
    "webApiPermissionRequests": [
      {
        "resource": "Microsoft Graph",
        "scope": "Calendars.ReadWrite"
      },
      {
        "resource": "Microsoft Graph",
        "scope": "User.ReadBasic.All"
      },
      {
        "resource": "Microsoft Graph",
        "scope": "Contacts.Read"
      },
      {
        "resource": "Microsoft Graph",
        "scope": "People.Read"
      }
    ]
    ```

<span data-ttu-id="08560-107">Die `Calendars.ReadWrite` Berechtigung ermöglicht Ihrem Webpart das Abrufen des Kalenders des Benutzers und das Hinzufügen von Ereignissen mithilfe von Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="08560-107">The `Calendars.ReadWrite` permission allows your web part to retrieve the user's calendar and add events using Microsoft Graph.</span></span> <span data-ttu-id="08560-108">Die anderen Berechtigungen werden von Komponenten im Microsoft Graph-Toolkit verwendet, um Informationen zu Ereignis Teilnehmern und Organisatoren zu rendern.</span><span class="sxs-lookup"><span data-stu-id="08560-108">The other permissions are used by components in the Microsoft Graph Toolkit to render information about event attendees and organizers.</span></span>

## <a name="optional-test-token-acquisition"></a><span data-ttu-id="08560-109">Optional: Testen der Token-Erfassung</span><span class="sxs-lookup"><span data-stu-id="08560-109">Optional: Test token acquisition</span></span>

> [!NOTE]
> <span data-ttu-id="08560-110">Die restlichen Schritte auf dieser Seite sind optional.</span><span class="sxs-lookup"><span data-stu-id="08560-110">The rest of the steps on this page are optional.</span></span> <span data-ttu-id="08560-111">Wenn Sie direkt zur Microsoft Graph-Codierung gelangen möchten, können Sie fortfahren, um [eine Kalenderansicht zu erhalten](/graph/tutorials/spfx?tutorial-step=3).</span><span class="sxs-lookup"><span data-stu-id="08560-111">If you'd prefer to get to the Microsoft Graph coding right away, you can proceed to [Get a calendar view](/graph/tutorials/spfx?tutorial-step=3).</span></span>

<span data-ttu-id="08560-112">Wir fügen dem Webpart einen temporären Code hinzu, um die Token-Akquisition zu testen.</span><span class="sxs-lookup"><span data-stu-id="08560-112">Let's add some temporary code to the web part to test token acquisition.</span></span>

1. <span data-ttu-id="08560-113">Öffnen Sie **/src/Webparts/graphTutorial/GraphTutorialWebPart.TS** , und fügen Sie die folgende `import` Anweisung am Anfang der Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="08560-113">Open **./src/webparts/graphTutorial/GraphTutorialWebPart.ts** and add the following `import` statement at the top of the file.</span></span>

    ```typescript
    import { AadTokenProvider } from '@microsoft/sp-http';
    ```

1. <span data-ttu-id="08560-114">Ersetzen Sie die vorhandene `render`-Funktion durch Folgendes.</span><span class="sxs-lookup"><span data-stu-id="08560-114">Replace the existing `render` function with the following.</span></span>

    ```typescript
    public render(): void {
    this.context.aadTokenProviderFactory
      .getTokenProvider()
      .then((provider: AadTokenProvider)=> {
      provider
        .getToken('https://graph.microsoft.com')
        .then((token: string) => {
          this.domElement.innerHTML = `
          <div class="${ styles.graphTutorial }">
            <div class="${ styles.container }">
              <div class="${ styles.row }">
                <div class="${ styles.column }">
                  <span class="${ styles.title }">Welcome to SharePoint!</span>
                  <p><code style="word-break: break-all;">${ token }</code></p>
                </div>
              </div>
            </div>
          </div>`;
        });
      });
    }
    ```

### <a name="deploy-the-web-part"></a><span data-ttu-id="08560-115">Bereitstellen des Webparts</span><span class="sxs-lookup"><span data-stu-id="08560-115">Deploy the web part</span></span>

1. <span data-ttu-id="08560-116">Führen Sie die folgenden beiden Befehle in der CLI aus, um das Webpart zu erstellen und zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="08560-116">Run the following two commands in your CLI to build and package your web part.</span></span>

    ```Shell
    gulp bundle --ship
    gulp package-solution --ship
    ```

1. <span data-ttu-id="08560-117">Öffnen Sie den Browser, und wechseln Sie zum SharePoint-App-Katalog des Mandanten.</span><span class="sxs-lookup"><span data-stu-id="08560-117">Open your browser and go to your tenant's SharePoint App Catalog.</span></span> <span data-ttu-id="08560-118">Wählen Sie auf der linken Seite das Menüelement **Apps für SharePoint** aus.</span><span class="sxs-lookup"><span data-stu-id="08560-118">Select the **Apps for SharePoint** menu item on the left-hand side.</span></span>

1. <span data-ttu-id="08560-119">Laden Sie die Datei **./SharePoint/Solution/Graph-Tutorial.sppkg** hoch.</span><span class="sxs-lookup"><span data-stu-id="08560-119">Upload the **./sharepoint/solution/graph-tutorial.sppkg** file.</span></span>

1. <span data-ttu-id="08560-120">Bestätigen Sie in der Aufforderung **Do You Trust...** , dass in der Aufforderung die vier Microsoft Graph-Berechtigungen aufgelistet sind, die Sie in der Datei **package-solution.jsfür** festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="08560-120">In the **Do you trust...** prompt, confirm that the prompt lists the 4 Microsoft Graph permissions you set in the **package-solution.json** file.</span></span> <span data-ttu-id="08560-121">Wählen Sie **Diese Lösung für alle Websites in der Organisation verfügbar machen** aus, und wählen Sie dann **Bereitstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="08560-121">Select **Make this solution available to all sites in the organization** , then select **Deploy**.</span></span>

1. <span data-ttu-id="08560-122">Wechseln Sie zum [SharePoint Admin Center](https://admin.microsoft.com/sharepoint?page=classicfeatures&modern=true) mithilfe eines Mandanten Administrators.</span><span class="sxs-lookup"><span data-stu-id="08560-122">Go to the [SharePoint admin center](https://admin.microsoft.com/sharepoint?page=classicfeatures&modern=true) using a tenant administrator.</span></span>

1. <span data-ttu-id="08560-123">Wählen Sie im Menü links die Option **erweitert** und dann **API-Zugriff** aus.</span><span class="sxs-lookup"><span data-stu-id="08560-123">In the left-hand menu, select **Advanced** , then **API access**.</span></span>

1. <span data-ttu-id="08560-124">Wählen Sie die ausstehenden Anforderungen aus dem Paket **Graph-Tutorial-Client-Side-Solution** aus, und wählen Sie **genehmigen** aus.</span><span class="sxs-lookup"><span data-stu-id="08560-124">Select each of the pending requests from the **graph-tutorial-client-side-solution** package and choose **Approve**.</span></span>

    ![Ein Screenshot der API-Zugriffsseite von SharePoint Admin Center](images/api-access.png)

### <a name="test-the-web-part"></a><span data-ttu-id="08560-126">Testen des Webparts</span><span class="sxs-lookup"><span data-stu-id="08560-126">Test the web part</span></span>

1. <span data-ttu-id="08560-127">Wechseln Sie zu einer SharePoint-Website, auf der Sie das Webpart testen möchten.</span><span class="sxs-lookup"><span data-stu-id="08560-127">Go to a SharePoint site where you want to test the web part.</span></span> <span data-ttu-id="08560-128">Erstellen Sie eine neue Seite, auf der das Webpart getestet werden soll.</span><span class="sxs-lookup"><span data-stu-id="08560-128">Create a new page to test the web part on.</span></span>

1. <span data-ttu-id="08560-129">Verwenden Sie die Webpart-Auswahl zum Suchen des **GraphTutorial** -Webparts und zum Hinzufügen des Webparts zur Seite.</span><span class="sxs-lookup"><span data-stu-id="08560-129">Use the web part picker to find the **GraphTutorial** web part and add it to the page.</span></span>

    ![Screenshot des GraphTutorial-Webparts in der Webpart-Auswahl](images/add-web-part.png)

1. <span data-ttu-id="08560-131">Das Zugriffstoken wird unter dem **Willkommensgruß an SharePoint gedruckt.**</span><span class="sxs-lookup"><span data-stu-id="08560-131">The access token is printed below the **Welcome to SharePoint!**</span></span> <span data-ttu-id="08560-132">Nachricht im Webpart.</span><span class="sxs-lookup"><span data-stu-id="08560-132">message in the web part.</span></span> <span data-ttu-id="08560-133">Sie können dieses Token kopieren und analysieren, [https://jwt.ms/](https://jwt.ms/) um zu bestätigen, dass es die Berechtigungs Bereiche enthält, die für das Webpart erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="08560-133">You can copy this token and parse it at [https://jwt.ms/](https://jwt.ms/) to confirm that it contains the permission scopes required by the web part.</span></span>

    ![Ein Screenshot des Webparts, in dem ein Zugriffstoken angezeigt wird](images/access-token.png)
