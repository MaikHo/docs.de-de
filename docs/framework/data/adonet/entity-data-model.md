---
title: Entity Data Model
description: Das Entity Data Model beschreibt die Struktur der Daten, unabhängig von Ihrer gespeicherten Form, die Herausforderungen behandelt, die sich aus der Speicherung von Daten in vielen Formularen ergeben.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: d32207e3a9dd35d2d8f8990bcbbd35e38d21d8bb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557618"
---
# <a name="entity-data-model"></a><span data-ttu-id="e06eb-103">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="e06eb-103">Entity Data Model</span></span>
<span data-ttu-id="e06eb-104">Das Entity Data Model (EDM) ist eine Reihe von Konzepten, die die Datenstruktur unabhängig von der gespeicherten Form beschreiben.</span><span class="sxs-lookup"><span data-stu-id="e06eb-104">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="e06eb-105">Das EDM ist aus dem 1976 von Peter Chen beschriebenen Entitätsbeziehungsmodell ausgeliehen, baut aber auch auf dem Entitätsbeziehungsmodell auf und erweitert seine herkömmliche Verwendung.</span><span class="sxs-lookup"><span data-stu-id="e06eb-105">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="e06eb-106">Das EDM löst die Herausforderungen, die sich aus dem Speichern von Daten in vielen Formen ergeben.</span><span class="sxs-lookup"><span data-stu-id="e06eb-106">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="e06eb-107">Denken Sie z. B. an ein Unternehmen, das Daten in relationalen Datenbanken, Textdateien, XML-Dateien, Arbeitsblättern und Berichten speichert.</span><span class="sxs-lookup"><span data-stu-id="e06eb-107">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="e06eb-108">Dies stellt bedeutende Herausforderungen an Datenmodellierung, Anwendungsentwurf und Datenzugriff dar.</span><span class="sxs-lookup"><span data-stu-id="e06eb-108">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="e06eb-109">Beim Entwerfen einer datenorientierten Anwendung besteht die Herausforderung darin, effizienten und verwaltbaren Code zu schreiben, ohne auf effizienten Datenzugriff, Speicherung und Skalierbarkeit zu verzichten.</span><span class="sxs-lookup"><span data-stu-id="e06eb-109">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="e06eb-110">Wenn Daten eine relationale Struktur haben, sind Datenzugriff, Speicherung und Skalierbarkeit sehr effizient, allerdings wird das Schreiben von effizientem und verwaltbarem Code schwieriger.</span><span class="sxs-lookup"><span data-stu-id="e06eb-110">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="e06eb-111">Wenn Daten über eine Objektstruktur verfügen, kehren sich Vor- und Nachteile um: Das Schreiben von effizientem und verwaltbarem Code erfolgt zu Lasten von effizientem Datenzugriff, Speicherung und Skalierbarkeit.</span><span class="sxs-lookup"><span data-stu-id="e06eb-111">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="e06eb-112">Selbst wenn die richtige Balance zwischen diesen Kompromissen gefunden wird, entstehen neue Herausforderungen, wenn Daten zwischen Formen verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="e06eb-112">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="e06eb-113">Das Entity Data Model löst diese Herausforderungen, indem die Datenstruktur in Bezug auf Entitäten und Beziehungen beschrieben wird, die unabhängig von einem Speicherschema sind.</span><span class="sxs-lookup"><span data-stu-id="e06eb-113">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="e06eb-114">Dadurch wird die gespeicherte Datenform unabhängig von Anwendungsentwurf und Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="e06eb-114">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="e06eb-115">Und da Entitäten und Beziehungen die Datenstruktur beschreiben, wie sie in einer Anwendung (nicht der gespeicherten Form) verwendet wird, können sie mit der Anwendung weiterentwickelt werden.</span><span class="sxs-lookup"><span data-stu-id="e06eb-115">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="e06eb-116">Ein `conceptual model` ist eine bestimmte Darstellung der Datenstruktur als Entitäten und Beziehungen und wird im Allgemeinen in einer domänenspezifischen Sprache (DSL) definiert, die die Konzepte des EDM implementiert.</span><span class="sxs-lookup"><span data-stu-id="e06eb-116">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="e06eb-117">Die [konzeptionelle Schema Definitions Sprache (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) ist ein Beispiel für eine solche domänenspezifische Sprache.</span><span class="sxs-lookup"><span data-stu-id="e06eb-117">[Conceptual schema definition language (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) is an example of such a domain-specific language.</span></span> <span data-ttu-id="e06eb-118">In einem konzeptionellen Modell beschriebene Entitäten und Beziehungen können als Abstraktionen von Objekten und Zuordnungen in einer Anwendung betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="e06eb-118">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="e06eb-119">Dadurch können sich Entwickler ohne Beachtung des Speicherschemas auf das konzeptionelle Modell konzentrieren und Code mit dem Schwerpunkt auf Effizienz und Verwaltbarkeit schreiben.</span><span class="sxs-lookup"><span data-stu-id="e06eb-119">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="e06eb-120">In der Zwischenzeit können sich Speicherschema-Designer auf die Effizienz von Datenzugriff, Speicherung und Skalierbarkeit konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="e06eb-120">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e06eb-121">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="e06eb-121">In This Section</span></span>  
 <span data-ttu-id="e06eb-122">In den Themen dieses Abschnitts werden die Konzepte des Entity Data Model erläutert.</span><span class="sxs-lookup"><span data-stu-id="e06eb-122">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="e06eb-123">Jede DSL, die das EDM implementiert, sollte die hier beschriebenen Konzepte enthalten.</span><span class="sxs-lookup"><span data-stu-id="e06eb-123">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="e06eb-124">Beachten Sie, dass das [ADO.NET-Entity Framework](./ef/index.md) CSDL verwendet, um konzeptionelle Modelle zu definieren.</span><span class="sxs-lookup"><span data-stu-id="e06eb-124">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="e06eb-125">Weitere Informationen finden Sie unter [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="e06eb-125">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
 [<span data-ttu-id="e06eb-126">Schlüsselkonzepte im Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="e06eb-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="e06eb-127">Entity Data Model: Namespaces</span><span class="sxs-lookup"><span data-stu-id="e06eb-127">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="e06eb-128">Entity Data Model: primitive Datentypen</span><span class="sxs-lookup"><span data-stu-id="e06eb-128">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="e06eb-129">Entity Data Model: Vererbung</span><span class="sxs-lookup"><span data-stu-id="e06eb-129">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="e06eb-130">Zuordnungsende</span><span class="sxs-lookup"><span data-stu-id="e06eb-130">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="e06eb-131">Multiplizität des Zuordnungsendes</span><span class="sxs-lookup"><span data-stu-id="e06eb-131">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="e06eb-132">Zuordnungssatz</span><span class="sxs-lookup"><span data-stu-id="e06eb-132">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="e06eb-133">Zuordnungssatzende</span><span class="sxs-lookup"><span data-stu-id="e06eb-133">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="e06eb-134">Zuordnungstyp</span><span class="sxs-lookup"><span data-stu-id="e06eb-134">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="e06eb-135">komplexer Typ</span><span class="sxs-lookup"><span data-stu-id="e06eb-135">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="e06eb-136">Entitätscontainer</span><span class="sxs-lookup"><span data-stu-id="e06eb-136">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="e06eb-137">Entitätsschlüssel</span><span class="sxs-lookup"><span data-stu-id="e06eb-137">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="e06eb-138">Entitätenmenge</span><span class="sxs-lookup"><span data-stu-id="e06eb-138">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="e06eb-139">Entitätstyp</span><span class="sxs-lookup"><span data-stu-id="e06eb-139">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="e06eb-140">facet</span><span class="sxs-lookup"><span data-stu-id="e06eb-140">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="e06eb-141">Fremdschlüsseleigenschaft</span><span class="sxs-lookup"><span data-stu-id="e06eb-141">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="e06eb-142">Im Modell deklarierte Funktion</span><span class="sxs-lookup"><span data-stu-id="e06eb-142">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="e06eb-143">Modelldefinierte Funktion</span><span class="sxs-lookup"><span data-stu-id="e06eb-143">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="e06eb-144">Navigationseigenschaft</span><span class="sxs-lookup"><span data-stu-id="e06eb-144">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="e06eb-145">property</span><span class="sxs-lookup"><span data-stu-id="e06eb-145">property</span></span>](property.md)  
  
 [<span data-ttu-id="e06eb-146">Einschränkung der referenziellen Integrität</span><span class="sxs-lookup"><span data-stu-id="e06eb-146">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="e06eb-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e06eb-147">See also</span></span>

- <span data-ttu-id="e06eb-148">[ADO.NET-Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e06eb-148">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="e06eb-149">[Übersicht über die EDMX-Datei](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e06eb-149">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="e06eb-150">CSDL-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="e06eb-150">CSDL Specification</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
