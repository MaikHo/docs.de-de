---
title: Sicherheit und Serialisierung
description: Erfahren Sie mehr über Sicherheit und Serialisierung. Verwenden Sie securityberechtigung mit dem angegebenen Flag "SerializationFormatter", um Objektinstanzdaten anzuzeigen oder zu ändern.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 393e334e8165f55812681848070929bdfb03a2a5
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855685"
---
# <a name="security-and-serialization"></a>Sicherheit und Serialisierung

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Da bei Serialisierung die Möglichkeit besteht, dass anderer Code Objektinstanzdaten anzeigen oder ändern kann, auf die andernfalls nicht zugegriffen werden könnte, wird für Code, der Serialisierung ausführt, eine spezielle Berechtigung benötigt: <xref:System.Security.Permissions.SecurityPermission> mit angegebenem <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> -Flag. Entsprechend der Standardrichtlinie bedeutet dies, dass diese Berechtigung nicht für aus dem Internet heruntergeladenen Code oder Code aus einem Intranet erteilt wird. Diese Berechtigung wird nur für Code auf dem lokalen Computer erteilt.  
  
 Normalerweise werden alle Felder einer Objektinstanz serialisiert. Das heißt, dass die Daten in den serialisierten Daten für die Instanz dargestellt werden. Code mit der Fähigkeit zum Interpretieren des Formats kann die Datenwerte unabhängig davon bestimmen, wie auf den Member zugegriffen werden kann. Ähnliches gilt für Deserialisierung. Dabei werden Daten aus der serialisierten Darstellung extrahiert, und der Objektzustand wird direkt festgelegt, wiederum ohne Beachtung der Zugriffsregeln.  
  
 Jedes Objekt, das sicherheitsrelevante Daten enthalten kann, sollte nach Möglichkeit als nicht serialisierbar festgelegt werden. Wenn ein Objekt serialisierbar sein muss, sollten die Felder, die vertrauliche Daten enthalten, als nicht serialisierbar festgelegt werden. Wenn diese Felder nicht als nicht serialisierbar festgelegt werden können, werden die sensiblen Daten für jeden Code verfügbar gemacht, der über die Berechtigung zum Serialisieren verfügt. Stellen Sie sicher, dass kein bösartiger Code diese Berechtigung erhalten kann.  
  
 Die <xref:System.Runtime.Serialization.ISerializable> -Schnittstelle ist nur zur Verwendung durch die Serialisierungsinfrastruktur vorgesehen. Ist sie aber nicht geschützt ist, kann sie vertrauliche Informationen freigeben. Wenn Sie benutzerdefinierte Serialisierung bereitstellen, indem Sie **ISerializable**implementieren, müssen Sie die folgenden Vorsichtsmaßnahmen treffen:  
  
- Die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode muss explizit geschützt werden, indem Sie entweder die **SecurityPermission** mit der **SerializationFormatter** -Berechtigung fordern oder sicherstellen, dass über die Methodenausgabe keine vertraulichen Informationen freigegeben werden. Beispiel:  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- Der spezielle Konstruktor, der für die Serialisierung verwendet wird, muss außerdem eine sorgfältige Überprüfung von Eingabe ausführen und entweder geschützt oder privat sein, um Missbrauch durch bösartigen Code zu verhindern. Außerdem sollte der Konstruktor dieselben Sicherheitsüberprüfungen und Berechtigungen erzwingen, die erforderlich sind, um eine Instanz einer solchen Klasse auf andere Weise zu erhalten, beispielsweise explizites Erstellen der Klasse oder indirektes Erstellen der Klasse über eine Factory.  
  
## <a name="see-also"></a>Weitere Informationen

- [Richtlinien für das Schreiben von sicherem Code](../../standard/security/secure-coding-guidelines.md)
