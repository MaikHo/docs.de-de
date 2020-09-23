---
title: 'Vorgehensweise: Erstellen einer Add-Erweiterungsmethode für einen Auflistungsinitialisierer'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: c36fab6635a9f7820c52c5f73c20487b92879b9a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086347"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="673d1-102">Gewusst wie: Erstellen einer Add-Erweiterungsmethode für einen Auflistungsinitialisierer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="673d1-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="673d1-103">Wenn Sie einen Auflistungsinitialisierer zum Erstellen einer Auflistung verwenden, sucht der Visual Basic Compiler nach einer Methode des Auflistungs `Add` Typs, für den die Parameter für die `Add` Methode mit den Typen der Werte im sammlungsinitialisierer verglichen werden.</span><span class="sxs-lookup"><span data-stu-id="673d1-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="673d1-104">Diese `Add` Methode wird verwendet, um die Auflistung mit den Werten aus dem Auflistungsinitialisierer aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="673d1-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="673d1-105">Wenn keine übereinstimmende `Add` Methode vorhanden ist und Sie den Code für die Auflistung nicht ändern können, können Sie eine Erweiterungsmethode mit dem Namen hinzufügen, die `Add` die für den Auflistungsinitialisierer erforderlichen Parameter annimmt.</span><span class="sxs-lookup"><span data-stu-id="673d1-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="673d1-106">Dies ist in der Regel erforderlich, wenn Sie sammlungsinitialisierer für generische Auflistungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="673d1-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="673d1-107">Beispiel</span><span class="sxs-lookup"><span data-stu-id="673d1-107">Example</span></span>  

 <span data-ttu-id="673d1-108">Im folgenden Beispiel wird gezeigt, wie dem generischen Typ eine Erweiterungsmethode hinzugefügt <xref:System.Collections.Generic.List%601> wird, sodass ein Auflistungsinitialisierer zum Hinzufügen von Objekten des Typs verwendet werden kann `Employee` .</span><span class="sxs-lookup"><span data-stu-id="673d1-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="673d1-109">Die Erweiterungsmethode ermöglicht Ihnen die Verwendung der gekürzten sammlungsinitialisierersyntax.</span><span class="sxs-lookup"><span data-stu-id="673d1-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="673d1-110">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="673d1-110">See also</span></span>

- [<span data-ttu-id="673d1-111">Auflistungsinitialisierer</span><span class="sxs-lookup"><span data-stu-id="673d1-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="673d1-112">Vorgehensweise: Erstellen einer Auflistung für einen Auflistungsinitialisierer</span><span class="sxs-lookup"><span data-stu-id="673d1-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
