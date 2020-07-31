---
title: <see> – C#-Programmierhandbuch
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863785"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="ef8e8-102">\<see> (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="ef8e8-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef8e8-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef8e8-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="ef8e8-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="ef8e8-104">Parameters</span></span>

- <span data-ttu-id="ef8e8-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="ef8e8-105">cref = "`member`"</span></span>

  <span data-ttu-id="ef8e8-106">Ein Verweis auf einen Member oder ein Feld, das von der aktuellen Kompilierungsumgebung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ef8e8-107">Der Compiler überprüft, ob das angegebene Codeelement vorhanden ist, und übergibt `member` an den Elementnamen in der XML-Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="ef8e8-108">Setzen Sie *member* in doppelte Anführungszeichen (" ").</span><span class="sxs-lookup"><span data-stu-id="ef8e8-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="ef8e8-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ef8e8-109">Remarks</span></span>

<span data-ttu-id="ef8e8-110">Mit dem `<see>`-Tag kann ein Link im Text angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="ef8e8-111">Verwenden Sie [\<seealso>](./seealso.md), um anzugeben, dass Text in einen Abschnitt „Siehe auch“ eingefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="ef8e8-112">Verwenden Sie das [cref-Attribut](./cref-attribute.md), um interne Links zu Dokumentationsseiten für Codeelemente zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="ef8e8-113">Außerdem ist ``href`` ein gültiges Attribut, das als Hyperlink fungiert.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="ef8e8-114">Kompilieren Sie mit [-doc](../../language-reference/compiler-options/doc-compiler-option.md), um Dokumentationskommentare zu einer Datei zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="ef8e8-115">Im folgenden Beispiel wird ein `<see>`-Tag innerhalb eines zusammenfassenden Abschnitts dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ef8e8-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="ef8e8-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ef8e8-116">See also</span></span>

- [<span data-ttu-id="ef8e8-117">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="ef8e8-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="ef8e8-118">Empfohlene Tags für Dokumentationskommentare</span><span class="sxs-lookup"><span data-stu-id="ef8e8-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
