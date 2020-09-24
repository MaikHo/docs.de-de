---
title: Aktivieren von Multiple Active Result Sets
description: Erfahren Sie, wie Sie Mars in einer Verbindungs Zeichenfolge aktivieren bzw. deaktivieren, die mit SQL Server funktioniert, sodass Sie mehrere Batches in einer einzelnen Verbindung in ADO.net ausführen können.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 0c5b4043b389c7dde39a477f90e82bbf654331f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156250"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="610bc-103">Aktivieren von Multiple Active Result Sets</span><span class="sxs-lookup"><span data-stu-id="610bc-103">Enabling Multiple Active Result Sets</span></span>

<span data-ttu-id="610bc-104">MARS ist eine Funktion, die mit SQL Server verwendet wird und das Ausführen mehrerer Batches über eine einzelne Verbindung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="610bc-104">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="610bc-105">Wenn MARS für die Verwendung mit SQL Server aktiviert wird, fügen die einzelnen verwendeten Befehlsobjekte der Verbindung eine Sitzung hinzu.</span><span class="sxs-lookup"><span data-stu-id="610bc-105">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="610bc-106">Eine einzelne MARS-Sitzung öffnet eine logische Verbindung, die MARS verwenden kann, und dann eine logische Verbindung für jeden aktiven Befehl.</span><span class="sxs-lookup"><span data-stu-id="610bc-106">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="610bc-107">Aktivieren und Deaktivieren von MARS in der Verbindungszeichenfolge</span><span class="sxs-lookup"><span data-stu-id="610bc-107">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
> <span data-ttu-id="610bc-108">Die folgenden Verbindungszeichenfolgen verwenden die **AdventureWorks**-Beispieldatenbank aus SQL Server.</span><span class="sxs-lookup"><span data-stu-id="610bc-108">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="610bc-109">Die angegebenen Verbindungszeichenfolgen setzen voraus, dass die Datenbank auf einem Server namens MSSQL1 installiert ist.</span><span class="sxs-lookup"><span data-stu-id="610bc-109">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="610bc-110">Ändern Sie die Verbindungszeichenfolge nach Bedarf für Ihre Umgebung.</span><span class="sxs-lookup"><span data-stu-id="610bc-110">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="610bc-111">Die MARS-Feature ist standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="610bc-111">The MARS feature is disabled by default.</span></span> <span data-ttu-id="610bc-112">Sie kann durch Hinzufügen des Schlüsselwortpaares „MultipleActiveResultSets=True“ zu Ihrer Verbindungszeichenfolge aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="610bc-112">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="610bc-113">„True“ ist der einzige gültige Wert zum Aktivieren von MARS.</span><span class="sxs-lookup"><span data-stu-id="610bc-113">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="610bc-114">Das folgende Beispiel zeigt, wie eine Verbindung mit einer Instanz von SQL Server hergestellt wird und wie angegeben wird, dass MARS aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="610bc-114">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="610bc-115">Sie können MARS deaktivieren, indem Sie das Schlüsselwortpaar „MultipleActiveResultSets=False“ zu Ihrer Verbindungszeichenfolge hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="610bc-115">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="610bc-116">„False“ ist der einzige gültige Wert zum Deaktivieren von MARS.</span><span class="sxs-lookup"><span data-stu-id="610bc-116">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="610bc-117">Die folgende Verbindungszeichenfolge zeigt, wie MARS deaktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="610bc-117">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="610bc-118">Besondere Überlegungen bei der Verwendung von MARS</span><span class="sxs-lookup"><span data-stu-id="610bc-118">Special Considerations When Using MARS</span></span>  

 <span data-ttu-id="610bc-119">Im Allgemeinen sollten bestehende Anwendungen nicht modifiziert werden müssen, um eine MARS-fähige Verbindung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="610bc-119">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="610bc-120">Wenn Sie jedoch MARS-Features in Ihren Anwendungen verwenden möchten, sollten Sie mit den folgenden besonderen Aspekten vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="610bc-120">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="610bc-121">Überlappen von Anweisungen</span><span class="sxs-lookup"><span data-stu-id="610bc-121">Statement Interleaving</span></span>  

 <span data-ttu-id="610bc-122">MARS-Vorgänge werden auf dem Server synchron ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="610bc-122">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="610bc-123">Die Überlappung von SELECT- und BULK INSERT-Anweisungen ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="610bc-123">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="610bc-124">DML- (Data Manipulation Language) und DDL-Anweisungen (Data Definition Language) werden jedoch atomisch ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="610bc-124">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="610bc-125">Alle Anweisungen, die versuchen, während der Ausführung eines atomischen Batches ausgeführt zu werden, werden blockiert.</span><span class="sxs-lookup"><span data-stu-id="610bc-125">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="610bc-126">Die parallele Ausführung auf dem Server ist kein MARS-Feature.</span><span class="sxs-lookup"><span data-stu-id="610bc-126">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="610bc-127">Wenn zwei Batches über eine MARS-Verbindung übermittelt werden, von denen einer eine SELECT-Anweisung und der andere eine DML-Anweisung enthält, kann DML mit der Ausführung innerhalb der Ausführung der SELECT-Anweisung beginnen.</span><span class="sxs-lookup"><span data-stu-id="610bc-127">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="610bc-128">Die DML-Anweisung muss jedoch vollständig abgeschlossen werden, ehe die SELECT-Anweisung fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="610bc-128">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="610bc-129">Wenn beide Anweisungen innerhalb derselben Transaktion ausgeführt werden, sind alle Änderungen, die durch eine DML-Anweisung nach Beginn der Ausführung der SELECT-Anweisung vorgenommen werden, für den Lesevorgang nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="610bc-129">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="610bc-130">Eine WAITFOR-Anweisung innerhalb einer SELECT-Anweisung hält die Transaktion nicht an, während sie wartet, d. h. bis die erste Zeile erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="610bc-130">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="610bc-131">Dies bedeutet, dass keine anderen Batches innerhalb der gleichen Verbindung ausgeführt werden können, während eine WAITFOR-Anweisung wartet.</span><span class="sxs-lookup"><span data-stu-id="610bc-131">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="610bc-132">MARS-Sitzungscache</span><span class="sxs-lookup"><span data-stu-id="610bc-132">MARS Session Cache</span></span>  

 <span data-ttu-id="610bc-133">Wenn eine Verbindung mit aktiviertem MARS geöffnet wird, wird eine logische Sitzung erstellt, was zusätzlichen Aufwand bedeutet.</span><span class="sxs-lookup"><span data-stu-id="610bc-133">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="610bc-134">Um den Mehraufwand zu minimieren und die Leistungsfähigkeit zu erhöhen, führt **SqlClient** eine Zwischenspeicherung der MARS-Sitzung in einer Verbindung durch.</span><span class="sxs-lookup"><span data-stu-id="610bc-134">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="610bc-135">Der Cache enthält höchstens 10 MARS-Sitzungen.</span><span class="sxs-lookup"><span data-stu-id="610bc-135">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="610bc-136">Dieser Wert kann nicht vom Benutzer angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="610bc-136">This value is not user adjustable.</span></span> <span data-ttu-id="610bc-137">Bei Erreichen des Sitzungslimits wird eine neue Sitzung erstellt, ohne dass ein Fehler ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="610bc-137">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="610bc-138">Der Cache und die darin enthaltenen Sitzungen sind verbindungsbezogen. Daher werden sie nicht von verschiedenen Verbindungen gemeinsam genutzt.</span><span class="sxs-lookup"><span data-stu-id="610bc-138">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="610bc-139">Sobald eine Sitzung freigegeben wird, wird sie an den Pool zurückgegeben, es sei denn, die Obergrenze des Pools ist erreicht.</span><span class="sxs-lookup"><span data-stu-id="610bc-139">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="610bc-140">Wenn der Cachepool voll ist, wird die Sitzung geschlossen.</span><span class="sxs-lookup"><span data-stu-id="610bc-140">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="610bc-141">MARS-Sitzungen laufen nicht ab.</span><span class="sxs-lookup"><span data-stu-id="610bc-141">MARS sessions do not expire.</span></span> <span data-ttu-id="610bc-142">Sie werden lediglich bereinigt, wenn das Verbindungsobjekt verworfen wird.</span><span class="sxs-lookup"><span data-stu-id="610bc-142">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="610bc-143">Der MARS-Sitzungscache wird nicht vorab geladen.</span><span class="sxs-lookup"><span data-stu-id="610bc-143">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="610bc-144">Er wird geladen, sobald die Anwendung mehr Sitzungen benötigt.</span><span class="sxs-lookup"><span data-stu-id="610bc-144">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="610bc-145">Threadsicherheit</span><span class="sxs-lookup"><span data-stu-id="610bc-145">Thread Safety</span></span>  

 <span data-ttu-id="610bc-146">MARS-Vorgänge sind nicht threadsicher.</span><span class="sxs-lookup"><span data-stu-id="610bc-146">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="610bc-147">Verbindungspooling</span><span class="sxs-lookup"><span data-stu-id="610bc-147">Connection Pooling</span></span>  

 <span data-ttu-id="610bc-148">MARS-fähige Verbindungen lassen sich wie andere Verbindungen in einem Pool zusammenfassen.</span><span class="sxs-lookup"><span data-stu-id="610bc-148">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="610bc-149">Wenn eine Anwendung zwei Verbindungen öffnet, eine mit aktiviertem und eine mit deaktiviertem MARS, befinden sich die beiden Verbindungen in getrennten Pools.</span><span class="sxs-lookup"><span data-stu-id="610bc-149">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="610bc-150">Weitere Informationen finden Sie unter [SQL Server-Verbindungspooling (ADO.NET)](../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="610bc-150">For more information, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="610bc-151">SQL Server-Batchausführungsumgebung</span><span class="sxs-lookup"><span data-stu-id="610bc-151">SQL Server Batch Execution Environment</span></span>  

 <span data-ttu-id="610bc-152">Beim Öffnen einer Verbindung wird eine Standardumgebung definiert.</span><span class="sxs-lookup"><span data-stu-id="610bc-152">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="610bc-153">Diese Umgebung wird dann in eine logische MARS-Sitzung kopiert.</span><span class="sxs-lookup"><span data-stu-id="610bc-153">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="610bc-154">Die Batchausführungsumgebung umfasst die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="610bc-154">The batch execution environment includes the following components:</span></span>  
  
- <span data-ttu-id="610bc-155">SET-Optionen (z. B. ANSI_NULLS, DATE_FORMAT, LANGUAGE und TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="610bc-155">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
- <span data-ttu-id="610bc-156">Sicherheitskontext (Benutzer/Anwendungsrolle)</span><span class="sxs-lookup"><span data-stu-id="610bc-156">Security context (user/application role)</span></span>  
  
- <span data-ttu-id="610bc-157">Datenbankkontext (aktuelle Datenbank)</span><span class="sxs-lookup"><span data-stu-id="610bc-157">Database context (current database)</span></span>  
  
- <span data-ttu-id="610bc-158">Ausführungszustandsvariablen (z. B. @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="610bc-158">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
- <span data-ttu-id="610bc-159">Temporäre Tabellen der obersten Ebene</span><span class="sxs-lookup"><span data-stu-id="610bc-159">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="610bc-160">Bei MARS ist einer Verbindung eine Standardausführungsumgebung zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="610bc-160">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="610bc-161">Jeder neue Batch, dessen Ausführung unter einer bestimmten Verbindung gestartet wird, erhält eine Kopie der Standardumgebung.</span><span class="sxs-lookup"><span data-stu-id="610bc-161">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="610bc-162">Bei Ausführung von Code in einem bestimmten Batch sind sämtliche an der Umgebung vorgenommenen Änderungen auf diesen speziellen Batch begrenzt.</span><span class="sxs-lookup"><span data-stu-id="610bc-162">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="610bc-163">Beim Abschluss der Ausführung werden die Ausführungseinstellungen in die Standardumgebung kopiert.</span><span class="sxs-lookup"><span data-stu-id="610bc-163">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="610bc-164">Bei einem einzelnen Batch, der mehrere Befehle enthält, die nacheinander in derselben Transaktion ausgeführt werden sollen, ist die Semantik die gleiche wie bei Verbindungen, die von früheren Clients oder Servern verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="610bc-164">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="610bc-165">Parallelausführung</span><span class="sxs-lookup"><span data-stu-id="610bc-165">Parallel Execution</span></span>  

 <span data-ttu-id="610bc-166">MARS ist nicht so konzipiert, dass alle Anforderungen für mehrere Verbindungen in einer Anwendung entfallen.</span><span class="sxs-lookup"><span data-stu-id="610bc-166">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="610bc-167">Wenn eine Anwendung eine tatsächliche parallele Ausführung von Befehlen auf einem Server benötigt, müssen mehrere Verbindungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="610bc-167">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="610bc-168">Ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="610bc-168">For example, consider the following scenario.</span></span> <span data-ttu-id="610bc-169">Es werden zwei Befehlsobjekte erstellt: eines zur Verarbeitung eines Resultsets und ein weiteres zur Aktualisierung von Daten. Beide nutzen eine gemeinsame Verbindung über MARS.</span><span class="sxs-lookup"><span data-stu-id="610bc-169">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="610bc-170">In diesem Szenario kann `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="610bc-170">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="610bc-171">erst erfolgreich ausgeführt werden, nachdem alle Ergebnisse des ersten Befehlsobjekts gelesen wurden. Daher wird eine entsprechende Ausnahme ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="610bc-171">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="610bc-172">Meldung: Der Transaktionskontext wird von einer anderen Sitzung verwendet.</span><span class="sxs-lookup"><span data-stu-id="610bc-172">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="610bc-173">Quelle: .NET SqlClient-Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="610bc-173">Source: .NET SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="610bc-174">Erwartet: (NULL)</span><span class="sxs-lookup"><span data-stu-id="610bc-174">Expected: (null)</span></span>  
  
 <span data-ttu-id="610bc-175">Empfangen: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="610bc-175">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="610bc-176">Es gibt zwei Optionen zum Umgang mit diesem Szenario:</span><span class="sxs-lookup"><span data-stu-id="610bc-176">There are three options for handling this scenario:</span></span>  
  
1. <span data-ttu-id="610bc-177">Starten Sie die Transaktion nach Erstellen des Readers so, dass sie nicht Teil der Transaktion ist.</span><span class="sxs-lookup"><span data-stu-id="610bc-177">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="610bc-178">Jede Aktualisierung wird dann eine eigene Transaktion.</span><span class="sxs-lookup"><span data-stu-id="610bc-178">Every update then becomes its own transaction.</span></span>  
  
2. <span data-ttu-id="610bc-179">Committen Sie alle Aufgaben nach Schließen des Readers.</span><span class="sxs-lookup"><span data-stu-id="610bc-179">Commit all work after the reader is closed.</span></span> <span data-ttu-id="610bc-180">Dies birgt das Potenzial für einen beträchtlichen Batch von Aktualisierungen.</span><span class="sxs-lookup"><span data-stu-id="610bc-180">This has the potential for a substantial batch of updates.</span></span>  
  
3. <span data-ttu-id="610bc-181">Verwenden Sie nicht MARS sondern für jedes Befehlsobjekt eine separate Verbindung, so wie Sie es vor MARS getan hätten.</span><span class="sxs-lookup"><span data-stu-id="610bc-181">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="610bc-182">Ermitteln der MARS-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="610bc-182">Detecting MARS Support</span></span>  

 <span data-ttu-id="610bc-183">Eine Anwendung kann auf MARS-Unterstützung prüfen, indem sie den Wert `SqlConnection.ServerVersion` liest.</span><span class="sxs-lookup"><span data-stu-id="610bc-183">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="610bc-184">Die Hauptnummer muss 9 für SQL Server 2005 und 10 für SQL Server 2008 lauten.</span><span class="sxs-lookup"><span data-stu-id="610bc-184">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610bc-185">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="610bc-185">See also</span></span>

- [<span data-ttu-id="610bc-186">Mehrere aktive Resultsets (MARS)</span><span class="sxs-lookup"><span data-stu-id="610bc-186">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="610bc-187">Übersicht über ADO.NET</span><span class="sxs-lookup"><span data-stu-id="610bc-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
