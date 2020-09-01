---
description: '#pragma – C#-Referenz'
title: '#pragma – C#-Referenz'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137954"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="3af2a-103">#pragma (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="3af2a-103">#pragma (C# Reference)</span></span>
<span data-ttu-id="3af2a-104">`#pragma` gibt dem Compiler spezielle Anweisungen für die Kompilierung der Datei, in der es auftritt.</span><span class="sxs-lookup"><span data-stu-id="3af2a-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="3af2a-105">Die Anweisungen müssen vom Compiler unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="3af2a-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="3af2a-106">Das heißt, Sie können `#pragma` nicht zum Erstellen von benutzerdefinierten Vorverarbeitungsanweisungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="3af2a-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="3af2a-107">Der Microsoft C#-Compiler unterstützt die folgenden beiden `#pragma`-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="3af2a-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="3af2a-108">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="3af2a-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="3af2a-109">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="3af2a-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="3af2a-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="3af2a-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="3af2a-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="3af2a-111">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="3af2a-112">Der Name einer erkannten pragma-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="3af2a-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="3af2a-113">Pragma-spezifische Argumente.</span><span class="sxs-lookup"><span data-stu-id="3af2a-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af2a-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3af2a-114">See also</span></span>

- [<span data-ttu-id="3af2a-115">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="3af2a-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3af2a-116">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="3af2a-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3af2a-117">C#-Präprozessoranweisungen</span><span class="sxs-lookup"><span data-stu-id="3af2a-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="3af2a-118">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="3af2a-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="3af2a-119">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="3af2a-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
