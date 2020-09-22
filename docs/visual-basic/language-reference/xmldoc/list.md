---
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 900cd8c467a21812d980cffa7e41120ae557704b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872788"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)

Definiert eine Liste oder Tabelle.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>Parameter  

 `type`  
 Der Typ der Liste. Muss ein "Aufzählungs Zeichen" für eine Aufzählungs Liste, "Zahl" für eine nummerierte Liste oder "Table" für eine Tabelle mit zwei Spalten sein.  
  
 `term`  
 Wird nur verwendet, wenn `type` "Table" ist. Ein zu definierenden Begriff, der im Beschreibungs-Tag definiert ist.  
  
 `description`  
 Wenn `type` "Bullet" oder "Number" ist, `description` ist ein Element in der Liste `type` , wenn "Table" ist, `description` die Definition von `term` .  
  
## <a name="remarks"></a>Hinweise  

 Der- `<listheader>` Block definiert die Überschrift einer Tabelle oder einer Definitionsliste. Wenn Sie eine Tabelle definieren, müssen Sie in der Überschrift nur einen Eintrag für angeben `term` .  
  
 Jedes Element der Liste wird mit einem `<item>`-Block angegeben. Beim Erstellen einer Definitionsliste müssen Sie sowohl `term` als auch angeben `description` . Für eine Tabelle, eine aufzählige Liste oder eine nummerierte Liste müssen Sie jedoch nur einen Eintrag für angeben `description` .  
  
 Eine Liste oder Tabelle kann so viele `<item>`-Blöcke besitzen wie nötig.  
  
 Kompilieren Sie mit [-doc](../../reference/command-line-compiler/doc.md), um Dokumentationskommentare zu einer Datei zu verarbeiten.  
  
## <a name="example"></a>Beispiel  

 In diesem Beispiel wird das- `<list>` Tag zum Definieren einer aufzurufenden Liste im Abschnitt "Hinweise" verwendet.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Weitere Informationen

- [XML-Kommentartags](index.md)
