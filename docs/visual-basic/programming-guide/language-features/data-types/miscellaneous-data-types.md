---
title: Sonstige Datentypen
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 45b44abc24b968f19b456cbe0be0f25efc8f0ce8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095459"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="995b4-102">Sonstige Datentypen (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="995b4-102">Miscellaneous Data Types (Visual Basic)</span></span>

<span data-ttu-id="995b4-103">Visual Basic stellt mehrere Datentypen bereit, die nicht an Zahlen oder Zeichen gerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="995b4-103">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="995b4-104">Stattdessen behandeln Sie spezialisierte Daten, z. b. Yes/No-Werte, Datums-/Uhrzeitwerte und Objektadressen.</span><span class="sxs-lookup"><span data-stu-id="995b4-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="995b4-105">Eine Tabelle, die einen parallelen Vergleich der Visual Basic-Datentypen anzeigt, finden Sie unter [Datentypen](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="995b4-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="995b4-106">Boolescher Typ</span><span class="sxs-lookup"><span data-stu-id="995b4-106">Boolean Type</span></span>  

 <span data-ttu-id="995b4-107">Der [boolesche Datentyp](../../../language-reference/data-types/boolean-data-type.md) ist ein nicht signierter Wert, der entweder als `True` oder interpretiert wird `False` .</span><span class="sxs-lookup"><span data-stu-id="995b4-107">The [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="995b4-108">Die Daten Breite hängt von der implementierenden Plattform ab.</span><span class="sxs-lookup"><span data-stu-id="995b4-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="995b4-109">Wenn eine Variable nur zwei Statuswerte enthalten kann, z. b. true/false, Yes/No oder on/off, deklarieren Sie Sie als `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="995b4-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="995b4-110">Datumstyp</span><span class="sxs-lookup"><span data-stu-id="995b4-110">Date Type</span></span>  

 <span data-ttu-id="995b4-111">Der [Date-Datentyp](../../../language-reference/data-types/date-data-type.md) ist ein 64-Bit-Wert, der Datums-und Uhrzeit Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="995b4-111">The [Date Data Type](../../../language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="995b4-112">Jedes Inkrement stellt 100 Nanosekunden der verstrichenen Zeit seit dem Beginn (12:00 Uhr) des 1. Januar des Jahres 1 des Jahres 1 im gregorianischen Kalender dar.</span><span class="sxs-lookup"><span data-stu-id="995b4-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="995b4-113">Wenn eine Variable einen Datumswert, einen Uhrzeitwert oder beides enthalten kann, deklarieren Sie Sie als `Date` .</span><span class="sxs-lookup"><span data-stu-id="995b4-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="995b4-114">Objekttyp</span><span class="sxs-lookup"><span data-stu-id="995b4-114">Object Type</span></span>  

 <span data-ttu-id="995b4-115">Der [Objekt Datentyp](../../../language-reference/data-types/object-data-type.md) ist eine 32-Bit-Adresse, die auf eine Objektinstanz in Ihrer Anwendung oder in einer anderen Anwendung zeigt.</span><span class="sxs-lookup"><span data-stu-id="995b4-115">The [Object Data Type](../../../language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="995b4-116">Eine `Object` Variable kann auf jedes Objekt verweisen, das von der Anwendung erkannt wird, oder auf Daten eines beliebigen Datentyps.</span><span class="sxs-lookup"><span data-stu-id="995b4-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="995b4-117">Dies schließt sowohl *Werttypen*wie `Integer` , `Boolean` , und Struktur Instanzen als auch *Verweis Typen*ein, die Instanzen von Objekten sind, die aus Klassen wie und erstellt werden `String` <xref:System.Windows.Forms.Form> , sowie Array Instanzen.</span><span class="sxs-lookup"><span data-stu-id="995b4-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="995b4-118">Wenn eine Variable einen Zeiger auf eine Instanz einer Klasse speichert, die Sie zum Zeitpunkt der Kompilierung nicht kennen oder auf Daten verschiedener Datentypen verweisen können, deklarieren Sie Sie als `Object` .</span><span class="sxs-lookup"><span data-stu-id="995b4-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="995b4-119">Der Vorteil des- `Object` Datentyps ist, dass Sie ihn zum Speichern von Daten eines beliebigen Datentyps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="995b4-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="995b4-120">Der Nachteil besteht darin, dass Sie zusätzliche Vorgänge verursachen, bei denen die Ausführungszeit länger dauert und die Anwendung langsamer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="995b4-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="995b4-121">Wenn Sie eine `Object` Variable für Werttypen verwenden, entstehen *Boxing* und *Unboxing*.</span><span class="sxs-lookup"><span data-stu-id="995b4-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="995b4-122">Wenn Sie Sie für Verweis Typen verwenden, wird eine *späte Bindung*verursacht.</span><span class="sxs-lookup"><span data-stu-id="995b4-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995b4-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="995b4-123">See also</span></span>

- [<span data-ttu-id="995b4-124">Typzeichen</span><span class="sxs-lookup"><span data-stu-id="995b4-124">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="995b4-125">Elementare Datentypen</span><span class="sxs-lookup"><span data-stu-id="995b4-125">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="995b4-126">Numerische Datentypen</span><span class="sxs-lookup"><span data-stu-id="995b4-126">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="995b4-127">Zeichendatentypen</span><span class="sxs-lookup"><span data-stu-id="995b4-127">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="995b4-128">Problembehandlung bei Datentypen</span><span class="sxs-lookup"><span data-stu-id="995b4-128">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="995b4-129">Frühes und spätes Binden</span><span class="sxs-lookup"><span data-stu-id="995b4-129">Early and Late Binding</span></span>](../early-late-binding/index.md)
