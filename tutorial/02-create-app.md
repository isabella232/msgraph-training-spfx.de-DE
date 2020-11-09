---
ms.openlocfilehash: 5164c68a78837c179636f685d28ddf61f93f8415
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823337"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="6389f-101">In diesem Lernprogramm erstellen Sie ein [clientseitiges SharePoint-Webpart](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts) , das Microsoft Graph verwendet, um den Kalender des Benutzers für die aktuelle Woche abzurufen, und dem Benutzer das Hinzufügen eines Ereignisses zu seinem Kalender gestatten kann.</span><span class="sxs-lookup"><span data-stu-id="6389f-101">In this tutorial, you'll create a [SharePoint client-side web part](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts) that will use Microsoft Graph to get the user's calendar for the current week and allow the user to add an event to their calendar.</span></span>

## <a name="create-a-web-part-project"></a><span data-ttu-id="6389f-102">Erstellen eines WebPart-Projekts</span><span class="sxs-lookup"><span data-stu-id="6389f-102">Create a web part project</span></span>

1. <span data-ttu-id="6389f-103">Öffnen Sie die Befehlszeilenschnittstelle (CLI) in einem leeren Verzeichnis, in dem Sie das Projekt erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="6389f-103">Open your command-line interface (CLI) in an empty directory where you want to create the project.</span></span> <span data-ttu-id="6389f-104">Führen Sie den folgenden Befehl aus, um den SharePoint-Generator zu starten.</span><span class="sxs-lookup"><span data-stu-id="6389f-104">Run the following command to start the Yeoman SharePoint generator.</span></span>

    ```Shell
    yo @microsoft/sharepoint
    ```

1. <span data-ttu-id="6389f-105">Antworten Sie wie folgt auf die Eingabeaufforderungen.</span><span class="sxs-lookup"><span data-stu-id="6389f-105">Respond to the prompts as follows.</span></span>

    - <span data-ttu-id="6389f-106">**Wie lautet Ihr Lösungsname?**</span><span class="sxs-lookup"><span data-stu-id="6389f-106">**What is your solution name?**</span></span> `graph-tutorial`
    - <span data-ttu-id="6389f-107">**Welche Basisplanpakete möchten Sie für Ihre Komponente(n) als Ziel festlegen?**</span><span class="sxs-lookup"><span data-stu-id="6389f-107">**Which baseline packages do you want to target for your component(s)?**</span></span> `SharePoint Online only (latest)`
    - <span data-ttu-id="6389f-108">**Wohin möchten Sie die Daten verschieben?**</span><span class="sxs-lookup"><span data-stu-id="6389f-108">**Where do you want to place the files?**</span></span> `Use the current folder`
    - <span data-ttu-id="6389f-109">**Möchten Sie den Mandantenadministratoren erlauben, festzulegen, ob die Lösungen unmittelbar für alle Websites bereitgestellt werden, ohne die Bereitstellung von Features oder das Hinzufügen von Apps zu Websites?**</span><span class="sxs-lookup"><span data-stu-id="6389f-109">**Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites?**</span></span> `Yes`
    - <span data-ttu-id="6389f-110">**Erfordern die Komponenten in der Lösung Berechtigungen für den Zugriff auf webapis, die eindeutig sind und nicht für andere Komponenten in der ten Ant freigegeben werden?**</span><span class="sxs-lookup"><span data-stu-id="6389f-110">**Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the ten ant?**</span></span> `No`
    - <span data-ttu-id="6389f-111">**Welches Typ von clientseitiger Komponente möchten Sie erstellen?**</span><span class="sxs-lookup"><span data-stu-id="6389f-111">**Which type of client-side component to create?**</span></span> `WebPart`
    - <span data-ttu-id="6389f-112">**Wie lautet der Name Ihres Webparts?**</span><span class="sxs-lookup"><span data-stu-id="6389f-112">**What is your Web part name?**</span></span> `GraphTutorial`
    - <span data-ttu-id="6389f-113">**Wie lautet die Beschreibung Ihres Webparts?**</span><span class="sxs-lookup"><span data-stu-id="6389f-113">**What is your Web part description?**</span></span> `GraphTutorial description`
    - <span data-ttu-id="6389f-114">**Welches Framework möchten Sie verwenden?**</span><span class="sxs-lookup"><span data-stu-id="6389f-114">**Which framework would you like to use?**</span></span> `No JavaScript framework`

1. <span data-ttu-id="6389f-115">Führen Sie den folgenden Befehl aus, um die Version des Manuskripts im Projekt auf 3,7 zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="6389f-115">Run the following command to update the TypeScript version in the project to 3.7.</span></span>

    ```Shell
    npm install @microsoft/rush-stack-compiler-3.7 --save-dev
    ```

1. <span data-ttu-id="6389f-116">Öffnen Sie **./tsconfig.jsein** , und ersetzen Sie `rush-stack-compiler-3.3` durch `rush-stack-compiler-3.7` .</span><span class="sxs-lookup"><span data-stu-id="6389f-116">Open **./tsconfig.json** and replace `rush-stack-compiler-3.3` with `rush-stack-compiler-3.7`.</span></span>

1. <span data-ttu-id="6389f-117">Öffnen Sie **./tslint.jsein** , und entfernen Sie die- `"no-use-before-declare": true,` Verbindung.</span><span class="sxs-lookup"><span data-stu-id="6389f-117">Open **./tslint.json** and remove the `"no-use-before-declare": true,` line.</span></span> <span data-ttu-id="6389f-118">Die `no-use-before-declare` Regel ist veraltet und verursacht während des Erstellungsprozesses einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="6389f-118">The `no-use-before-declare` rule is deprecated and will cause an error during the build process.</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="6389f-119">Installieren von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="6389f-119">Install dependencies</span></span>

<span data-ttu-id="6389f-120">Bevor Sie fortfahren, installieren Sie einige zusätzliche NPM-Pakete, die Sie später verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="6389f-120">Before moving on, install some additional NPM packages that you will use later.</span></span>

- <span data-ttu-id="6389f-121">[Microsoft Graph-Beschreibungen](https://github.com/microsoftgraph/msgraph-typescript-typings) zur Bereitstellung von IntelliSense für Microsoft Graph-Objekte.</span><span class="sxs-lookup"><span data-stu-id="6389f-121">[Microsoft Graph TypeScript definitions](https://github.com/microsoftgraph/msgraph-typescript-typings) to provide Intellisense for Microsoft Graph objects.</span></span>
- <span data-ttu-id="6389f-122">[Microsoft Graph-Toolkit](https://docs.microsoft.com/graph/toolkit/overview) , um Benutzeroberflächenkomponenten für das Webpart bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="6389f-122">[Microsoft Graph Toolkit](https://docs.microsoft.com/graph/toolkit/overview) to provide UI components for the web part.</span></span>
- <span data-ttu-id="6389f-123">[Date-FNS](https://date-fns.org/) für hilfreiche Funktionen zum Arbeiten mit Datumsangaben.</span><span class="sxs-lookup"><span data-stu-id="6389f-123">[date-fns](https://date-fns.org/) for helpful functions for working with dates.</span></span>

```Shell
npm install @microsoft/microsoft-graph-types@1.17.0 --save-dev
npm install @microsoft/mgt@1.3.4 date-fns @2.16.0
```
