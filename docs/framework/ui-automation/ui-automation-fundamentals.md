---
title: Notions de base d'UI Automation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AutoGeneratedOrientationPage
helpviewer_keywords: UI automation fundamentals
ms.assetid: d270ab45-542b-45c0-a240-e80aa4a61b95
caps.latest.revision: "54"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 57fd183b042779d06274573db7b4569dbe6a54d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-fundamentals"></a><span data-ttu-id="cd7c7-102">Notions de base d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-102">UI Automation Fundamentals</span></span>
> [!NOTE]
>  <span data-ttu-id="cd7c7-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cd7c7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cd7c7-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="cd7c7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cd7c7-105">Cette section contient des vues d’ensemble de haut niveau de la [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd7c7-105">This section contains high-level overviews of the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd7c7-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cd7c7-106">In This Section</span></span>  
 [<span data-ttu-id="cd7c7-107">Vue d’ensemble UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-107">UI Automation Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [<span data-ttu-id="cd7c7-108">UI Automation et Microsoft Active Accessibility</span><span class="sxs-lookup"><span data-stu-id="cd7c7-108">UI Automation and Microsoft Active Accessibility</span></span>](../../../docs/framework/ui-automation/ui-automation-and-microsoft-active-accessibility.md)  
 [<span data-ttu-id="cd7c7-109">Vue d’ensemble d’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-109">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="cd7c7-110">Vue d’ensemble du modèles contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-110">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="cd7c7-111">Vue d’ensemble des propriétés UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-111">UI Automation Properties Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [<span data-ttu-id="cd7c7-112">Vue d’ensemble des événements UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-112">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [<span data-ttu-id="cd7c7-113">Vue d’ensemble de la sécurité UI Automation</span><span class="sxs-lookup"><span data-stu-id="cd7c7-113">UI Automation Security Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-security-overview.md)  
 [<span data-ttu-id="cd7c7-114">À l’aide d’UI Automation pour les tests automatisés</span><span class="sxs-lookup"><span data-stu-id="cd7c7-114">Using UI Automation for Automated Testing</span></span>](../../../docs/framework/ui-automation/using-ui-automation-for-automated-testing.md)  
  
## <a name="reference"></a><span data-ttu-id="cd7c7-115">Référence</span><span class="sxs-lookup"><span data-stu-id="cd7c7-115">Reference</span></span>  
 <xref:System.Windows.Automation>  
  
 <xref:System.Windows.Automation.Provider>  
  
 <xref:System.Windows.Automation.Text>  
  
 <xref:UIAutomationClientsideProviders>