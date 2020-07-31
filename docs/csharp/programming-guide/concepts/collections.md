---
title: Auflistungen (C#)
description: Hier erfahren Sie mehr über Sammlungen in C#, die für das Arbeiten mit Gruppen von Objekten verwendet werden. Sammlungen können dynamisch vergrößert und verkleinert werden, wenn sich die Anforderungen der Anwendung ändern.
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 2375980e2915d4daa5a221a94eee2aea41959852
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924928"
---
# <a name="collections-c"></a><span data-ttu-id="f53c0-104">Auflistungen (C#)</span><span class="sxs-lookup"><span data-stu-id="f53c0-104">Collections (C#)</span></span>

<span data-ttu-id="f53c0-105">Für eine Vielzahl von Anwendungen sollten Sie Gruppen von miteinander verwandten Objekten erstellen und verwalten.</span><span class="sxs-lookup"><span data-stu-id="f53c0-105">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="f53c0-106">Zum Gruppieren von Objekten gibt es zwei Möglichkeiten: das Erstellen von Objektarrays und das Erstellen von Auflistungen von Objekten.</span><span class="sxs-lookup"><span data-stu-id="f53c0-106">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="f53c0-107">Arrays eignen sich bestens zum Erstellen und Arbeiten mit einer festen Anzahl von Objekten mit starkem Typ.</span><span class="sxs-lookup"><span data-stu-id="f53c0-107">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="f53c0-108">Weitere Informationen zu Arrays finden Sie unter [Arrays](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f53c0-108">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="f53c0-109">Auflistungen ermöglichen ein flexibleres Arbeiten mit Objektgruppen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-109">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="f53c0-110">Im Gegensatz zu Arrays kann sich die Gruppe von Objekten, mit denen Sie arbeiten, in Abhängigkeit von den sich ändernden Anforderungen der Anwendung dynamisch vergrößern bzw. verkleinern.</span><span class="sxs-lookup"><span data-stu-id="f53c0-110">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="f53c0-111">Bei einigen Auflistungen können Sie jedem Objekt, das Sie in die Auflistung einfügen, einen Schlüssel zuweisen, sodass das Objekt anhand des Schlüssels schnell abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f53c0-111">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="f53c0-112">Eine Auflistung ist eine Klasse. Daher müssen Sie eine Instanzen der Klasse deklarieren, bevor Sie dieser Auflistung Elemente hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="f53c0-112">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="f53c0-113">Wenn die Auflistung Elemente eines Datentyps enthält, können Sie eine der Klassen im <xref:System.Collections.Generic?displayProperty=nameWithType>-Namespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="f53c0-113">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f53c0-114">Eine generische Auflistung erzwingt Typsicherheit, sodass der Auflistung kein anderer Datentyp hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f53c0-114">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="f53c0-115">Wenn Sie ein Element aus einer generischen Auflistung abrufen, brauchen Sie dessen Datentyp nicht zu bestimmen oder zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="f53c0-115">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="f53c0-116">Schließen Sie bei den Beispielen in diesem Thema [using](../../language-reference/keywords/using-directive.md)-Anweisungen für die `System.Collections.Generic`- und `System.Linq`-Namespaces ein.</span><span class="sxs-lookup"><span data-stu-id="f53c0-116">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="f53c0-117">**Inhalt**</span><span class="sxs-lookup"><span data-stu-id="f53c0-117">**In this topic**</span></span>

- [<span data-ttu-id="f53c0-118">Verwenden einer einfachen Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-118">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="f53c0-119">Arten von Auflistungen</span><span class="sxs-lookup"><span data-stu-id="f53c0-119">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="f53c0-120">System.Collections.Generic-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-120">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="f53c0-121">System.Collections.Concurrent-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-121">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="f53c0-122">System.Collections-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-122">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="f53c0-123">Implementieren einer Auflistung von Schlüssel-Wert-Paaren</span><span class="sxs-lookup"><span data-stu-id="f53c0-123">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="f53c0-124">Verwenden von LINQ zum Zugriff auf eine Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-124">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="f53c0-125">Sortieren einer Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-125">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="f53c0-126">Definieren einer benutzerdefinierten Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-126">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="f53c0-127">Iteratoren</span><span class="sxs-lookup"><span data-stu-id="f53c0-127">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="f53c0-128">Verwenden einer einfachen Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-128">Using a Simple Collection</span></span>

<span data-ttu-id="f53c0-129">In den Beispielen in diesem Abschnitt wird die generische Klasse <xref:System.Collections.Generic.List%601> verwendet, die es Ihnen ermöglicht, mit einer stark typisierten Liste von Objekten zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="f53c0-129">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="f53c0-130">Im folgenden Beispiel wird eine Liste von Zeichenfolgen erstellt, und die Zeichenfolgen werden unter Verwendung einer [foreach](../../language-reference/keywords/foreach-in.md)-Anweisung durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-130">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="f53c0-131">Wenn der Inhalt einer Auflistung im Voraus bekannt ist, können Sie einen *Auflistungsinitialisierer* verwenden, um die Auflistung zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="f53c0-131">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="f53c0-132">Weitere Informationen finden Sie unter [Objekt- und Auflistungsinitialisierer](../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="f53c0-132">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="f53c0-133">Das folgende Beispiel entspricht dem vorherigen Beispiel, außer dass ein Auflistungsinitialisierer verwendet wird, um der Auflistung Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-133">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="f53c0-134">Sie können anstelle einer [for](../../language-reference/keywords/for.md)-Anweisung eine `foreach`-Anweisung verwenden, um eine Auflistung zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-134">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="f53c0-135">Sie erreichen dies, indem Sie durch die Indexposition auf die Auflistungselemente zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-135">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="f53c0-136">Der Index der Elemente beginnt mit 0 und endet an der Elementanzahl minus 1.</span><span class="sxs-lookup"><span data-stu-id="f53c0-136">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="f53c0-137">Im folgenden Beispiel werden die Elemente einer Auflistung unter Verwendung von `for` anstelle von `foreach` durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-137">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="f53c0-138">Im folgenden Beispiel wird ein Element aus der Auflistung entfernt, indem das zu entfernende Objekt angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f53c0-138">The following example removes an element from the collection by specifying the object to remove.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

<span data-ttu-id="f53c0-139">Im folgenden Beispiel werden alle Elemente aus einer generischen Liste entfernt.</span><span class="sxs-lookup"><span data-stu-id="f53c0-139">The following example removes elements from a generic list.</span></span> <span data-ttu-id="f53c0-140">Anstelle einer `foreach`-Anweisung wird eine [for](../../language-reference/keywords/for.md)-Anweisung verwendet, die die Elemente in absteigender Reihenfolge durchläuft.</span><span class="sxs-lookup"><span data-stu-id="f53c0-140">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="f53c0-141">Dies liegt daran, dass die <xref:System.Collections.Generic.List%601.RemoveAt%2A>-Methode dazu führt, dass Elemente nach einem entfernten Element einen niedrigeren Indexwert haben.</span><span class="sxs-lookup"><span data-stu-id="f53c0-141">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

<span data-ttu-id="f53c0-142">Für den Typ der Elemente in <xref:System.Collections.Generic.List%601> können Sie auch eine eigene Klasse definieren.</span><span class="sxs-lookup"><span data-stu-id="f53c0-142">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="f53c0-143">Im folgenden Beispiel wird die `Galaxy`-Klasse, die von <xref:System.Collections.Generic.List%601> verwendet wird, im Code definiert.</span><span class="sxs-lookup"><span data-stu-id="f53c0-143">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="f53c0-144">Arten von Auflistungen</span><span class="sxs-lookup"><span data-stu-id="f53c0-144">Kinds of Collections</span></span>

<span data-ttu-id="f53c0-145">Viele häufig verwendete Sammlungen werden von .NET bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f53c0-145">Many common collections are provided by .NET.</span></span> <span data-ttu-id="f53c0-146">Jeder Auflistungstyp ist für einen speziellen Zweck ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="f53c0-146">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="f53c0-147">Einige der häufig verwendeten Auflistungsklassen werden in diesem Abschnitt beschrieben:</span><span class="sxs-lookup"><span data-stu-id="f53c0-147">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="f53c0-148"><xref:System.Collections.Generic>-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-148"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="f53c0-149"><xref:System.Collections.Concurrent>-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-149"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="f53c0-150"><xref:System.Collections>-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-150"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="f53c0-151">System.Collections.Generic-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-151">System.Collections.Generic Classes</span></span>

<span data-ttu-id="f53c0-152">Zum Erstellen einer generischen Auflistung verwenden Sie eine der Klassen im <xref:System.Collections.Generic>-Namespace.</span><span class="sxs-lookup"><span data-stu-id="f53c0-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="f53c0-153">Eine generische Auflistung ist sinnvoll, wenn jedes Element der Auflistung zum gleichen Datentyp gehört.</span><span class="sxs-lookup"><span data-stu-id="f53c0-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="f53c0-154">Eine generische Auflistung erzwingt eine starke Typisierung, da ihr nur Elemente des gewünschten Datentyps hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="f53c0-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="f53c0-155">In der folgenden Tabelle werden einige der häufig verwendeten Klassen des <xref:System.Collections.Generic?displayProperty=nameWithType>-Namespace aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="f53c0-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="f53c0-156">Klasse</span><span class="sxs-lookup"><span data-stu-id="f53c0-156">Class</span></span>|<span data-ttu-id="f53c0-157">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="f53c0-157">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="f53c0-158">Stellt eine Auflistung von Schlüssel-Wert-Paaren dar, deren Reihenfolge anhand des Schlüssels bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="f53c0-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="f53c0-159">Stellt eine Liste von Objekten dar, auf die über einen Index zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f53c0-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="f53c0-160">Stellt Methoden zum Durchsuchen, Sortieren und Bearbeiten von Listen bereit.</span><span class="sxs-lookup"><span data-stu-id="f53c0-160">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="f53c0-161">Stellt eine FIFO-Auflistung (First In, First Out) von Objekten dar.</span><span class="sxs-lookup"><span data-stu-id="f53c0-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="f53c0-162">Stellt eine Auflistung von Schlüssel-Wert-Paaren dar, die auf Grundlage der zugeordneten <xref:System.Collections.Generic.IComparer%601>-Implementierung nach den Schlüsseln sortiert sind.</span><span class="sxs-lookup"><span data-stu-id="f53c0-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="f53c0-163">Stellt eine LIFO-Auflistung (Last In, First Out) von Objekten dar.</span><span class="sxs-lookup"><span data-stu-id="f53c0-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f53c0-164">Weitere Informationen finden Sie unter [Häufig verwendete Auflistungstypen](../../../standard/collections/commonly-used-collection-types.md), [Auswählen einer Auflistungsklasse](../../../standard/collections/selecting-a-collection-class.md) und <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="f53c0-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="f53c0-165">System.Collections.Concurrent-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-165">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="f53c0-166">In .NET Framework 4 oder höher stellen die Sammlungen im Namespace <xref:System.Collections.Concurrent> effiziente, threadsichere Vorgänge für den Zugriff auf Sammlungselemente über mehrere Threads bereit.</span><span class="sxs-lookup"><span data-stu-id="f53c0-166">In .NET Framework 4 and later versions, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="f53c0-167">Die Klassen im <xref:System.Collections.Concurrent>-Namespace sollten anstelle von entsprechenden Typen in <xref:System.Collections.Generic?displayProperty=nameWithType>- und <xref:System.Collections?displayProperty=nameWithType>-Namespaces verwendet werden, wenn mehrere Threads gleichzeitig auf die Auflistung zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="f53c0-168">Weitere Informationen finden Sie unter [Threadsichere Auflistungen](../../../standard/collections/thread-safe/index.md) und <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="f53c0-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="f53c0-169">Einige der in die <xref:System.Collections.Concurrent>-Namespaces aufgenommenen Klassen sind <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> und <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="f53c0-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="f53c0-170">System.Collections-Klassen</span><span class="sxs-lookup"><span data-stu-id="f53c0-170">System.Collections Classes</span></span>

<span data-ttu-id="f53c0-171">Bei den Klassen im <xref:System.Collections?displayProperty=nameWithType>-Namespace werden Elemente nicht als speziell typisierte Objekte, sondern als Objekte vom Typ `Object` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="f53c0-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="f53c0-172">Sofern möglich sollten die generischen Auflistungen im <xref:System.Collections.Generic?displayProperty=nameWithType>-Namespace oder <xref:System.Collections.Concurrent>-Namespace anstelle der älteren Typen im `System.Collections`-Namespace verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f53c0-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="f53c0-173">In der folgenden Tabelle werden einige der häufig verwendeten Klassen im `System.Collections`-Namespace aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="f53c0-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="f53c0-174">Klasse</span><span class="sxs-lookup"><span data-stu-id="f53c0-174">Class</span></span>|<span data-ttu-id="f53c0-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f53c0-175">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="f53c0-176">Stellt ein Array von Objekten dar, das je nach Bedarf dynamisch vergrößert wird.</span><span class="sxs-lookup"><span data-stu-id="f53c0-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="f53c0-177">Stellt eine Auflistung von Schlüssel-Wert-Paaren dar, die auf Grundlage des Hashcodes des Schlüssels geordnet sind.</span><span class="sxs-lookup"><span data-stu-id="f53c0-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="f53c0-178">Stellt eine FIFO-Auflistung (First In, First Out) von Objekten dar.</span><span class="sxs-lookup"><span data-stu-id="f53c0-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="f53c0-179">Stellt eine LIFO-Auflistung (Last In, First Out) von Objekten dar.</span><span class="sxs-lookup"><span data-stu-id="f53c0-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f53c0-180">Der <xref:System.Collections.Specialized>-Namespace bietet spezialisierte und stark typisierte Auflistungsklassen, beispielsweise für Zeichenfolgenauflistungen sowie für Wörterbücher mit verketteten Listen und Hybridwörterbücher.</span><span class="sxs-lookup"><span data-stu-id="f53c0-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="f53c0-181">Implementieren einer Auflistung von Schlüssel/Wert-Paaren</span><span class="sxs-lookup"><span data-stu-id="f53c0-181">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="f53c0-182">Die generische Auflistung <xref:System.Collections.Generic.Dictionary%602> ermöglicht es Ihnen, unter Verwendung des Schlüssels der einzelnen Elemente auf die Elemente einer Auflistung zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-182">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="f53c0-183">Jede Hinzufügung zum Wörterbuch besteht aus einem Wert und dem zugeordneten Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="f53c0-183">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="f53c0-184">Ein Wert kann anhand des zugehörigen Schlüssels schnell abgerufen werden, da die `Dictionary`-Klasse in Form einer Hashtabelle implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="f53c0-184">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="f53c0-185">Das folgende Beispiel erstellt eine `Dictionary`-Auflistung und durchläuft das Wörterbuch unter Verwendung einer `foreach`-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="f53c0-185">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<span data-ttu-id="f53c0-186">Wenn stattdessen ein Auflistungsinitialisierer zum Erstellen der `Dictionary`-Auflistung verwendet werden soll, können Sie die `BuildDictionary`- und `AddToDictionary`-Methoden durch die folgende Methode ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-186">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

<span data-ttu-id="f53c0-187">Im folgenden Beispiel werden die <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>-Methode und die <xref:System.Collections.Generic.Dictionary%602.Item%2A>-Eigenschaft von `Dictionary` verwendet, um anhand des Schlüssels schnell nach einem Element zu suchen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-187">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="f53c0-188">Die `Item`-Eigenschaft ermöglicht den Zugriff auf ein Element in der `elements`-Auflistung unter Verwendung des `elements[symbol]`-Codes in C#.</span><span class="sxs-lookup"><span data-stu-id="f53c0-188">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

<span data-ttu-id="f53c0-189">Im folgenden Beispiel wird stattdessen die <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>-Methode verwendet, um anhand des Schlüssels schnell nach einem Element zu suchen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-189">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="f53c0-190">Verwenden von LINQ zum Zugriff auf eine Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-190">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="f53c0-191">LINQ (Language-Integrated Query) kann verwendet werden, um auf Auflistungen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-191">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="f53c0-192">LINQ-Abfragen stellen Filter-, Sortier- und Gruppierungsfunktionen bereit.</span><span class="sxs-lookup"><span data-stu-id="f53c0-192">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="f53c0-193">Weitere Informationen finden Sie unter [Erste Schritte mit LINQ in C#](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="f53c0-193">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="f53c0-194">Im folgenden Beispiel wird eine LINQ-Abfrage für eine generische `List` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f53c0-194">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="f53c0-195">Die LINQ-Abfrage gibt eine andere Auflistung zurück, die die Ergebnisse enthält.</span><span class="sxs-lookup"><span data-stu-id="f53c0-195">The LINQ query returns a different collection that contains the results.</span></span>

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="f53c0-196">Sortieren einer Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-196">Sorting a Collection</span></span>

<span data-ttu-id="f53c0-197">Das folgende Beispiel zeigt ein Verfahren zum Sortieren einer Auflistung.</span><span class="sxs-lookup"><span data-stu-id="f53c0-197">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="f53c0-198">In dem Beispiel werden Instanzen der `Car`-Klasse sortiert, die in <xref:System.Collections.Generic.List%601> gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="f53c0-198">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f53c0-199">Die `Car`-Klasse implementiert die <xref:System.IComparable%601>-Schnittstelle, die die Implementierung der <xref:System.IComparable%601.CompareTo%2A>-Methode erfordert.</span><span class="sxs-lookup"><span data-stu-id="f53c0-199">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="f53c0-200">Jeder Aufruf der <xref:System.IComparable%601.CompareTo%2A>-Methode führt einen einzelnen Vergleich aus, der für die Sortierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f53c0-200">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="f53c0-201">Vom Benutzer erstellter Code in der `CompareTo`-Methode gibt einen Wert für jeden Vergleich des aktuellen Objekts mit einem anderen Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="f53c0-201">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="f53c0-202">Der zurückgegebene Wert ist kleiner als Null, wenn das aktuelle Objekt kleiner ist als das andere Objekt, größer als Null, wenn das aktuelle Objekt größer als das andere Objekt ist und Null, wenn beide Objekt gleich groß sind.</span><span class="sxs-lookup"><span data-stu-id="f53c0-202">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="f53c0-203">Dies ermöglicht es Ihnen, in dem Code die Kriterien für größer als, kleiner als und gleich zu definieren.</span><span class="sxs-lookup"><span data-stu-id="f53c0-203">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="f53c0-204">In der `ListCars`-Methode sortiert die `cars.Sort()`-Anweisung die Liste.</span><span class="sxs-lookup"><span data-stu-id="f53c0-204">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="f53c0-205">Dieser Aufruf der <xref:System.Collections.Generic.List%601.Sort%2A>-Methode von <xref:System.Collections.Generic.List%601> führt dazu, dass die `CompareTo`-Methode für die `Car`-Objekte in der `List` automatisch aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f53c0-205">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="f53c0-206">Definieren einer benutzerdefinierten Auflistung</span><span class="sxs-lookup"><span data-stu-id="f53c0-206">Defining a Custom Collection</span></span>

<span data-ttu-id="f53c0-207">Sie können eine Auflistung definieren, indem Sie die <xref:System.Collections.Generic.IEnumerable%601>- oder <xref:System.Collections.IEnumerable>-Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="f53c0-207">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="f53c0-208">Sie können zwar eine benutzerdefinierte Sammlung definieren, in der Regel ist es aber besser, die in .NET enthaltenen Sammlungen zu verwenden. Diese werden weiter oben unter [Arten von Sammlungen](#BKMK_KindsOfCollections) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f53c0-208">Although you can define a custom collection, it is usually better to instead use the collections that are included in .NET, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this article.</span></span>

<span data-ttu-id="f53c0-209">Im folgenden Beispiel wird die benutzerdefinierte Auflistungsklasse `AllColors` definiert.</span><span class="sxs-lookup"><span data-stu-id="f53c0-209">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="f53c0-210">Diese Klasse implementiert die <xref:System.Collections.IEnumerable>-Schnittstelle, die die Implementierung der <xref:System.Collections.IEnumerable.GetEnumerator%2A>-Methode erfordert.</span><span class="sxs-lookup"><span data-stu-id="f53c0-210">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="f53c0-211">Die `GetEnumerator`-Methode gibt eine Instanz der `ColorEnumerator`-Klasse zurück.</span><span class="sxs-lookup"><span data-stu-id="f53c0-211">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="f53c0-212">`ColorEnumerator` implementiert die <xref:System.Collections.IEnumerator>-Schnittstelle, die die Implementierung der <xref:System.Collections.IEnumerator.Current%2A>-Eigenschaft, der <xref:System.Collections.IEnumerator.MoveNext%2A>-Methode und der <xref:System.Collections.IEnumerator.Reset%2A>-Methode erfordert.</span><span class="sxs-lookup"><span data-stu-id="f53c0-212">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="f53c0-213">Iterators</span><span class="sxs-lookup"><span data-stu-id="f53c0-213">Iterators</span></span>

<span data-ttu-id="f53c0-214">Ein *Iterator* wird verwendet, um eine benutzerdefinierte Iteration durch eine Auflistung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f53c0-214">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="f53c0-215">Ein Iterator kann eine Methode oder ein `get`-Accessor sein.</span><span class="sxs-lookup"><span data-stu-id="f53c0-215">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="f53c0-216">Ein Iterator verwendet eine [yield return](../../language-reference/keywords/yield.md)-Anweisung, um jedes Element der Auflistung separat zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="f53c0-216">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="f53c0-217">Sie rufen einen Iterator mithilfe einer [foreach](../../language-reference/keywords/foreach-in.md)-Anweisung auf.</span><span class="sxs-lookup"><span data-stu-id="f53c0-217">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="f53c0-218">Jede Iteration der `foreach`-Schleife ruft den Iterator auf.</span><span class="sxs-lookup"><span data-stu-id="f53c0-218">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="f53c0-219">Wenn eine `yield return`-Anweisung im Iterator erreicht ist, wird ein Ausdruck zurückgegeben, und die aktuelle Position im Code wird beibehalten.</span><span class="sxs-lookup"><span data-stu-id="f53c0-219">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="f53c0-220">Wenn der Iterator das nächste Mal aufgerufen wird, wird die Ausführung von dieser Position neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="f53c0-220">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="f53c0-221">Weitere Informationen finden Sie unter [Iteratoren (C#)](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="f53c0-221">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="f53c0-222">Im folgenden Beispiel wird eine Iteratormethode verwendet.</span><span class="sxs-lookup"><span data-stu-id="f53c0-222">The following example uses an iterator method.</span></span> <span data-ttu-id="f53c0-223">Die Iteratormethode verfügt über eine `yield return`-Anweisung, die sich innerhalb einer [for](../../language-reference/keywords/for.md)-Schleife befindet.</span><span class="sxs-lookup"><span data-stu-id="f53c0-223">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="f53c0-224">In der `ListEvenNumbers`-Methode erstellt jede Iteration des `foreach`-Anweisungstexts einen Aufruf der Iteratormethode, der zur nächsten `yield return`-Anweisung übergeht.</span><span class="sxs-lookup"><span data-stu-id="f53c0-224">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f53c0-225">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f53c0-225">See also</span></span>

- [<span data-ttu-id="f53c0-226">Objekt- und Auflistungsinitialisierer</span><span class="sxs-lookup"><span data-stu-id="f53c0-226">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="f53c0-227">Programmierkonzepte (C#)</span><span class="sxs-lookup"><span data-stu-id="f53c0-227">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="f53c0-228">Option Strict-Anweisung</span><span class="sxs-lookup"><span data-stu-id="f53c0-228">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f53c0-229">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="f53c0-229">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="f53c0-230">Parallel LINQ (PLINQ) (Paralleles LINQ (PLINQ))</span><span class="sxs-lookup"><span data-stu-id="f53c0-230">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="f53c0-231">Sammlungen und Datenstrukturen</span><span class="sxs-lookup"><span data-stu-id="f53c0-231">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="f53c0-232">Auswählen einer Auflistungsklasse</span><span class="sxs-lookup"><span data-stu-id="f53c0-232">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="f53c0-233">Vergleiche und Sortierungen innerhalb von Auflistungen</span><span class="sxs-lookup"><span data-stu-id="f53c0-233">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="f53c0-234">Verwenden von generischen Auflistungen</span><span class="sxs-lookup"><span data-stu-id="f53c0-234">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
