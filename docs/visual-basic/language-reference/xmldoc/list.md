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
# <a name="list-visual-basic"></a><span data-ttu-id="3fc0e-101">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fc0e-101">\<list> (Visual Basic)</span></span>

<span data-ttu-id="3fc0e-102">Definiert eine Liste oder Tabelle.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc0e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="3fc0e-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3fc0e-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="3fc0e-104">Parameters</span></span>  

 `type`  
 <span data-ttu-id="3fc0e-105">Der Typ der Liste.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-105">The type of the list.</span></span> <span data-ttu-id="3fc0e-106">Muss ein "Aufzählungs Zeichen" für eine Aufzählungs Liste, "Zahl" für eine nummerierte Liste oder "Table" für eine Tabelle mit zwei Spalten sein.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="3fc0e-107">Wird nur verwendet, wenn `type` "Table" ist.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-107">Only used when `type` is "table."</span></span> <span data-ttu-id="3fc0e-108">Ein zu definierenden Begriff, der im Beschreibungs-Tag definiert ist.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="3fc0e-109">Wenn `type` "Bullet" oder "Number" ist, `description` ist ein Element in der Liste `type` , wenn "Table" ist, `description` die Definition von `term` .</span><span class="sxs-lookup"><span data-stu-id="3fc0e-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc0e-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3fc0e-110">Remarks</span></span>  

 <span data-ttu-id="3fc0e-111">Der- `<listheader>` Block definiert die Überschrift einer Tabelle oder einer Definitionsliste.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="3fc0e-112">Wenn Sie eine Tabelle definieren, müssen Sie in der Überschrift nur einen Eintrag für angeben `term` .</span><span class="sxs-lookup"><span data-stu-id="3fc0e-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="3fc0e-113">Jedes Element der Liste wird mit einem `<item>`-Block angegeben.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="3fc0e-114">Beim Erstellen einer Definitionsliste müssen Sie sowohl `term` als auch angeben `description` .</span><span class="sxs-lookup"><span data-stu-id="3fc0e-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="3fc0e-115">Für eine Tabelle, eine aufzählige Liste oder eine nummerierte Liste müssen Sie jedoch nur einen Eintrag für angeben `description` .</span><span class="sxs-lookup"><span data-stu-id="3fc0e-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3fc0e-116">Eine Liste oder Tabelle kann so viele `<item>`-Blöcke besitzen wie nötig.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="3fc0e-117">Kompilieren Sie mit [-doc](../../reference/command-line-compiler/doc.md), um Dokumentationskommentare zu einer Datei zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fc0e-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3fc0e-118">Example</span></span>  

 <span data-ttu-id="3fc0e-119">In diesem Beispiel wird das- `<list>` Tag zum Definieren einer aufzurufenden Liste im Abschnitt "Hinweise" verwendet.</span><span class="sxs-lookup"><span data-stu-id="3fc0e-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3fc0e-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3fc0e-120">See also</span></span>

- [<span data-ttu-id="3fc0e-121">XML-Kommentartags</span><span class="sxs-lookup"><span data-stu-id="3fc0e-121">XML Comment Tags</span></span>](index.md)
