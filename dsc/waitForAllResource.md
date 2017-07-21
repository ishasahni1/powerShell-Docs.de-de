---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: WaitForAll-Ressource in DSC
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="f7104-103">WaitForAll-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="f7104-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="f7104-104">Gilt für: Windows PowerShell 5.0 und höher.</span><span class="sxs-lookup"><span data-stu-id="f7104-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="f7104-105">Die DSC-Ressource (Desired State Configuration) **WaitForAll** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="f7104-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="f7104-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf allen der in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="f7104-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="f7104-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7104-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="f7104-108">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f7104-108">Properties</span></span>

|  <span data-ttu-id="f7104-109">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f7104-109">Property</span></span>  |  <span data-ttu-id="f7104-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f7104-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f7104-111">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="f7104-111">ResourceName</span></span>| <span data-ttu-id="f7104-112">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="f7104-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="f7104-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="f7104-113">NodeName</span></span>| <span data-ttu-id="f7104-114">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="f7104-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="f7104-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f7104-115">RetryIntervalSec</span></span>| <span data-ttu-id="f7104-116">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="f7104-116">The number of seconds before retrying.</span></span> <span data-ttu-id="f7104-117">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="f7104-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="f7104-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="f7104-118">RetryCount</span></span>| <span data-ttu-id="f7104-119">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="f7104-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="f7104-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f7104-120">ThrottleLimit</span></span>| <span data-ttu-id="f7104-121">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="f7104-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="f7104-122">Per Voreinstellung wird der new-cimsession-Standardwert verwendet.</span><span class="sxs-lookup"><span data-stu-id="f7104-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="f7104-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f7104-123">DependsOn</span></span> | <span data-ttu-id="f7104-124">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="f7104-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f7104-125">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f7104-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="f7104-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f7104-126">Example</span></span>

<span data-ttu-id="f7104-127">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="f7104-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>
