---
ms.openlocfilehash: bb55b2bea2497628ceb2e09c889ce62e773d8e71
ms.sourcegitcommit: 523e64e972f247e2df57cd8de949ac7bd1b8b047
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "48823344"
---
<!-- markdownlint-disable MD002 MD041 -->

In diesem Lernprogramm erfahren Sie, wie Sie ein [clientseitiges SharePoint-Webpart](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts) erstellen, das die Microsoft Graph-API zum Abrufen von Kalenderinformationen für einen Benutzer verwendet.

> [!TIP]
> Wenn Sie das fertige Lernprogramm einfach herunterladen möchten, können Sie das GitHub- [Repository](https://github.com/microsoftgraph/msgraph-training-spfx)herunterladen oder Klonen.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie dieses Lernprogramm starten, sollten Sie die folgenden Tools auf dem Entwicklungscomputer installiert haben.

- [Node.js](https://nodejs.org/en/download/releases/)
- [Yeoman](https://yeoman.io/)
- [Gulp](https://gulpjs.com/)
- [SharePoint-Generator](https://docs.microsoft.com/sharepoint/dev/spfx/toolchain/scaffolding-projects-using-yeoman-sharepoint-generator)

Weitere Details zu den Anforderungen für die SharePoint Framework-Entwicklung finden Sie unter [Einrichten Ihrer SharePoint Framework-Entwicklungsumgebung](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-development-environment).

> [!IMPORTANT]
> SharePoint-Framework erfordert Node.js Version 10. x. Stellen Sie sicher, dass Sie die richtige Version installieren.

Sie sollten auch über ein Microsoft-Büro-oder Schulkonto verfügen, das über Zugriff auf ein globales Administratorkonto in derselben Organisation verfügt. Wenn Sie kein Microsoft-Konto haben, können Sie [sich für das Office 365 Entwicklerprogramm registrieren](https://developer.microsoft.com/office/dev-program) , um ein kostenloses Office 365-Abonnement zu erhalten.

Ihr Microsoft 365-Mandant sollte [für die SharePoint Framework-Entwicklung eingerichtet](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-developer-tenant)sein, wobei ein App-Katalog und eine TestWebsite erstellt wurden, bevor Sie mit diesem Lernprogramm beginnen.

> [!NOTE]
> Dieses Lernprogramm wurde mit den folgenden Versionen der oben genannten Tools geschrieben. Die Schritte in diesem Leitfaden funktionieren möglicherweise mit anderen Versionen, jedoch nicht getestet.
>
> - Node.js 10.22.0
> - Autobauer 3.1.1
> - Schluck 4.0.2
> - 1.11.0-SharePoint-Generator

## <a name="feedback"></a>Feedback

Geben Sie Feedback zu diesem Lernprogramm im [GitHub-Repository](https://github.com/microsoftgraph/msgraph-training-spfx)an.
