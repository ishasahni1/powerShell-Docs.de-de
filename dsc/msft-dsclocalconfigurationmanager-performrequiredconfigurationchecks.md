---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Startet eine Konsistenzprüfung unter Verwendung des Taskplaners.

<a id="syntax" class="xliff"></a>
Syntax
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a id="parameters" class="xliff"></a>
Parameter
----------

*Flags* \[in\]  
Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt. Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:

|Wert |Beschreibung |
|:--- |:---|
|**1** | Eine normale Konsistenzprüfung. |
|**2** | Die Fortsetzung einer Konsistenzprüfung nach einem Neustart. Dieser Wert sollte nicht mit anderen Werten kombiniert werden. |
|**4** | Die Konfiguration sollte von dem Pull-Server abgerufen werden, der in der Metakonfiguration für den Knoten angegeben ist. Dieser Wert sollte immer mit **1** kombiniert werden, um einen Wert von **5** zu erzielen. |
|**8** | Senden des Status an den Berichtsserver. |

<a id="return-value" class="xliff"></a>
## Rückgabewert
------------

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

<a id="remarks" class="xliff"></a>
## Hinweise

Dies ist eine statische Methode.

<a id="requirements" class="xliff"></a>
## Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## Siehe auch


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 



