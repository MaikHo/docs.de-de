---
title: Das XML Schema Definition-Tool und die XML-Serialisierung
description: Das XML Schema Definition-Tool generiert C#- oder Visual Basic-Klassendateien für ein XSD-Schema und ein XML-Schema aus einer Bibliothek oder ausführbaren Datei.
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 6451f3b5f6e8ec2c1454e5cf7ffb95a96b620214
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554982"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a>Das XML Schema Definition-Tool und die XML-Serialisierung

Das XML Schema Definition-Tool ([XML Schema Definition-Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) wird zusammen mit den .NET Framework-Tools als Bestandteil des Windows&reg; Software Development Kits (SDK) installiert. Das Tool ist hauptsächlich für zwei Zwecke vorgesehen:  
  
- Um C#- oder Visual Basic-Klassendateien zu erstellen, die einer bestimmten XML-Schema-Definition (XSD) entsprechen. Das Tool übernimmt ein XML-Schema als Argument und gibt eine Datei mit einer Gruppe von Klassen aus, die dem Schema entsprechen, wenn sie mit <xref:System.Xml.Serialization.XmlSerializer> serialisiert werden. Informationen dazu, wie mit diesem Tool Klassen erstellt werden, die einem bestimmten Schema entsprechen, finden Sie unter [Vorgehensweise: Generieren von Klassen und XML-Schemadokumenten mit dem XML Schema Definition-Tool](xml-schema-def-tool-gen.md).  
  
- So generieren Sie ein XML-Schemadokument aus einer DLL-Datei oder EXE-Datei Um das Schema einer Gruppe von Dateien darzustellen, die Sie erstellt haben oder die mit Attributen verändert wurde, übergeben Sie dem Tool die DLL- oder EXE-Datei als Argument, um das XML-Schema zu generieren. Informationen dazu, wie mit diesem Tool ein XML-Schemadokument aus einer Gruppe von Klassen erzeugt wird, finden Sie unter [Vorgehensweise: Generieren von Klassen und XML-Schemadokumenten mit dem XML Schema Definition-Tool](xml-schema-def-tool-gen.md).  
  
Weitere Informationen zur Verwendung dieses Tools finden Sie unter [XML Schema Definition-Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Data.DataSet>
- [Einführung in die XML-Serialisierung](introducing-xml-serialization.md)
- [XML Schema Definition-Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [How to: Serialisieren eines Objekts](how-to-serialize-an-object.md).
- [How to: Deserialisieren eines Objekts](how-to-deserialize-an-object.md)
- [How to: Generieren von Klassen und XML-Schemadokumenten mit dem XML Schema Definition-Tool](xml-schema-def-tool-gen.md)
- [Bindungsunterstützung für XML-Schema](/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))
