---
title: Behandeln von DataAdapter-Ereignissen
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a2c2dc71cc9e5c445fd05534dad5ad47fd66f436
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194725"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="98f80-102">Behandeln von DataAdapter-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="98f80-102">Handling DataAdapter Events</span></span>

<span data-ttu-id="98f80-103">Der ADO.NET-<xref:System.Data.Common.DataAdapter> macht drei Ereignisse verfügbar, mit denen Sie auf Änderungen der Daten der Datenquelle reagieren können.</span><span class="sxs-lookup"><span data-stu-id="98f80-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="98f80-104">In der folgenden Tabelle finden Sie eine Beschreibung dieser `DataAdapter`-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="98f80-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="98f80-105">Ereignis</span><span class="sxs-lookup"><span data-stu-id="98f80-105">Event</span></span>|<span data-ttu-id="98f80-106">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="98f80-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="98f80-107">Es wird gerade ein Aktualisierungs-, Einfüge- oder Löschvorgang für eine Zeile eingeleitet (durch Aufrufen einer der `Update`-Methoden).</span><span class="sxs-lookup"><span data-stu-id="98f80-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="98f80-108">Ein Update-, Einfüge- oder Löschvorgang für eine Zeile ist abgeschlossen (durch Aufrufen einer der `Update`-Methoden).</span><span class="sxs-lookup"><span data-stu-id="98f80-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="98f80-109">Während eines `Fill`-Vorgangs ist ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="98f80-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="98f80-110">RowUpdating und RowUpdated</span><span class="sxs-lookup"><span data-stu-id="98f80-110">RowUpdating and RowUpdated</span></span>  

 <span data-ttu-id="98f80-111">`RowUpdating` wird ausgelöst, bevor ein Update einer Zeile des <xref:System.Data.DataSet>-Objekts in der Datenquelle verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="98f80-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="98f80-112">`RowUpdated` wird ausgelöst, nachdem ein Update einer Zeile des `DataSet`-Objekts in der Datenquelle verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="98f80-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="98f80-113">Folglich können Sie mit dem `RowUpdating`-Ereignis das Verhalten von Updates ändern, bevor sie vorgenommen werden, zusätzliche Behandlungsoptionen beim Auftreten eines Updates anbieten, einen Verweis auf eine aktualisierte Zeile beibehalten, das aktuelle Update abbrechen und es für die spätere Verarbeitung in einem Stapelverarbeitungsprozess einplanen usw.</span><span class="sxs-lookup"><span data-stu-id="98f80-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="98f80-114">`RowUpdated` ist hilfreich bei der Reaktion auf Fehler und Ausnahmen, die während des Updates auftreten.</span><span class="sxs-lookup"><span data-stu-id="98f80-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="98f80-115">Sie können dem `DataSet` Fehlerinformationen, eine Wiederholungslogik u. a. m. hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="98f80-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="98f80-116">Die Argumente <xref:System.Data.Common.RowUpdatingEventArgs> und <xref:System.Data.Common.RowUpdatedEventArgs>, die an die Ereignisse `RowUpdating` und `RowUpdated` übergeben werden, enthalten Folgendes: eine `Command`-Eigenschaft, die auf das `Command`-Objekt verweist, das zur Ausführung des Updates verwendet wird, eine `Row`-Eigenschaft, die auf das `DataRow`-Objekt verweist, dass die aktualisierten Informationen enthält, eine `StatementType`-Eigenschaft zur Angabe der auszuführenden Updatestypen, die `TableMapping`, sofern zutreffend, und den `Status` des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="98f80-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="98f80-117">Mit der `Status`-Eigenschaft können Sie ermitteln, ob während des Vorgangs ein Fehler aufgetreten ist, und gegebenenfalls die Aktionen für die aktuellen und die resultierenden Zeilen steuern.</span><span class="sxs-lookup"><span data-stu-id="98f80-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="98f80-118">Wenn das Ereignis eintritt, entspricht die `Status`-Eigenschaft entweder `Continue` oder `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="98f80-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="98f80-119">In der folgenden Tabelle sind die Werte dargestellt, die Sie für die `Status`-Eigenschaft festlegen können, um nachfolgende Aktionen während des Updates zu steuern.</span><span class="sxs-lookup"><span data-stu-id="98f80-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="98f80-120">Status</span><span class="sxs-lookup"><span data-stu-id="98f80-120">Status</span></span>|<span data-ttu-id="98f80-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="98f80-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="98f80-122">Setzt den Aktualisierungsvorgang fort.</span><span class="sxs-lookup"><span data-stu-id="98f80-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="98f80-123">Bricht den Updatevorgang ab und löst eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="98f80-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="98f80-124">Ignoriert die aktuelle Zeile und setzt den Aktualisierungsvorgang fort.</span><span class="sxs-lookup"><span data-stu-id="98f80-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="98f80-125">Bricht den Aktualisierungsvorgang ab, löst jedoch keine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="98f80-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="98f80-126">Durch das Festlegen der `Status`-Eigenschaft auf `ErrorsOccurred` wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="98f80-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="98f80-127">Welche Ausnahme ausgelöst wird, können Sie steuern, indem Sie für die `Errors`-Eigenschaft die gewünschte Ausnahme angeben.</span><span class="sxs-lookup"><span data-stu-id="98f80-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="98f80-128">Wenn Sie einen der anderen Werte für `Status` verwenden, wird keine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="98f80-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="98f80-129">Sie können auch die `ContinueUpdateOnError`-Eigenschaft verwenden, um Fehler für aktualisierte Zeilen zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="98f80-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="98f80-130">Wenn für `DataAdapter.ContinueUpdateOnError` der Wert `true` angegeben ist und das Updates einer Zeile eine Ausnahme auslöst, wird der Text der Ausnahme in die `RowError`-Information der entsprechenden Zeile aufgenommen. Die Verarbeitung wird fortgesetzt, ohne dass eine Ausnahme ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="98f80-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="98f80-131">Auf diese Weise können Sie auf Fehler reagieren, wenn `Update` abgeschlossen wurde. Dagegen können Sie beim `RowUpdated`-Ereignis auf den Fehler reagieren, sobald er festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="98f80-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="98f80-132">Im folgenden Codebeispiel wird dargestellt, wie Ereignishandler hinzugefügt und entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="98f80-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="98f80-133">Der `RowUpdating`-Ereignishandler schreibt ein Protokoll aller gelöschten Datensätze und versieht die Löschvorgangaufzeichnungen jeweils mit einem Timestamp.</span><span class="sxs-lookup"><span data-stu-id="98f80-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="98f80-134">Der- `RowUpdated` Ereignishandler fügt Fehlerinformationen zur- `RowError` Eigenschaft der Zeile in der hinzu `DataSet` , unterdrückt die Ausnahme und setzt die Verarbeitung fort (Spiegelung des Verhaltens von `ContinueUpdateOnError`  =  `true` ).</span><span class="sxs-lookup"><span data-stu-id="98f80-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="98f80-135">FillError</span><span class="sxs-lookup"><span data-stu-id="98f80-135">FillError</span></span>  

 <span data-ttu-id="98f80-136">Der `DataAdapter` gibt das `FillError`-Ereignis aus, wenn während des `Fill`-Vorgangs ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="98f80-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="98f80-137">Dieser Fehlertyp tritt auf, wenn die Daten in der hinzugefügten Zeile nicht ohne Präzisionsverlust in einen .NET Framework-Typ konvertiert werden konnten.</span><span class="sxs-lookup"><span data-stu-id="98f80-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="98f80-138">Wenn während eines `Fill`-Vorgangs ein Fehler auftritt, wird der `DataTable` die aktuelle Zeile nicht hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="98f80-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="98f80-139">Mit dem `FillError`-Ereignis können Sie den Fehler auflösen und die Zeile hinzufügen oder die betreffende Zeile ignorieren und den `Fill`-Vorgang fortsetzen.</span><span class="sxs-lookup"><span data-stu-id="98f80-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="98f80-140">Die an das `FillErrorEventArgs`-Ereignis übergebenen `FillError` können mehrere Eigenschaften enthalten, mit denen Sie auf Fehler reagieren und diese auflösen können.</span><span class="sxs-lookup"><span data-stu-id="98f80-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="98f80-141">In der folgenden Tabelle werden die Eigenschaften des `FillErrorEventArgs`-Objekts dargestellt.</span><span class="sxs-lookup"><span data-stu-id="98f80-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="98f80-142">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="98f80-142">Property</span></span>|<span data-ttu-id="98f80-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="98f80-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="98f80-144">Die `Exception`, die aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="98f80-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="98f80-145">Das `DataTable`-Objekt, das ausgefüllt wurde, als der Fehler auftrat.</span><span class="sxs-lookup"><span data-stu-id="98f80-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="98f80-146">Ein Array aus Objekten, das die Werte der beim Eintreten des Fehlers hinzugefügten Zeile enthält.</span><span class="sxs-lookup"><span data-stu-id="98f80-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="98f80-147">Die Ordinalzahlverweise des `Values`-Arrays entsprechen den Ordinalzahlverweisen der Spalten der hinzugefügten Zeile.</span><span class="sxs-lookup"><span data-stu-id="98f80-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="98f80-148">So ist z. B. `Values[0]` der Wert, der als erste Spalte der Zeile hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="98f80-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="98f80-149">Sie können festlegen, ob eine Ausnahme ausgelöst werden soll oder nicht.</span><span class="sxs-lookup"><span data-stu-id="98f80-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="98f80-150">Durch das Festlegen der `Continue`-Eigenschaft auf `false` wird der aktuelle `Fill`-Vorgang angehalten, und es wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="98f80-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="98f80-151">Durch das Festlegen der `Continue`-Eigenschaft auf `true` wird der `Fill`-Vorgang trotz des Fehlers fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="98f80-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="98f80-152">Im folgenden Codebeispiel wird ein Ereignishandler für das `FillError`-Ereignis `DataAdapter` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="98f80-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="98f80-153">Im `FillError`-Ereigniscode bestimmt das Beispiel, ob die Möglichkeit von Präzisionsverlust besteht, und bietet die Chance, auf die Ausnahme zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="98f80-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="98f80-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="98f80-154">See also</span></span>

- [<span data-ttu-id="98f80-155">"DataAdapters" und "DataReaders"</span><span class="sxs-lookup"><span data-stu-id="98f80-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="98f80-156">Behandeln von DataSet-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="98f80-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="98f80-157">Behandeln von DataTable-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="98f80-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="98f80-158">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="98f80-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="98f80-159">Übersicht über ADO.NET</span><span class="sxs-lookup"><span data-stu-id="98f80-159">ADO.NET Overview</span></span>](ado-net-overview.md)
