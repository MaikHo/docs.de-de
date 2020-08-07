---
title: 'Vorgehensweise: Suchen aller Knoten in einem Namespace (C#)'
description: Erfahren Sie, wie Sie nach dem Namespace eines Elements oder Attributs filtern,um alle Knoten in diesem Namespace zu suchen.
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: bf739480c6b4e2c53d5c430d47ff833e8995f6a4
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303308"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="b0f1b-103">Vorgehensweise: Suchen aller Knoten in einem Namespace (C#)</span><span class="sxs-lookup"><span data-stu-id="b0f1b-103">How to find all nodes in a namespace (C#)</span></span>
<span data-ttu-id="b0f1b-104">Sie können nach den Namespaces der einzelnen Elemente oder Attribute filtern und so alle Knoten im jeweiligen Namespace ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b0f1b-104">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f1b-105">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b0f1b-105">Example</span></span>  
 <span data-ttu-id="b0f1b-106">Das folgende Beispiel erstellt eine XML-Struktur mit zwei Namespaces.</span><span class="sxs-lookup"><span data-stu-id="b0f1b-106">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="b0f1b-107">Anschließend durchläuft das Beispiel die Struktur und gibt die Namen aller Elemente und Attribute in einem dieser Namespaces aus.</span><span class="sxs-lookup"><span data-stu-id="b0f1b-107">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="b0f1b-108">Dieser Code erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="b0f1b-108">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="b0f1b-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b0f1b-109">Example</span></span>  
 <span data-ttu-id="b0f1b-110">Die XML-Datei, auf die die folgende Abfrage zugreift, enthält Aufträge in zwei verschiedenen Namespaces.</span><span class="sxs-lookup"><span data-stu-id="b0f1b-110">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="b0f1b-111">Die Abfrage erstellt eine neue Struktur, die nur die Elemente in einem der Namespaces enthält.</span><span class="sxs-lookup"><span data-stu-id="b0f1b-111">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="b0f1b-112">In diesem Beispiel wird das folgende XML-Dokument verwendet: [Beispiel-XML-Datei: Konsolidierte Bestellungen](./sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="b0f1b-112">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="b0f1b-113">Dieser Code erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="b0f1b-113">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
</Root>  
```  
