---
title: 'Vorgehensweise: Sortieren von Abfrageergebnissen unter Verwendung von LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: 94c2907f05aa9b5b2bc8659cef6f523187f1ef6b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071793"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="6f738-102">Gewusst wie: Sortieren von Abfrageergebnissen unter Verwendung von LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f738-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="6f738-103">Language-Integrated Query (LINQ) vereinfacht den Zugriff auf Datenbankinformationen und das Ausführen von Abfragen.</span><span class="sxs-lookup"><span data-stu-id="6f738-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="6f738-104">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Anwendung erstellen, die Abfragen für eine SQL Server Datenbank ausführt und die Ergebnisse nach mehreren Feldern sortiert, indem Sie die- `Order By` Klausel verwenden.</span><span class="sxs-lookup"><span data-stu-id="6f738-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="6f738-105">Die Sortierreihenfolge für jedes Feld kann eine aufsteigende oder absteigende Reihenfolge sein.</span><span class="sxs-lookup"><span data-stu-id="6f738-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="6f738-106">Weitere Informationen finden Sie unter [Order By-Klausel](../../../language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6f738-106">For more information, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="6f738-107">In den Beispielen in diesem Thema wird die Beispieldatenbank Northwind verwendet.</span><span class="sxs-lookup"><span data-stu-id="6f738-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="6f738-108">Befindet sich diese Datenbank nicht auf Ihrem Entwicklungscomputer, können Sie sie aus dem Microsoft Download Center herunterladen.</span><span class="sxs-lookup"><span data-stu-id="6f738-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="6f738-109">Anweisungen hierzu finden Sie unter [Herunterladen von Beispiel Datenbanken](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="6f738-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="6f738-110">So erstellen Sie eine Verbindung mit einer Datenbank</span><span class="sxs-lookup"><span data-stu-id="6f738-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="6f738-111">Öffnen Sie in Visual Studio **Server-Explorer** / **Datenbank-Explorer** , indem **Server Explorer**Sie / im Menü **Ansicht** auf Server-Explorer**Datenbank-Explorer** klicken.</span><span class="sxs-lookup"><span data-stu-id="6f738-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="6f738-112">Klicken Sie in **Server-Explorer**Datenbank-Explorer mit der rechten Maustaste auf **Datenverbindungen** / **Database Explorer** und dann auf **Verbindung hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6f738-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="6f738-113">Geben Sie eine gültige Verbindung mit der Northwind-Beispieldatenbank an.</span><span class="sxs-lookup"><span data-stu-id="6f738-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="6f738-114">So fügen Sie ein Projekt hinzu, das eine LINQ to SQL Datei enthält</span><span class="sxs-lookup"><span data-stu-id="6f738-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="6f738-115">Zeigen Sie in Visual Studio im Menü **Datei** auf **Neu**, und klicken Sie auf **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="6f738-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="6f738-116">Wählen Sie Visual Basic **Windows Forms Anwendung** als Projekttyp aus.</span><span class="sxs-lookup"><span data-stu-id="6f738-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="6f738-117">Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6f738-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="6f738-118">Wählen Sie die Element Vorlage **LINQ to SQL Klassen** aus.</span><span class="sxs-lookup"><span data-stu-id="6f738-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="6f738-119">Benennen Sie die Datei mit `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="6f738-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="6f738-120">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6f738-120">Click **Add**.</span></span> <span data-ttu-id="6f738-121">Der objektrelationaler Designer (O/R-Designer) wird für die Datei Northwind. dbml geöffnet.</span><span class="sxs-lookup"><span data-stu-id="6f738-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="6f738-122">So fügen Sie dem O/R-Designer abzufragende Tabellen hinzu</span><span class="sxs-lookup"><span data-stu-id="6f738-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="6f738-123">Erweitern Sie in **Server-Explorer** / **Datenbank-Explorer**die Verbindung mit der Northwind-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="6f738-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="6f738-124">Erweitern Sie den Ordner **Tabellen** .</span><span class="sxs-lookup"><span data-stu-id="6f738-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="6f738-125">Wenn Sie den O/R-Designer geschlossen haben, können Sie ihn erneut öffnen, indem Sie auf die Datei Northwind. dbml, die Sie zuvor hinzugefügt haben, doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="6f738-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="6f738-126">Klicken Sie auf die Tabelle Customers, und ziehen Sie Sie in den linken Bereich des Designers.</span><span class="sxs-lookup"><span data-stu-id="6f738-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="6f738-127">Klicken Sie auf die Tabelle Orders, und ziehen Sie Sie in den linken Bereich des Designers.</span><span class="sxs-lookup"><span data-stu-id="6f738-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="6f738-128">Der Designer erstellt neue `Customer` - `Order` Objekte und-Objekte für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="6f738-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="6f738-129">Beachten Sie, dass der Designer automatisch Beziehungen zwischen den Tabellen erkennt und untergeordnete Eigenschaften für verbundene Objekte erstellt.</span><span class="sxs-lookup"><span data-stu-id="6f738-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="6f738-130">IntelliSense zeigt beispielsweise, dass das- `Customer` Objekt über eine- `Orders` Eigenschaft für alle Bestellungen verfügt, die mit diesem Kunden verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="6f738-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="6f738-131">Speichern Sie die Änderungen, und schließen Sie den Designer.</span><span class="sxs-lookup"><span data-stu-id="6f738-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="6f738-132">Speichern Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="6f738-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="6f738-133">So fügen Sie Code hinzu, um die Datenbank abzufragen und die Ergebnisse anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="6f738-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="6f738-134">Ziehen Sie aus der **Toolbox**ein- <xref:System.Windows.Forms.DataGridView> Steuerelement auf das Windows-Standardformular für das Projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="6f738-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="6f738-135">Doppelklicken Sie auf Form1, um dem- `Load` Ereignis des Formulars Code hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6f738-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="6f738-136">Wenn Sie dem O/R-Designer Tabellen hinzugefügt haben, hat der Designer dem Projekt ein-Objekt hinzugefügt <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="6f738-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="6f738-137">Dieses Objekt enthält den Code, den Sie für den Zugriff auf diese Tabellen benötigen, und für den Zugriff auf einzelne Objekte und Auflistungen für jede Tabelle.</span><span class="sxs-lookup"><span data-stu-id="6f738-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="6f738-138">Das- <xref:System.Data.Linq.DataContext> Objekt für das Projekt wird basierend auf dem Namen der DBML-Datei benannt.</span><span class="sxs-lookup"><span data-stu-id="6f738-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="6f738-139">Für dieses Projekt hat das <xref:System.Data.Linq.DataContext> Objekt den Namen `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="6f738-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="6f738-140">Sie können eine Instanz von <xref:System.Data.Linq.DataContext> im Code erstellen und die im O/R-Designer angegebenen Tabellen Abfragen.</span><span class="sxs-lookup"><span data-stu-id="6f738-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="6f738-141">Fügen Sie dem-Ereignis den folgenden Code hinzu `Load` , um die Tabellen abzufragen, die als Eigenschaften des Daten Kontexts verfügbar gemacht werden, und die Ergebnisse zu sortieren.</span><span class="sxs-lookup"><span data-stu-id="6f738-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="6f738-142">Die Abfrage sortiert die Ergebnisse nach der Anzahl der Kunden Bestellungen in absteigender Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="6f738-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="6f738-143">Kunden, die über die gleiche Anzahl von Bestellungen verfügen, werden nach Firmenname in aufsteigender Reihenfolge sortiert (Standard).</span><span class="sxs-lookup"><span data-stu-id="6f738-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. <span data-ttu-id="6f738-144">Drücken Sie F5, um das Projekt auszuführen und die Ergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6f738-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f738-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6f738-145">See also</span></span>

- [<span data-ttu-id="6f738-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="6f738-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="6f738-147">Abfragen</span><span class="sxs-lookup"><span data-stu-id="6f738-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="6f738-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6f738-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="6f738-149">DataContext-Methoden (O/R-Designer)</span><span class="sxs-lookup"><span data-stu-id="6f738-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
