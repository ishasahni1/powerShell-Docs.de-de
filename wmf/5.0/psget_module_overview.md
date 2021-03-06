---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="powershell-module-discovery-install-and-inventory-with-powershellget" class="xliff"></a>
# Ermittlung, Installation und Inventur von PowerShell-Modulen mit PowerShellGet
 
PowerShellGet ist in dieser Version von WMF enthalten:
-   „Find-Module“ kann Modulmetadaten anhand des „-Tag“-Parameters filtern.
-   „Find-Module“ kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.
-   „Find-Module“ kann mit den Parametern „-Command“, „-DscResource“ und „-Includes“ den Modulinhalt filtern.
-   „Find-DscResource“ ermöglicht die Ermittlung einzelner DSC-Ressourcen in Repositorys.
-   Unterstützung für die Installation über und Veröffentlichung in Dateifreigaben mit NuGet

<a id="example-commands" class="xliff"></a>
## Beispiele für Befehle
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

<a id="new-features-in-powershellget" class="xliff"></a>
## Neue Features in Windows PowerShellGet
-   Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für Windows PowerShell 5.0 oder höher
-   Unterstützung der Installation von Modulabhängigkeiten
-   Drei neue Cmdlets
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
    
