---
title: 'Vorgehensweise: Generieren von Textdateien aus XML (C#)'
description: Hier erfahren Sie, wie Sie eine CSV-Datei aus einer XML-Datei in C# erstellen. Für dieses Beispiel wird die Methodensyntax und der Aggregate-Operator verwendet.
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: a6e9ce803ddfac3f1609d60a4f51661232cbb2f4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105053"
---
# <a name="how-to-generate-text-files-from-xml-c"></a>Vorgehensweise: Generieren von Textdateien aus XML (C#)
In diesem Beispiel wird gezeigt, wie Sie aus einer XML-Datei eine CSV-Datei generieren können.  
  
## <a name="example"></a>Beispiel  
 Die C#-Version dieses Beispiels verwendet die Methodensyntax und den `Aggregate`-Operator, um aus einem XML-Dokument in einem einzelnen Ausdruck eine CSV-Datei zu generieren. Weitere Informationen finden Sie unter [Abfragesyntax und Methodensyntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 In diesem Beispiel wird das folgende XML-Dokument verwendet: [Beispiel-XML-Datei: Kunden und Bestellungen (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 Dieser Code erzeugt die folgende Ausgabe:  
  
```output  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a>Siehe auch

- [Projektionen und Transformationen (LINQ to XML) (C#)](how-to-work-with-dictionaries-using-linq-to-xml.md)
