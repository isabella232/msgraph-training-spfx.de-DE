---
ms.openlocfilehash: 98ecf04b99250ceab37ce46f47f2e9a46714d7ed
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48831262"
---
# <a name="graph-tutorial"></a><span data-ttu-id="6b496-101">Graph – Tutorial</span><span class="sxs-lookup"><span data-stu-id="6b496-101">graph-tutorial</span></span>

## <a name="summary"></a><span data-ttu-id="6b496-102">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="6b496-102">Summary</span></span>

<span data-ttu-id="6b496-103">Kurze Zusammenfassung der Funktionen und verwendeten Technologien.</span><span class="sxs-lookup"><span data-stu-id="6b496-103">Short summary on functionality and used technologies.</span></span>

<span data-ttu-id="6b496-104">[Abbildung der Lösung in Aktion, wenn möglich]</span><span class="sxs-lookup"><span data-stu-id="6b496-104">[picture of the solution in action, if possible]</span></span>

## <a name="used-sharepoint-framework-version"></a><span data-ttu-id="6b496-105">Verwendete SharePoint Framework-Version</span><span class="sxs-lookup"><span data-stu-id="6b496-105">Used SharePoint Framework Version</span></span>

![Version](https://img.shields.io/badge/version-1.11-green.svg)

## <a name="applies-to"></a><span data-ttu-id="6b496-107">Gilt für</span><span class="sxs-lookup"><span data-stu-id="6b496-107">Applies to</span></span>

- [<span data-ttu-id="6b496-108">SharePoint Framework</span><span class="sxs-lookup"><span data-stu-id="6b496-108">SharePoint Framework</span></span>](https://aka.ms/spfx)
- [<span data-ttu-id="6b496-109">Microsoft 365-Mandant</span><span class="sxs-lookup"><span data-stu-id="6b496-109">Microsoft 365 tenant</span></span>](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-developer-tenant)

> <span data-ttu-id="6b496-110">Holen Sie sich Ihren eigenen kostenlosen Entwicklungsmandanten, indem Sie das [Microsoft 365 Developer Program](http://aka.ms/o365devprogram) abonnieren.</span><span class="sxs-lookup"><span data-stu-id="6b496-110">Get your own free development tenant by subscribing to [Microsoft 365 developer program](http://aka.ms/o365devprogram)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b496-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6b496-111">Prerequisites</span></span>

> <span data-ttu-id="6b496-112">Spezielle Voraussetzungen?</span><span class="sxs-lookup"><span data-stu-id="6b496-112">Any special pre-requisites?</span></span>

## <a name="solution"></a><span data-ttu-id="6b496-113">Lösung</span><span class="sxs-lookup"><span data-stu-id="6b496-113">Solution</span></span>

<span data-ttu-id="6b496-114">Lösung</span><span class="sxs-lookup"><span data-stu-id="6b496-114">Solution</span></span>|<span data-ttu-id="6b496-115">Autor (en)</span><span class="sxs-lookup"><span data-stu-id="6b496-115">Author(s)</span></span>
--------|---------
<span data-ttu-id="6b496-116">Ordnername</span><span class="sxs-lookup"><span data-stu-id="6b496-116">folder name</span></span> | <span data-ttu-id="6b496-117">Autoren Details (Name, Firma, Twitter-Alias mit Link)</span><span class="sxs-lookup"><span data-stu-id="6b496-117">Author details (name, company, twitter alias with link)</span></span>

## <a name="version-history"></a><span data-ttu-id="6b496-118">Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="6b496-118">Version history</span></span>

<span data-ttu-id="6b496-119">Version</span><span class="sxs-lookup"><span data-stu-id="6b496-119">Version</span></span>|<span data-ttu-id="6b496-120">Datum</span><span class="sxs-lookup"><span data-stu-id="6b496-120">Date</span></span>|<span data-ttu-id="6b496-121">Kommentare</span><span class="sxs-lookup"><span data-stu-id="6b496-121">Comments</span></span>
-------|----|--------
<span data-ttu-id="6b496-122">1.1</span><span class="sxs-lookup"><span data-stu-id="6b496-122">1.1</span></span>|<span data-ttu-id="6b496-123">10. März 2021</span><span class="sxs-lookup"><span data-stu-id="6b496-123">March 10, 2021</span></span>|<span data-ttu-id="6b496-124">Kommentar aktualisieren</span><span class="sxs-lookup"><span data-stu-id="6b496-124">Update comment</span></span>
<span data-ttu-id="6b496-125">1.0</span><span class="sxs-lookup"><span data-stu-id="6b496-125">1.0</span></span>|<span data-ttu-id="6b496-126">29. Januar 2021</span><span class="sxs-lookup"><span data-stu-id="6b496-126">January 29, 2021</span></span>|<span data-ttu-id="6b496-127">Erstveröffentlichung:</span><span class="sxs-lookup"><span data-stu-id="6b496-127">Initial release</span></span>

## <a name="disclaimer"></a><span data-ttu-id="6b496-128">Haftungsausschluss</span><span class="sxs-lookup"><span data-stu-id="6b496-128">Disclaimer</span></span>

<span data-ttu-id="6b496-129">**Dieser Code wird ohne jegliche ausdrückliche oder implizite *Gewährleistung bereit* gestellt, einschließlich impliziter Garantien für die Eignung für einen bestimmten Zweck, die Marktgängigkeit oder die Nichtverletzung.**</span><span class="sxs-lookup"><span data-stu-id="6b496-129">**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>

---

## <a name="minimal-path-to-awesome"></a><span data-ttu-id="6b496-130">Minimaler Pfad zu awesome</span><span class="sxs-lookup"><span data-stu-id="6b496-130">Minimal Path to Awesome</span></span>

- <span data-ttu-id="6b496-131">Klonen Sie dieses Repository</span><span class="sxs-lookup"><span data-stu-id="6b496-131">Clone this repository</span></span>
- <span data-ttu-id="6b496-132">Stellen Sie sicher, dass Sie sich im Projektmappenordner befinden.</span><span class="sxs-lookup"><span data-stu-id="6b496-132">Ensure that you are at the solution folder</span></span>
- <span data-ttu-id="6b496-133">in der Befehlszeile ausführen:</span><span class="sxs-lookup"><span data-stu-id="6b496-133">in the command-line run:</span></span>
  - <span data-ttu-id="6b496-134">**NPM-Installation**</span><span class="sxs-lookup"><span data-stu-id="6b496-134">**npm install**</span></span>
  - <span data-ttu-id="6b496-135">**Schluck Dienst**</span><span class="sxs-lookup"><span data-stu-id="6b496-135">**gulp serve**</span></span>

> <span data-ttu-id="6b496-136">Fügen Sie bei Bedarf weitere Schritte ein.</span><span class="sxs-lookup"><span data-stu-id="6b496-136">Include any additional steps as needed.</span></span>

## <a name="features"></a><span data-ttu-id="6b496-137">Features</span><span class="sxs-lookup"><span data-stu-id="6b496-137">Features</span></span>

<span data-ttu-id="6b496-138">Beschreibung der Erweiterung, die sich oben auf der allgemeinen Zusammenfassung der oberen Ebene erweitert.</span><span class="sxs-lookup"><span data-stu-id="6b496-138">Description of the extension that expands upon high-level summary above.</span></span>

<span data-ttu-id="6b496-139">Diese Erweiterung veranschaulicht die folgenden Konzepte:</span><span class="sxs-lookup"><span data-stu-id="6b496-139">This extension illustrates the following concepts:</span></span>

- <span data-ttu-id="6b496-140">Thema 1</span><span class="sxs-lookup"><span data-stu-id="6b496-140">topic 1</span></span>
- <span data-ttu-id="6b496-141">Thema 2</span><span class="sxs-lookup"><span data-stu-id="6b496-141">topic 2</span></span>
- <span data-ttu-id="6b496-142">Thema 3</span><span class="sxs-lookup"><span data-stu-id="6b496-142">topic 3</span></span>

> <span data-ttu-id="6b496-143">Beachten Sie, dass durch bessere Abbildungen und Dokumentation die Beispiel Nutzung und der von Ihnen bereitgestellten Werte für andere erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="6b496-143">Notice that better pictures and documentation will increase the sample usage and the value you are providing for others.</span></span> <span data-ttu-id="6b496-144">Vielen Dank für Ihre Übermittlungen Advance.</span><span class="sxs-lookup"><span data-stu-id="6b496-144">Thanks for your submissions advance.</span></span>

> <span data-ttu-id="6b496-145">Teilen Sie Ihr Webpart für andere über das Microsoft 365-Muster und-Methoden Programm, um die Sichtbarkeit und Belichtung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6b496-145">Share your web part with others through Microsoft 365 Patterns and Practices program to get visibility and exposure.</span></span> <span data-ttu-id="6b496-146">Weitere Informationen zu den Community-, Open-Source-Projekten und anderen Aktivitäten von http://aka.ms/m365pnp .</span><span class="sxs-lookup"><span data-stu-id="6b496-146">More details on the community, open-source projects and other activities from http://aka.ms/m365pnp.</span></span>

## <a name="references"></a><span data-ttu-id="6b496-147">Informationsquellen</span><span class="sxs-lookup"><span data-stu-id="6b496-147">References</span></span>

- [<span data-ttu-id="6b496-148">Erste Schritte mit SharePoint-Framework</span><span class="sxs-lookup"><span data-stu-id="6b496-148">Getting started with SharePoint Framework</span></span>](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-developer-tenant)
- [<span data-ttu-id="6b496-149">Erstellen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6b496-149">Building for Microsoft teams</span></span>](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/build-for-teams-overview)
- [<span data-ttu-id="6b496-150">Verwenden von Microsoft Graph in Ihrer Lösung</span><span class="sxs-lookup"><span data-stu-id="6b496-150">Use Microsoft Graph in your solution</span></span>](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/using-microsoft-graph-apis)
- [<span data-ttu-id="6b496-151">Veröffentlichen von SharePoint-Framework-Anwendungen auf dem Marketplace</span><span class="sxs-lookup"><span data-stu-id="6b496-151">Publish SharePoint Framework applications to the Marketplace</span></span>](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/publish-to-marketplace-overview)
- <span data-ttu-id="6b496-152">[Microsoft 365 Patterns and Practices](https://aka.ms/m365pnp) -Anleitungen, Tools, Beispiele und Open-Source-Steuerelemente für Ihre Microsoft 365-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="6b496-152">[Microsoft 365 Patterns and Practices](https://aka.ms/m365pnp) - Guidance, tooling, samples and open-source controls for your Microsoft 365 development</span></span>
