---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „ProcessSet“"
ms.openlocfilehash: b713d1a9c34eab6966de4f342991ead32c19df5d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="dsc-windowsprocess-resource" class="xliff"></a>
# DSC-Ressource „WindowsProcess“

> Gilt für: Windows PowerShell 5.0

Die Ressource **ProcessSet** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten. Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [WindowsProcess](windowsProcessResource.md) für jede Gruppe aufruft, die im `GroupName`-Parameter angegeben ist.

<a id="syntax" class="xliff"></a>
## Syntax

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Arguments| Eine Zeichenfolge mit Argumenten, die wie vorhanden an den Prozess übergeben werden. Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.| 
| Path| Die Pfade zu den ausführbaren Prozessdateien. Wenn es sich um die Namen der ausführbaren Dateien (keine vollqualifizierten Pfade) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable **Path** (`$env:Path`), um die Dateien zu ermitteln. Wenn die Werte dieser Eigenschaft vollqualifizierte Pfade sind, verwendet DSC nicht die Umgebungsvariable **Path**, um die Dateien zu finden, und löst einen Fehler aus, wenn beliebige der Pfade nicht vorhanden sind. Relative Pfade sind nicht zulässig.| 
| Credential| Gibt die Anmeldeinformationen zum Starten des Prozesses an.| 
| Ensure| Gibt an, ob der Prozess vorhanden ist. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist. Legen Sie sie andernfalls auf „Absent“ fest. Die Standardeinstellung ist „Present“.| 
| StandardErrorPath| Der Pfad, in den der Prozess Standardfehler schreibt. Eine vorhandene Datei wird überschrieben.| 
| StandardInputPath| Der Datenstrom, aus dem der Prozess die Standardeingabe empfängt.| 
| StandardOutputPath| Der Pfad der Datei, in die der Prozess die Standardausgabe schreibt. Eine vorhandene Datei wird überschrieben.| 
| WorkingDirectory| Der Speicherort, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **_ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft so: DependsOn = "[ResourceType]ResourceName".| 

