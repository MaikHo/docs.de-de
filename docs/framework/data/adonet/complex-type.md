---
title: Komplexer Typ
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203786"
---
# <a name="complex-type"></a>Komplexer Typ

Ein *komplexer Typ* ist eine Vorlage zum Definieren von umfangreichen, strukturierten Eigenschaften für [Entitäts Typen](entity-type.md) oder für andere komplexe Typen. Jede Vorlage enthält Folgendes:  
  
- Eine eindeutige Bezeichnung. (Erforderlich)  
  
    > [!NOTE]
    > Der Name eines komplexen Typs darf nicht mit dem Namen eines Entitätstyps innerhalb des gleichen Namespace übereinstimmen.  
  
- Daten in Form von einer oder mehreren [Eigenschaften](property.md). (Optional.)  
  
    > [!NOTE]
    > Eine Eigenschaft eines komplexen Typs kann ein anderer komplexer Typ sein.  
  
 Ein komplexer Typ ähnelt insofern einem Entitätstyp, als ein komplexer Typ eine Datennutzlast in Form von primitiven Typeigenschaften oder anderen komplexen Typen enthalten kann. Es gibt jedoch einige Hauptunterschiede zwischen komplexen Typen und Entitätstypen:  
  
- Komplexe Typen weisen keine Identitäten auf und können daher nicht unabhängig sein. Komplexe Typen können nur Eigenschaften von Entitätstypen oder anderen komplexen Typen sein.  
  
- Komplexe Typen können nicht an [Zuordnungen](association-type.md)teilnehmen. Keines der Enden einer Zuordnung kann ein komplexer Typ sein, daher können [Navigations Eigenschaften](navigation-property.md) nicht für komplexe Typen definiert werden.  
  
## <a name="example"></a>Beispiel  

 Der [ADO.NET-Entity Framework](./ef/index.md) verwendet eine domänenspezifische Sprache (DSL) mit der Bezeichnung konzeptionelle Schema Definitions Sprache ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), um konzeptionelle Modelle zu definieren. Die folgende CSDL definiert einen komplexen Typ, Adress, mit den primitiven Typeigenschaften `StreetAddress`, `City`, `StateOrProvince`, `Country` und `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Deklarieren Sie den Eigenschaftentyp in der Entitätstypdefinition, um den komplexen Typ `Address` (oben) als Eigenschaft für einen Entitätstyp zu definieren. Die folgende CSDL deklariert die `Address`-Eigenschaft als komplexen Typ für einen Entitätstyp (Publisher):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Schlüsselkonzepte im Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
