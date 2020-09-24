---
title: System.Object-Methoden
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d2b96ca9e7bedd0e0438b47698d4b963844c92f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155639"
---
# <a name="systemobject-methods"></a><span data-ttu-id="99d1b-102">System.Object-Methoden</span><span class="sxs-lookup"><span data-stu-id="99d1b-102">System.Object Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="99d1b-103">unterstützt die folgenden <xref:System.Object> Methoden.</span><span class="sxs-lookup"><span data-stu-id="99d1b-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="99d1b-104">unterstützt die folgenden <xref:System.Object>-Methoden nicht.</span><span class="sxs-lookup"><span data-stu-id="99d1b-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="99d1b-105"><xref:System.Object.ToString?displayProperty=nameWithType> für binäre Typen wie `BINARY`, `VARBINARY`, `IMAGE` und `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="99d1b-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="99d1b-106">Unterschiede zu .NET</span><span class="sxs-lookup"><span data-stu-id="99d1b-106">Differences from .NET</span></span>  

 <span data-ttu-id="99d1b-107">Die Ausgabe von <xref:System.Object.ToString?displayProperty=nameWithType> für Double verwendet SQL `CONVERT` (nvarchar (30), @x , 2) in SQL.</span><span class="sxs-lookup"><span data-stu-id="99d1b-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="99d1b-108">SQL verwendet in diesem Fall immer 16 Ziffern und wissenschaftliche Schreibweise (z. B. "0.000000000000000e+000" für 0).</span><span class="sxs-lookup"><span data-stu-id="99d1b-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="99d1b-109">Im Ergebnis erzeugt die <xref:System.Object.ToString?displayProperty=nameWithType>-Konvertierung nicht die gleiche Zeichenfolge wie <xref:System.Convert.ToString%2A?displayProperty=nameWithType> im .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99d1b-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d1b-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="99d1b-110">See also</span></span>

- [<span data-ttu-id="99d1b-111">Datentypen und Funktionen</span><span class="sxs-lookup"><span data-stu-id="99d1b-111">Data Types and Functions</span></span>](data-types-and-functions.md)
