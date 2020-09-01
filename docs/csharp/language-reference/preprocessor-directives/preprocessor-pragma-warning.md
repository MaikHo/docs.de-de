---
description: '#pragma warning – C#-Referenz'
title: '#pragma warning – C#-Referenz'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 3085c21db386ca215d48bbe8ade83cd26732242c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137967"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="466c6-103">#pragma warning (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="466c6-103">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="466c6-104">`#pragma warning` kann bestimmte Warnungen aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="466c6-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="466c6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="466c6-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="466c6-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="466c6-106">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="466c6-107">Eine durch Trennzeichen getrennte Liste mit Warnzahlen.</span><span class="sxs-lookup"><span data-stu-id="466c6-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="466c6-108">Das Präfix „CS“ ist optional.</span><span class="sxs-lookup"><span data-stu-id="466c6-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="466c6-109">Wenn keine Warnzahlen angegeben werden, deaktiviert `disable` alle Warnungen und `restore` aktiviert sie.</span><span class="sxs-lookup"><span data-stu-id="466c6-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="466c6-110">Um Warnzahlen in Visual Studio zu suchen, erstellen Sie Ihr Projekt und suchen Sie nach den Warnzahlen im Fenster **Ausgabe**.</span><span class="sxs-lookup"><span data-stu-id="466c6-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="466c6-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="466c6-111">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="466c6-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="466c6-112">See also</span></span>

- [<span data-ttu-id="466c6-113">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="466c6-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="466c6-114">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="466c6-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="466c6-115">C#-Präprozessoranweisungen</span><span class="sxs-lookup"><span data-stu-id="466c6-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="466c6-116">C#-Compilerfehler</span><span class="sxs-lookup"><span data-stu-id="466c6-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
