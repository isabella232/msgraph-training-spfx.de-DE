---
ms.openlocfilehash: bb55b2bea2497628ceb2e09c889ce62e773d8e71
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823344"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="8ddc1-101">In diesem Lernprogramm erfahren Sie, wie Sie ein [clientseitiges SharePoint-Webpart](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts) erstellen, das die Microsoft Graph-API zum Abrufen von Kalenderinformationen für einen Benutzer verwendet.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-101">This tutorial teaches you how to build a [SharePoint client-side web part](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts) that uses the Microsoft Graph API to retrieve calendar information for a user.</span></span>

> [!TIP]
> <span data-ttu-id="8ddc1-102">Wenn Sie das fertige Lernprogramm einfach herunterladen möchten, können Sie das GitHub- [Repository](https://github.com/microsoftgraph/msgraph-training-spfx)herunterladen oder Klonen.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-spfx).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ddc1-103">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8ddc1-103">Prerequisites</span></span>

<span data-ttu-id="8ddc1-104">Bevor Sie dieses Lernprogramm starten, sollten Sie die folgenden Tools auf dem Entwicklungscomputer installiert haben.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-104">Before you start this tutorial, you should have the following tools installed on your development machine.</span></span>

- [<span data-ttu-id="8ddc1-105">Node.js</span><span class="sxs-lookup"><span data-stu-id="8ddc1-105">Node.js</span></span>](https://nodejs.org/en/download/releases/)
- [<span data-ttu-id="8ddc1-106">Yeoman</span><span class="sxs-lookup"><span data-stu-id="8ddc1-106">Yeoman</span></span>](https://yeoman.io/)
- [<span data-ttu-id="8ddc1-107">Gulp</span><span class="sxs-lookup"><span data-stu-id="8ddc1-107">Gulp</span></span>](https://gulpjs.com/)
- [<span data-ttu-id="8ddc1-108">SharePoint-Generator</span><span class="sxs-lookup"><span data-stu-id="8ddc1-108">Yeoman SharePoint generator</span></span>](https://docs.microsoft.com/sharepoint/dev/spfx/toolchain/scaffolding-projects-using-yeoman-sharepoint-generator)

<span data-ttu-id="8ddc1-109">Weitere Details zu den Anforderungen für die SharePoint Framework-Entwicklung finden Sie unter [Einrichten Ihrer SharePoint Framework-Entwicklungsumgebung](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-development-environment).</span><span class="sxs-lookup"><span data-stu-id="8ddc1-109">You can find more details about requirements for SharePoint Framework development at [Set up your SharePoint Framework development environment](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-development-environment).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ddc1-110">SharePoint-Framework erfordert Node.js Version 10. x.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-110">SharePoint Framework requires Node.js version 10.x.</span></span> <span data-ttu-id="8ddc1-111">Stellen Sie sicher, dass Sie die richtige Version installieren.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-111">Be sure to install the correct version.</span></span>

<span data-ttu-id="8ddc1-112">Sie sollten auch über ein Microsoft-Büro-oder Schulkonto verfügen, das über Zugriff auf ein globales Administratorkonto in derselben Organisation verfügt.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-112">You should also have a Microsoft work or school account, with access to a global administrator account in the same organization.</span></span> <span data-ttu-id="8ddc1-113">Wenn Sie kein Microsoft-Konto haben, können Sie [sich für das Office 365 Entwicklerprogramm registrieren](https://developer.microsoft.com/office/dev-program) , um ein kostenloses Office 365-Abonnement zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-113">If you don't have a Microsoft account, you can [sign up for the Office 365 Developer Program](https://developer.microsoft.com/office/dev-program) to get a free Office 365 subscription.</span></span>

<span data-ttu-id="8ddc1-114">Ihr Microsoft 365-Mandant sollte [für die SharePoint Framework-Entwicklung eingerichtet](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-developer-tenant)sein, wobei ein App-Katalog und eine TestWebsite erstellt wurden, bevor Sie mit diesem Lernprogramm beginnen.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-114">Your Microsoft 365 tenant should be [setup for SharePoint Framework development](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-developer-tenant), with an app catalog and testing site created before you start this tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="8ddc1-115">Dieses Lernprogramm wurde mit den folgenden Versionen der oben genannten Tools geschrieben.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-115">This tutorial was written with the following versions of the above tools.</span></span> <span data-ttu-id="8ddc1-116">Die Schritte in diesem Leitfaden funktionieren möglicherweise mit anderen Versionen, jedoch nicht getestet.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-116">The steps in this guide may work with other versions, but that has not been tested.</span></span>
>
> - <span data-ttu-id="8ddc1-117">Node.js 10.22.0</span><span class="sxs-lookup"><span data-stu-id="8ddc1-117">Node.js 10.22.0</span></span>
> - <span data-ttu-id="8ddc1-118">Autobauer 3.1.1</span><span class="sxs-lookup"><span data-stu-id="8ddc1-118">Yeoman 3.1.1</span></span>
> - <span data-ttu-id="8ddc1-119">Schluck 4.0.2</span><span class="sxs-lookup"><span data-stu-id="8ddc1-119">Gulp 4.0.2</span></span>
> - <span data-ttu-id="8ddc1-120">1.11.0-SharePoint-Generator</span><span class="sxs-lookup"><span data-stu-id="8ddc1-120">Yeoman SharePoint generator 1.11.0</span></span>

## <a name="feedback"></a><span data-ttu-id="8ddc1-121">Feedback</span><span class="sxs-lookup"><span data-stu-id="8ddc1-121">Feedback</span></span>

<span data-ttu-id="8ddc1-122">Geben Sie Feedback zu diesem Lernprogramm im [GitHub-Repository](https://github.com/microsoftgraph/msgraph-training-spfx)an.</span><span class="sxs-lookup"><span data-stu-id="8ddc1-122">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-spfx).</span></span>
