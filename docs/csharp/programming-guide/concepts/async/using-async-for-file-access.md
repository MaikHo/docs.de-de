---
title: Using Async for File Access (C#) (Verwenden von Async für Dateizugriff (C#))
description: Informationen zur Verwendung des Async-Features für den Zugriff auf Dateien in C# Sie können asynchrone Methoden aufrufen, ohne Rückrufe verwenden oder den Code methodenübergreifend aufteilen zu müssen.
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: eb67bd408fe37b99e6c5ffdc2550e8f95110d7eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925123"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="ae6e0-104">Using Async for File Access (C#) (Verwenden von Async für Dateizugriff (C#))</span><span class="sxs-lookup"><span data-stu-id="ae6e0-104">Using Async for File Access (C#)</span></span>
<span data-ttu-id="ae6e0-105">Sie können die Async-Funktion verwenden, um auf Dateien zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-105">You can use the async feature to access files.</span></span> <span data-ttu-id="ae6e0-106">Mithilfe der Async-Funktion können Sie asynchrone Methoden aufrufen, ohne Rückrufe zu verwenden oder den Code über mehrere Methoden oder Lambdaausdrücke teilen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="ae6e0-107">Um synchronen Code asynchron auszuführen, rufen Sie einfach eine asynchrone Methode anstelle einer synchronen Methode auf und fügen Sie dem Code einige Schlüsselwörter hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="ae6e0-108">Sie sollten die folgenden Gründe für das Hinzufügen von Asynchronie zu Dateizugriffsaufrufen in Betracht ziehen:</span><span class="sxs-lookup"><span data-stu-id="ae6e0-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="ae6e0-109">Durch Asynchronie kann die Reaktionsfähigkeit von UI-Anwendungen verbessert werden, da der UI-Thread, der den Vorgang startet, andere Aufgaben durchführen kann.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="ae6e0-110">Wenn der UI-Thread Code ausführt, der viel Zeit benötigt (z.B. mehr als 50 Millisekunden), kann die UI einfrieren, bis der E/A-Vorgang abgeschlossen ist und der UI-Thread wieder Tastatur- und Mauseingaben und andere Ereignisse verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="ae6e0-111">Asynchronie verbessert die Skalierbarkeit von ASP.NET und anderen serverbasierten Anwendungen, indem die Notwendigkeit von Threads reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="ae6e0-112">Wenn die Anwendung einen dedizierten Thread pro Antwort verwendet und tausend Anforderungen gleichzeitig behandelt werden, werden auch tausend Threads benötigt.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="ae6e0-113">Asynchrone Vorgänge benötigen während der Wartezeit oft keinen Thread.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-113">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="ae6e0-114">Sie verwenden den vorhandenen E/A-Abschlussthread kurz am Ende.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-114">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="ae6e0-115">Die Latenz von Dateizugriffsvorgängen kann unter bestimmten Umständen sehr niedrig sein, aber sie kann in Zukunft stark ansteigen.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="ae6e0-116">Eine Datei kann z.B. auf einen Server auf der anderen Seite der Erde verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-116">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="ae6e0-117">Der zusätzliche Mehraufwand durch Verwendung der Async-Funktion ist gering.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-117">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="ae6e0-118">Asynchrone Aufgaben können problemlos parallel ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-118">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="ae6e0-119">Ausführen der Beispiele</span><span class="sxs-lookup"><span data-stu-id="ae6e0-119">Running the Examples</span></span>  
 <span data-ttu-id="ae6e0-120">Sie können eine **WPF-Anwendung** oder **Windows Forms-Anwendung** erstellen und dann eine **Schaltfläche** hinzufügen, um die Beispiele in diesem Thema auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-120">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="ae6e0-121">Fügen Sie im `Click`-Ereignis der Schaltfläche einen Aufruf der ersten Methode jedes Beispiels hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-121">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="ae6e0-122">Beziehen Sie in den folgenden Beispielen die `using`-Anweisungen ein.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-122">In the following examples, include the following `using` directives.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="ae6e0-123">Verwenden der FileStream-Klasse</span><span class="sxs-lookup"><span data-stu-id="ae6e0-123">Use of the FileStream Class</span></span>  
 <span data-ttu-id="ae6e0-124">In den Beispielen in diesem Thema wird die <xref:System.IO.FileStream>-Klasse verwendet, die über eine Option verfügt, die asynchrone E/A-Vorgänge auf Betriebssystemebene auslöst.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-124">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="ae6e0-125">Mit dieser Option können Sie das Blockieren eines ThreadPool-Threads in vielen Fällen vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-125">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="ae6e0-126">Geben Sie zum Aktivieren dieser Option das Argument `useAsync=true` oder `options=FileOptions.Asynchronous` im Konstruktoraufruf an.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-126">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="ae6e0-127">Sie können diese Option nicht mit <xref:System.IO.StreamReader> und <xref:System.IO.StreamWriter> verwenden, wenn Sie sie direkt öffnen, indem Sie einen Dateipfad angeben.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-127">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="ae6e0-128">Allerdings können Sie diese Option verwenden, wenn Sie ihnen ein <xref:System.IO.Stream> geben, das die <xref:System.IO.FileStream>-Klasse geöffnet hat.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-128">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="ae6e0-129">Beachten Sie, dass asynchrone Aufrufe in Anwendungsbenutzeroberflächen schneller sind, selbst wenn ein ThreadPool-Thread blockiert wird, da der UI-Thread während der Wartezeit nicht blockiert ist.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-129">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="ae6e0-130">Schreiben von Text</span><span class="sxs-lookup"><span data-stu-id="ae6e0-130">Writing Text</span></span>  
 <span data-ttu-id="ae6e0-131">Im folgenden Beispiel wird Text in eine Datei geschrieben.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-131">The following example writes text to a file.</span></span> <span data-ttu-id="ae6e0-132">Bei jeder await-Anweisung wird die Methode sofort beendet.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-132">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="ae6e0-133">Wenn die Datei-E/A abgeschlossen ist, wird die Methode bei der Anweisung hinter der await-Anweisung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-133">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="ae6e0-134">Beachten Sie, dass sich der async-Modifizierer in der Definition der Methoden befindet, die die await-Anweisung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-134">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="ae6e0-135">Das ursprüngliche Beispiel verfügt über die Anweisung `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, bei der es sich um eine Kontraktion der folgenden zwei Anweisungen handelt:</span><span class="sxs-lookup"><span data-stu-id="ae6e0-135">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="ae6e0-136">Die erste Anweisung gibt eine Aufgabe zurück und löst die Dateiverarbeitung aus.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-136">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="ae6e0-137">Die zweite await-Anweisung führt dazu, dass die Methode sofort beendet wird und eine andere Aufgabe zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-137">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="ae6e0-138">Wenn die Dateiverarbeitung später abgeschlossen wird, wird die Ausführung bei der Anweisung fortgesetzt, die auf die „await“-Anweisung folgt.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-138">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="ae6e0-139">Weitere Informationen finden Sie unter [Ablaufsteuerung in asynchronen Programmen (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="ae6e0-139">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="ae6e0-140">Lesen von Text</span><span class="sxs-lookup"><span data-stu-id="ae6e0-140">Reading Text</span></span>  
 <span data-ttu-id="ae6e0-141">Im folgenden Beispiel wird Text aus einer Datei gelesen.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-141">The following example reads text from a file.</span></span> <span data-ttu-id="ae6e0-142">Der Text wird gepuffert und in diesem Fall in <xref:System.Text.StringBuilder> abgelegt.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="ae6e0-143">Anders als im vorherigen Beispiel generiert die Auswertung von „await“ einen Wert.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="ae6e0-144">Die Methode <xref:System.IO.Stream.ReadAsync%2A> gibt ein <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>-Element zurück, sodass die Auswertung von „await“ einen `Int32`-Wert (`numRead`) erzeugt, nachdem der Vorgang abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="ae6e0-145">Weitere Informationen finden Sie unter [Async Return Types (C#) (Asynchrone Rückgabetypen (C#))](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae6e0-145">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="ae6e0-146">Parallele Asynchrone E/A</span><span class="sxs-lookup"><span data-stu-id="ae6e0-146">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="ae6e0-147">Das folgende Beispiel zeigt die parallele Verarbeitung durch das Schreiben von zehn Textdateien.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-147">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="ae6e0-148">Die Methode <xref:System.IO.Stream.WriteAsync%2A> gibt für jede Datei eine Aufgabe zurück, die anschließend zu einer Liste von Aufgaben hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-148">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="ae6e0-149">Die `await Task.WhenAll(tasks);`-Anweisung beendet die Methode und wird innerhalb der Methode fortgesetzt, wenn die Dateiverarbeitung für alle Aufgaben abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-149">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="ae6e0-150">Im Beispiel werden alle <xref:System.IO.FileStream>-Instanzen in einem `finally`-Block geschlossen, nachdem die Aufgaben abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-150">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="ae6e0-151">Wenn jeder `FileStream` stattdessen in einer `using`-Anweisung erstellt wurde, kann `FileStream` verworfen werden, bevor die Aufgabe abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-151">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="ae6e0-152">Beachten Sie, dass sich eine Steigerung der Leistung fast ausschließlich aus der parallelen und nicht der asynchronen Verarbeitung ergibt.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-152">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="ae6e0-153">Die Vorteile der Asynchronie sind, dass sie nicht mehrere Threads und den Benutzeroberflächenthread bindet.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-153">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ae6e0-154">Bei Verwendung der Methoden <xref:System.IO.Stream.WriteAsync%2A> und <xref:System.IO.Stream.ReadAsync%2A> können Sie einen <xref:System.Threading.CancellationToken> angeben, mit dem Sie den Vorgang in der Mitte des Streams beenden können.</span><span class="sxs-lookup"><span data-stu-id="ae6e0-154">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="ae6e0-155">Weitere Informationen finden Sie unter [Fine-Tuning Your Async Application (C#) (Abstimmen der asynchronen Anwendung (C#))](./fine-tuning-your-async-application.md) und [Abbruch in verwalteten Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="ae6e0-155">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6e0-156">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ae6e0-156">See also</span></span>

- [<span data-ttu-id="ae6e0-157">Asynchrone Programmierung mit „async“ und „await“ (C#)</span><span class="sxs-lookup"><span data-stu-id="ae6e0-157">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="ae6e0-158">Asynchrone Rückgabetypen (C#)</span><span class="sxs-lookup"><span data-stu-id="ae6e0-158">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="ae6e0-159">Ablaufsteuerung in asynchronen Programmen (C#)</span><span class="sxs-lookup"><span data-stu-id="ae6e0-159">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
