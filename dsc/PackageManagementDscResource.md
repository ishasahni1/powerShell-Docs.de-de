---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „PackageManagement“"
ms.openlocfilehash: a984fbf5db561a696d89b60dde8b92096c6e4924
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="dsc-packagemanagement-resource" class="xliff"></a>
# DSC-Ressource „PackageManagement“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **PackageManagement** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Paketverwaltungspaketen auf einem Zielknoten. Diese Ressource erfordert das Modul **PackageManagement**, das unter „http://PowerShellGallery.com“ verfügbar ist.

<a id="syntax" class="xliff"></a>
## Syntax

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

<a id="properties" class="xliff"></a>
## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen des Pakets an, das installiert oder deinstalliert werden soll.| 
| Source| Gibt den Namen der Paketquelle an, unter der sich das Paket befindet. Dies kann entweder ein URI oder eine Quelle sein, die bei der DSC-Ressource „Register-PackageSource“ oder „PackageManagementSource“ registriert ist. Die DSC-Ressourcen „MSFT_PackageManagementSource“ kann ebenfalls eine Paketquelle registrieren.| 
| Ensure| Bestimmt, ob das Paket installiert oder deinstalliert werden soll.| 
| RequiredVersion| Gibt die genaue Version des Pakets an, das Sie installieren möchten. Wenn Sie diesen Parameter nicht angeben, installiert diese DSC-Ressource die neueste verfügbare Version des Pakets, wobei Einstellung des Parameters „MaximumVersion“ berücksichtigt wird.| 
| MinimumVersion| Gibt die zulässige Mindestversion für das zu installierende Paket an. Wenn Sie diesen Parameter nicht hinzufügen, installiert diese DSC-Ressource die höchste verfügbare Version des Pakets, wobei Einstellung des Parameters „MaximumVersion“ berücksichtigt wird.| 
| MaximumVersion| Gibt die zulässige Höchstversion für das zu installierende Paket an. Wenn Sie diesen Parameter nicht angeben, installiert diese DSC-Ressource die höchste verfügbare Version des Pakets.| 
| SourceCredential | Gibt ein Benutzerkonto an, das über Rechte zum Installieren eines Pakets für einen angegebenen Paketanbieter oder eine bestimmte Quelle verfügt.| 
| ProviderName| Gibt den Namen eines Paketanbieters an, auf den Ihre Paketsuche sich erstrecken soll. Paketanbieternamen können Sie durch Ausführen des Cmdlets „Get-PackageProvider“ abrufen.| 
| AdditionalParameters| Anbieterspezifische Parameter, die als eine Hashtabelle übergeben werden. Für NuGet-Anbieter können Sie z. B. zusätzliche Parameter wie „DestinationPath“ übergeben.| 

<a id="additional-parameters" class="xliff"></a>
## Zusätzliche Parameter
In der folgenden Tabelle sind die Optionen für die Eigenschaft „AdditionalParameters“ aufgeführt.
|  Parameter  | Beschreibung   | 
|---|---|
| DestinationPath| Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet. Gibt einen Dateispeicherort an, an dem das Paket installiert werden soll.|
| InstallationPolicy| Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet. Bestimmt, ob Sie der Paketquelle vertrauen. Entweder „Nicht vertrauenswürdig“, oder „Vertrauenswürdig“.|

<a id="example" class="xliff"></a>
## Beispiel

In diesem Beispiel werden das NuGet-Paket **JQuery** und das PowerShell-Modul **GistProvider** mithilfe der DSC-Ressource **PackageManagement** installiert. In diesem Beispiel wird zunächst sichergestellt, dass die erforderlichen Paketquellen verfügbar sind. Anschließend wird der erwartete Zustand der **JQuery**- und **GistProvider**-Pakete (NuGet bzw. PowerShell) definiert.

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

