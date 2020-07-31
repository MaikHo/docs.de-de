---
title: Übersicht der LINQ to XML-Klassen (C#)
description: In diesem Artikel werden die LINQ to XML-Klassen in C# im System.Xml.Linq-Namespace zusammengefasst, wobei jeweils eine kurze Beschreibung angezeigt wird.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165432"
---
# <a name="linq-to-xml-classes-overview-c"></a>Übersicht der LINQ to XML-Klassen (C#)
In diesem Thema finden Sie eine Liste der [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]-Klassen im <xref:System.Xml.Linq>-Namespace sowie jeweils eine kurze Beschreibung.  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML-Klassen  
  
### <a name="xattribute-class"></a>"XAttribute"-Klasse  
 <xref:System.Xml.Linq.XAttribute> stellt ein XML-Attribut dar. Ausführliche Informationen und Beispiele finden Sie unter [XAttribute Class Overview (C#) (Übersicht über die XAttribute-Klasse (C#))](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>"XCData"-Klasse  
 <xref:System.Xml.Linq.XCData> stellt einen CDATA-Textknoten dar.  
  
### <a name="xcomment-class"></a>"XComment"-Klasse  
 <xref:System.Xml.Linq.XComment> stellt einen XML-Kommentar dar.  
  
### <a name="xcontainer-class"></a>"XContainer"-Klasse  
 <xref:System.Xml.Linq.XContainer> ist eine abstrakte Basisklasse für alle Knoten, die untergeordnete Knoten besitzen dürfen. Die folgenden Klassen leiten sich von der <xref:System.Xml.Linq.XContainer>-Klasse her:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration-Klasse  
 <xref:System.Xml.Linq.XDeclaration> stellt eine XML-Deklaration dar. XML-Deklarationen werden zum Deklarieren der XML-Version und zum Codieren von Dokumenten verwendet. Außerdem geben XML-Deklarationen an, ob das XML-Dokument eigenständig ist. Wenn ein Dokument eigenständig ist, sind keine externen Markupdeklarationen vorhanden (weder in einer externen DTD, noch in einer externen Parameterentität, auf die von der internen Teilmenge aus verwiesen wird).  
  
### <a name="xdocument-class"></a>"XDocument"-Klasse  
 <xref:System.Xml.Linq.XDocument> stellt ein XML-Dokument dar. Ausführliche Informationen und Beispiele finden Sie unter [XDocument Class Overview (C#) (Übersicht über die XDocument-Klasse (C#))](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>"XDocumentType"-Klasse  
 <xref:System.Xml.Linq.XDocumentType> stellt eine XML-Dokumenttypdefinition (DTD) dar.  
  
### <a name="xelement-class"></a>"XElement"-Klasse  
 <xref:System.Xml.Linq.XElement> stellt ein XML-Element dar. Ausführliche Informationen und Beispiele finden Sie unter [XElement Class Overview (C#) (Übersicht über die XElement-Klasse (C#))](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>"XName"-Klasse  
 <xref:System.Xml.Linq.XName> stellt Namen von Elementen (<xref:System.Xml.Linq.XElement>) und Attributen (<xref:System.Xml.Linq.XAttribute>) dar. Ausführliche Informationen und Beispiele finden Sie unter [XDocument Class Overview (C#) (Übersicht über die XDocument-Klasse (C#))](./xdocument-class-overview.md).  
  
 Bei der Entwicklung von [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wurde auf einen möglichst einfachen Umgang mit XML-Namen Wert gelegt. Aufgrund ihrer Komplexität werden XML-Namen in XML oft als Angelegenheit für Fortgeschrittene betrachtet. Ursache dieser Komplexität sind aber nicht die von den Entwicklern regelmäßig beim Programmieren verwendeten Namespaces, sondern die Namespacepräfixe. Namespacepräfixe können helfen, die Anzahl der Tastaturanschläge zu verringern, die beim Eingeben von XML oder beim Bearbeiten von XML im Sinne einer besseren Lesbarkeit notwendig sind. Präfixe sind jedoch häufig nur eine Verknüpfung zur Verwendung des vollständigen XML-Namespace und in den meisten Fällen nicht erforderlich. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vereinfacht XML-Namen, indem alle Präfixe in ihren entsprechenden XML-Namespace aufgelöst werden. Wenn erforderlich, sind Präfixe über die <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>-Methode verfügbar.  
  
 Bei Bedarf ist es möglich, Namespacepräfixe zu steuern. Eine solche Steuerung von Namespacepräfixen ist z. B. dann erforderlich, wenn Sie mit anderen XML-Systemen, wie XSLT oder XAML, arbeiten. Wenn Sie beispielsweise einen XPath-Ausdruck verwenden, der Namespacepräfixe verwendet und in ein XSLT-Stylesheet eingebettet ist, müssen Sie sicherstellen, dass Ihr XML-Dokument mit Namespacepräfixen serialisiert wird, die den im XPath-Ausdruck verwendeten Namespacepräfixen entsprechen.  
  
### <a name="xnamespace-class"></a>"XNamespace"-Klasse  
 <xref:System.Xml.Linq.XNamespace> stellt einen Namespace für ein <xref:System.Xml.Linq.XElement> oder ein <xref:System.Xml.Linq.XAttribute> dar. Namespaces sind eine Komponente eines <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>"XNode"-Klasse  
 <xref:System.Xml.Linq.XNode> ist eine abstrakte Klasse, die die Knoten einer XML-Struktur darstellt. Die folgenden Klassen leiten sich von der <xref:System.Xml.Linq.XNode>-Klasse her:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>"XNodeDocumentOrderComparer"-Klasse  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> ermöglicht das Vergleichen von Knoten anhand ihrer Dokumentreihenfolge.  
  
### <a name="xnodeequalitycomparer-class"></a>"XNodeEqualityComparer"-Klasse  
 <xref:System.Xml.Linq.XNodeEqualityComparer> ermöglicht das Vergleichen von Knoten anhand ihrer Wertgleichheit.  
  
### <a name="xobject-class"></a>"XObject"-Klasse  
 <xref:System.Xml.Linq.XObject> ist eine abstrakte Basisklasse von <xref:System.Xml.Linq.XNode> und <xref:System.Xml.Linq.XAttribute>. Sie stellt Anmerkungs- und Ereignisfunktionen bereit.  
  
### <a name="xobjectchange-class"></a>"XObjectChange"-Klasse  
 <xref:System.Xml.Linq.XObjectChange> gibt den Ereignistyp an, wenn ein Ereignis für ein <xref:System.Xml.Linq.XObject> ausgelöst wird.  
  
### <a name="xobjectchangeeventargs-class"></a>"XObjectChangeEventArgs"-Klasse  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> stellt Daten für die Ereignisse <xref:System.Xml.Linq.XObject.Changing> und <xref:System.Xml.Linq.XObject.Changed> bereit.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction-Klasse  
 <xref:System.Xml.Linq.XProcessingInstruction> stellt eine XML-Verarbeitungsanweisung dar. Eine Verarbeitungsanweisung stellt der Anwendung, die das XML-Dokument verarbeitet, entsprechende Informationen zur Verarbeitung bereit.  
  
### <a name="xtext-class"></a>"XText"-Klasse  
 <xref:System.Xml.Linq.XText> stellt einen Textknoten dar. Diese Klasse muss in den meisten Fällen nicht verwendet werden. Sie wird hauptsächlich für gemischten Inhalt eingesetzt.  
  
## <a name="see-also"></a>Siehe auch

- [LINQ to XML Programming Overview (C#) (Übersicht der LINQ to XML-Programmierung (C#))](./linq-to-xml-overview.md)
