---
title: Laden eines "DataSets" aus XML
description: Erfahren Sie, wie Sie Inhalte zu einem ADO.NET-DataSet aus XML hinzufügen. Der .NET Framework bietet Flexibilität für das, was zu laden ist, und die Struktur des Datasets.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0920acac2c82677cfce37703b7027dedce91a535
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166806"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="88494-104">Laden eines "DataSets" aus XML</span><span class="sxs-lookup"><span data-stu-id="88494-104">Loading a DataSet from XML</span></span>

<span data-ttu-id="88494-105">Der Inhalt eines ADO.NET-<xref:System.Data.DataSet> kann aus einem XML-Stream oder einem XML-Dokument erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="88494-105">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="88494-106">Außerdem können Sie mit .NET Framework größtenteils festlegen, welche Informationen aus der XML-Quelle geladen werden sollen und wie das Schema oder die relationale Struktur des <xref:System.Data.DataSet> erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="88494-106">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="88494-107"><xref:System.Data.DataSet>Verwenden Sie die Methode "read **XML** " des-Objekts, um eine mit Daten aus XML auszufüllen <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="88494-107">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="88494-108">Die Read **XML** -Methode liest aus einer Datei, einem Stream oder einem **XmlReader**-Objekt und übernimmt die Quelle des XML-Codes sowie ein optionales **xmllesemode** -Argument als Argumente.</span><span class="sxs-lookup"><span data-stu-id="88494-108">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="88494-109">Weitere Informationen zum **XmlReader**finden Sie unter [Lesen von XML-Daten mit XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="88494-109">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="88494-110">Die Read **XML** -Methode liest den Inhalt des XML-Streams oder-Dokuments und lädt den <xref:System.Data.DataSet> mit Daten.</span><span class="sxs-lookup"><span data-stu-id="88494-110">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="88494-111">Außerdem wird das relationale Schema von erstellt, <xref:System.Data.DataSet> abhängig vom angegebenen **xmllesemode** und davon, ob ein relationales Schema bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="88494-111">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="88494-112">In der folgenden Tabelle werden die Optionen für das **xmllesemode** -Argument beschrieben.</span><span class="sxs-lookup"><span data-stu-id="88494-112">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="88494-113">Option</span><span class="sxs-lookup"><span data-stu-id="88494-113">Option</span></span>|<span data-ttu-id="88494-114">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="88494-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="88494-115">**Automatisch**</span><span class="sxs-lookup"><span data-stu-id="88494-115">**Auto**</span></span>|<span data-ttu-id="88494-116">Dies ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="88494-116">This is the default.</span></span> <span data-ttu-id="88494-117">Prüft die XML-Daten und wählt die am besten geeignete Option in der folgenden Reihenfolge aus:</span><span class="sxs-lookup"><span data-stu-id="88494-117">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="88494-118">-Wenn das XML ein DiffGram ist, wird **DiffGram** verwendet.</span><span class="sxs-lookup"><span data-stu-id="88494-118">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="88494-119">Wenn das <xref:System.Data.DataSet> ein Schema enthält oder das XML ein Inline Schema enthält, wird "read **Schema** " verwendet.</span><span class="sxs-lookup"><span data-stu-id="88494-119">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="88494-120">Wenn das <xref:System.Data.DataSet> kein Schema enthält und das XML kein Inline Schema enthält, wird das **InferSchema** verwendet.</span><span class="sxs-lookup"><span data-stu-id="88494-120">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="88494-121">Wenn Sie das Format des gelesenen XML-Codes kennen, empfiehlt es sich, einen expliziten **xmllesemode**festzulegen, anstatt den **automatischen** Standardwert zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="88494-121">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="88494-122">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="88494-122">**ReadSchema**</span></span>|<span data-ttu-id="88494-123">Liest beliebige Inlineschemata und lädt Daten und Schemata.</span><span class="sxs-lookup"><span data-stu-id="88494-123">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="88494-124">Wenn das <xref:System.Data.DataSet> bereits ein Schema enthält, werden neue Tabellen aus dem Inlineschema zum vorhandenen Schema im <xref:System.Data.DataSet> hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="88494-124">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="88494-125">Wenn bereits Tabellen im Inlineschema des <xref:System.Data.DataSet> vorhanden sind, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="88494-125">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="88494-126">Das Schema einer vorhandenen Tabelle kann nicht mithilfe von **xmllesemode. Read Schema**geändert werden.</span><span class="sxs-lookup"><span data-stu-id="88494-126">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="88494-127">Wenn das <xref:System.Data.DataSet> kein Schema enthält und kein Inlineschema vorhanden ist, werden keine Daten gelesen.</span><span class="sxs-lookup"><span data-stu-id="88494-127">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="88494-128">Ein Inlineschema kann mit dem XSD-Schema (XML Schema Definition Language) definiert werden.</span><span class="sxs-lookup"><span data-stu-id="88494-128">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="88494-129">Ausführliche Informationen zum Schreiben eines Inline Schemas als XML-Schema finden Sie unter [Ableiten einer relationalen DataSet-Struktur aus einem XML-Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="88494-129">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="88494-130">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="88494-130">**IgnoreSchema**</span></span>|<span data-ttu-id="88494-131">Ignoriert alle Inlineschemata und lädt die Daten in das vorhandene <xref:System.Data.DataSet>-Schema.</span><span class="sxs-lookup"><span data-stu-id="88494-131">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="88494-132">Daten, die nicht mit dem vorhandenen Schema übereinstimmen, werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="88494-132">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="88494-133">Wenn kein Schema im <xref:System.Data.DataSet> vorhanden ist, werden keine Daten geladen.</span><span class="sxs-lookup"><span data-stu-id="88494-133">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="88494-134">Wenn es sich bei den Daten um ein DiffGram-DataSet handelt, hat **ignoreschema** die gleiche Funktionalität wie **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="88494-134">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="88494-135">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="88494-135">**InferSchema**</span></span>|<span data-ttu-id="88494-136">Ignoriert alle Inlineschemata, leitet das Schema aus der Struktur der XML-Daten ab und lädt anschließend die Daten.</span><span class="sxs-lookup"><span data-stu-id="88494-136">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="88494-137">Wenn das <xref:System.Data.DataSet> bereits ein Schema enthält, wird das aktuelle Schema durch Hinzufügen von Spalten zu den vorhandenen Tabellen erweitert.</span><span class="sxs-lookup"><span data-stu-id="88494-137">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="88494-138">Wenn keine Tabellen vorhanden sind, werden keine zusätzlichen Tabellen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="88494-138">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="88494-139">Eine Ausnahme wird ausgelöst, wenn bereits eine hergeleitete Tabelle mit einem anderen Namespace vorhanden ist oder wenn hergeleitete Spalten mit vorhandenen Spalten kollidieren.</span><span class="sxs-lookup"><span data-stu-id="88494-139">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="88494-140">Ausführliche Informationen dazu, wie " **infoxmlschema** " ein Schema aus einem XML-Dokument ableitet, finden Sie unter [ableiten der relationalen DataSet-Struktur aus XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="88494-140">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="88494-141">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="88494-141">**DiffGram**</span></span>|<span data-ttu-id="88494-142">	Liest ein DiffGram und fügt die Daten dem aktuellen Schema hinzu.</span><span class="sxs-lookup"><span data-stu-id="88494-142">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="88494-143">**DiffGram** führt neue Zeilen mit vorhandenen Zeilen zusammen, bei denen die eindeutigen Bezeichnerwerte entsprechen.</span><span class="sxs-lookup"><span data-stu-id="88494-143">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="88494-144">Informationen hierzu finden Sie unter "Zusammenführen von Daten aus XML-Dokumenten" am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="88494-144">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="88494-145">Weitere Informationen zu DiffGrams finden Sie unter [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="88494-145">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="88494-146">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="88494-146">**Fragment**</span></span>|<span data-ttu-id="88494-147">Setzt den Lesevorgang für mehrere XML-Fragmente fort, bis das Ende des Streams erreicht ist.</span><span class="sxs-lookup"><span data-stu-id="88494-147">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="88494-148">Fragmente, die mit dem <xref:System.Data.DataSet>-Schema übereinstimmen, werden an die entsprechenden Tabellen angehängt.</span><span class="sxs-lookup"><span data-stu-id="88494-148">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="88494-149">Fragmente, die nicht mit dem <xref:System.Data.DataSet>-Schema übereinstimmen, werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="88494-149">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="88494-150">Wenn Sie einen **XmlReader** an **ReadXml** übergeben, der Teil der Art und Weise in ein XML-Dokument positioniert ist, liest **ReadXml** den nächsten Elementknoten und behandelt dies als Stamm Element, wobei nur bis zum Ende des Element Knotens gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="88494-150">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="88494-151">Dies trifft nicht zu, wenn Sie **xmllesemode. Fragment**angeben.</span><span class="sxs-lookup"><span data-stu-id="88494-151">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="88494-152">DTD-Entitäten</span><span class="sxs-lookup"><span data-stu-id="88494-152">DTD Entities</span></span>  

 <span data-ttu-id="88494-153">Wenn Ihr XML Entitäten enthält, die in einem DTD-Schema (Document Type Definition) definiert sind, wird eine Ausnahme ausgelöst, wenn Sie versuchen, ein zu laden, <xref:System.Data.DataSet> indem Sie einen Dateinamen, einen Stream oder einen nicht validierenden **XmlReader** an die Datei " **infoxml**" übergeben.</span><span class="sxs-lookup"><span data-stu-id="88494-153">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="88494-154">Stattdessen müssen Sie einen **XmlValidatingReader**erstellen, bei dem **EntityHandling** auf **EntityHandling. ExpandEntities**festgelegt ist, und **XmlValidatingReader** an die Datei "read **XML**" übergeben.</span><span class="sxs-lookup"><span data-stu-id="88494-154">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="88494-155">Der **XmlValidatingReader** erweitert die Entitäten, bevor Sie von gelesen werden <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="88494-155">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="88494-156">In den folgenden Codebeispielen wird dargestellt, wie ein <xref:System.Data.DataSet> aus einem XML-Stream geladen wird.</span><span class="sxs-lookup"><span data-stu-id="88494-156">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="88494-157">Das erste Beispiel zeigt, wie ein Dateiname an die Methode "read **XML** " übermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="88494-157">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="88494-158">Im zweiten Beispiel wird eine Zeichenfolge mit XML-Daten mithilfe eines <xref:System.IO.StringReader> geladen.</span><span class="sxs-lookup"><span data-stu-id="88494-158">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> <span data-ttu-id="88494-159">Wenn Sie " **infoxml** " zum Laden einer sehr großen Datei aufzurufen, kann die Leistung beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="88494-159">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="88494-160">Um die beste Leistung für " **infoxml**" zu gewährleisten, müssen Sie die <xref:System.Data.DataTable.BeginLoadData%2A> -Methode für jede Tabelle in der abrufen <xref:System.Data.DataSet> und dann " **infoxml**" aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="88494-160">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="88494-161">Rufen Sie zum Schluss <xref:System.Data.DataTable.EndLoadData%2A> für jede Tabelle im <xref:System.Data.DataSet> auf. Dies wird im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="88494-161">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> <span data-ttu-id="88494-162">Wenn das XSD-Schema für den <xref:System.Data.DataSet> einen **targetNamespace**enthält, werden die Daten möglicherweise nicht gelesen, und beim Aufrufen von "read **XML** " zum Laden von <xref:System.Data.DataSet> mit XML, das Elemente ohne qualifizierenden Namespace enthält, können Ausnahmen auftreten.</span><span class="sxs-lookup"><span data-stu-id="88494-162">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="88494-163">Um nicht qualifizierte Elemente in diesem Fall zu lesen, legen Sie **Element Form default** im XSD-Schema auf "qualified" fest.</span><span class="sxs-lookup"><span data-stu-id="88494-163">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="88494-164">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="88494-164">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="88494-165">	Zusammenführen von Daten aus XML-Dokumenten</span><span class="sxs-lookup"><span data-stu-id="88494-165">Merging Data from XML</span></span>  

 <span data-ttu-id="88494-166">Wenn das <xref:System.Data.DataSet> bereits Daten enthält, werden die neuen Daten aus der XML-Quelle den im <xref:System.Data.DataSet> bereits vorhandenen Daten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="88494-166">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="88494-167">"Read **XML** " wird nicht aus dem XML-Code in die <xref:System.Data.DataSet> Zeilen Informationen mit übereinstimmenden primär Schlüsseln zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="88494-167">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="88494-168">Um vorhandene Zeilen Informationen mit neuen Informationen aus XML zu überschreiben, verwenden Sie " **infoxml** ", um eine neue zu erstellen <xref:System.Data.DataSet> , und dann <xref:System.Data.DataSet.Merge%2A> die neue <xref:System.Data.DataSet> in die vorhandene <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="88494-168">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="88494-169">Beachten Sie, dass beim Laden eines DiffGram mithilfe von "read **XML** " mit dem **xmllesemode** " **DiffGram** " Zeilen zusammengeführt werden, die denselben eindeutigen Bezeichner aufweisen.</span><span class="sxs-lookup"><span data-stu-id="88494-169">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88494-170">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="88494-170">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="88494-171">Using XML in a DataSet (Verwenden von XML in einem DataSet)</span><span class="sxs-lookup"><span data-stu-id="88494-171">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="88494-172">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="88494-172">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="88494-173">Ableiten einer relationalen DataSet-Struktur aus einem XML-Schema (XSD)</span><span class="sxs-lookup"><span data-stu-id="88494-173">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="88494-174">Ableiten einer relationalen DataSet-Struktur aus einem XML-Schema</span><span class="sxs-lookup"><span data-stu-id="88494-174">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="88494-175">Laden von DataSet-Schemainformationen aus XML</span><span class="sxs-lookup"><span data-stu-id="88494-175">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="88494-176">"DataSets", "DataTables" und "DataViews"</span><span class="sxs-lookup"><span data-stu-id="88494-176">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="88494-177">Übersicht über ADO.NET</span><span class="sxs-lookup"><span data-stu-id="88494-177">ADO.NET Overview</span></span>](../ado-net-overview.md)
