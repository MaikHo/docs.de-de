---
title: Threading-Modell
description: Erfahren Sie mehr über Situationen, in denen Sie möglicherweise mehrere Threads in Ihrer Windows Presentation Foundation Anwendung benötigen. Single Thread-Lösungen werden bevorzugt.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 9b67b6ea2896e9e6fec57dee8d1013d54fab03fc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166387"
---
# <a name="threading-model"></a>Threading-Modell
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] soll Entwicklern bei Problemen mit Threading helfen. Folglich muss die Mehrzahl der [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Entwickler keine Schnittstelle schreiben, die mehr als einen Thread verwendet. Da Multithreadprogramme komplex und schwierig zu debuggen sind, sollten sie vermieden werden, wenn Singlethread-Lösungen vorhanden sind.

 Unabhängig davon, wie gut entworfen wurde, kann kein [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Framework für jede Art von Problem eine Single Thread-Lösung bereitstellen. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wird geschlossen, aber es gibt immer noch Situationen, in denen mehrere Threads die [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Reaktionsfähigkeit oder die Anwendungsleistung verbessern. In diesem Artikel werden zunächst einige Hintergrundinformationen angegeben, dann einige dieser Situationen beschrieben und am Ende einige Details auf niedriger Ebene besprochen.

> [!NOTE]
> In diesem Thema wird das Threading mithilfe der- <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> Methode für asynchrone Aufrufe erläutert. Sie können auch asynchrone Aufrufe durchführen, indem Sie die- <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Methode aufrufen, die einen- <xref:System.Action> <xref:System.Func%601> Parameter oder einen-Parameter annimmt.  Die- <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Methode gibt ein <xref:System.Windows.Threading.DispatcherOperation> oder zurück <xref:System.Windows.Threading.DispatcherOperation%601> , das über eine- <xref:System.Windows.Threading.DispatcherOperation.Task%2A> Eigenschaft verfügt. Sie können das `await` Schlüsselwort entweder mit dem <xref:System.Windows.Threading.DispatcherOperation> oder dem zugeordneten verwenden <xref:System.Threading.Tasks.Task> . Wenn Sie synchron auf das <xref:System.Threading.Tasks.Task> warten müssen, das von <xref:System.Windows.Threading.DispatcherOperation> oder <xref:System.Windows.Threading.DispatcherOperation%601> zurückgegeben wird, rufen Sie die <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>-Erweiterungsmethode auf.  Das Aufrufen von <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> führt zu einem Deadlock. Weitere Informationen zum <xref:System.Threading.Tasks.Task> Ausführen von asynchronen Vorgängen mithilfe von finden Sie Unteraufgaben Parallelität.  Die- <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Methode verfügt auch über über Ladungen, die einen <xref:System.Action> oder <xref:System.Func%601> als Parameter annehmen.  Mithilfe der-Methode können Sie <xref:System.Windows.Threading.Dispatcher.Invoke%2A> synchrone Aufrufe durchführen, indem Sie einen-Delegaten übergeben <xref:System.Action> <xref:System.Func%601> .

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>Übersicht und Verteiler
 Anwendungen beginnen in der Regel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mit zwei Threads: einer für die Behandlung von Rendering und einem weiteren für die Verwaltung von [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Der Renderingthread wird im Hintergrund ausgeblendet, während der [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread Eingaben empfängt, Ereignisse verarbeitet, den Bildschirm zeichnet und Anwendungscode ausführt. Die meisten Anwendungen verwenden einen einzelnen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread, aber in manchen Situationen ist es am besten, mehrere zu verwenden. Dies wird weiter unten mit einem Beispiel erläutert.

 Der [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread fügt Arbeitselemente in ein Objekt ein, das als bezeichnet wird <xref:System.Windows.Threading.Dispatcher> . Vom <xref:System.Windows.Threading.Dispatcher> werden Arbeitsaufgaben nach Priorität ausgewählt und jeweils vollständig ausgeführt.  Jeder [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread muss mindestens einen aufweisen <xref:System.Windows.Threading.Dispatcher> , und jeder <xref:System.Windows.Threading.Dispatcher> kann Arbeitsaufgaben in genau einem Thread ausführen.

 Der Trick, reaktionsfähige, benutzerfreundliche Anwendungen zu entwickeln, besteht darin, den Durchsatz zu maximieren, <xref:System.Windows.Threading.Dispatcher> indem die Arbeitselemente gering gehalten werden. Auf diese Weise werden Elemente in der Warteschlange, die auf die Verarbeitung warten, nie abgelaufen <xref:System.Windows.Threading.Dispatcher> . Jede spürbare Verzögerung zwischen Eingabe und Antwort kann für einen Benutzer frustrierend sein.

 Wie sollen also [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Anwendungen große Vorgänge verarbeiten? Was geschieht, wenn der Code eine aufwändige Berechnung beinhaltet oder eine Abfrage einer Datenbank auf einem Remoteserver ausführen muss? In der Regel besteht die Antwort darin, den großen Vorgang in einem separaten Thread zu behandeln, sodass der Thread nicht mehr in [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] der <xref:System.Windows.Threading.Dispatcher> Warteschlange steht. Wenn der große Vorgang fertiggestellt ist, kann er sein Ergebnis zur Anzeige an den Thread zurückmelden [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

 In der Vergangenheit ermöglicht Windows [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] den Zugriff auf Elemente nur durch den Thread, der Sie erstellt hat. Dies bedeutet, dass ein Hintergrundthread bei einer Aufgabe mit langer Laufzeit kein Textfeld aktualisieren kann, wenn er abgeschlossen ist. Windows führt dies aus, um die Integrität der Komponenten sicherzustellen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Ein Listenfeld könnte merkwürdig aussehen, wenn sein Inhalt während des Zeichnens von einem Hintergrundthread aktualisiert werden würde.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verfügt über einen integrierten gegenseitigen Ausschlussmechanismus, der diese Koordination erzwingt. Die meisten Klassen in werden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] von abgeleitet <xref:System.Windows.Threading.DispatcherObject> . Bei der Erstellung speichert ein einen <xref:System.Windows.Threading.DispatcherObject> Verweis auf den, der mit <xref:System.Windows.Threading.Dispatcher> dem aktuell laufenden Thread verknüpft ist. Tatsächlich verknüpft der den <xref:System.Windows.Threading.DispatcherObject> Thread, der ihn erstellt. Während der Programmausführung <xref:System.Windows.Threading.DispatcherObject> kann eine seine öffentliche Methode aufzurufen <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> . <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>überprüft den <xref:System.Windows.Threading.Dispatcher> , der dem aktuellen Thread zugeordnet ist, und vergleicht ihn mit dem <xref:System.Windows.Threading.Dispatcher> während der Konstruktion gespeicherten Verweis. Wenn Sie nicht identisch sind, wird von <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> eine Ausnahme ausgelöst. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>soll am Anfang jeder Methode aufgerufen werden, die zu einer gehört <xref:System.Windows.Threading.DispatcherObject> .

 Wenn nur ein Thread das ändern kann [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , wie interagieren Hintergrundthreads mit dem Benutzer? Ein Hintergrund Thread kann den [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread auffordern, einen Vorgang in seinem Auftrag auszuführen. Dies erfolgt durch das Registrieren eines Arbeits Elements beim <xref:System.Windows.Threading.Dispatcher> des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Threads. Die <xref:System.Windows.Threading.Dispatcher> -Klasse stellt zwei Methoden zum Registrieren von Arbeits Elementen bereit: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> und <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> . Beide Methoden planen einen Delegaten für die Ausführung ein. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>ist ein synchroner Aufruf – das heißt, er wird erst zurückgegeben, wenn der [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread die Ausführung des Delegaten tatsächlich abgeschlossen hat. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>ist asynchron und wird sofort zurückgegeben.

 <xref:System.Windows.Threading.Dispatcher>Ordnet die Elemente in der Warteschlange nach Priorität an. Es gibt zehn Ebenen, die angegeben werden können, wenn ein Element zur <xref:System.Windows.Threading.Dispatcher> Warteschlange hinzugefügt wird. Diese Prioritäten werden in der- <xref:System.Windows.Threading.DispatcherPriority> Enumeration beibehalten. Ausführliche Informationen zu <xref:System.Windows.Threading.DispatcherPriority> Ebenen finden Sie in der Windows SDK-Dokumentation.

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>Threads in Aktion: Beispiele

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Eine Singlethread-Anwendung mit einer Berechnung mit langer Laufzeit
 Die meisten grafischen Benutzeroberflächen (GUIs) verbringen einen großen Teil ihrer Zeit im Leerlauf und warten auf Ereignisse, die als Reaktion auf Benutzerinteraktionen generiert werden. Bei sorgfältiger Programmierung kann diese Leerlaufzeit konstruktiv genutzt werden, ohne dass sich dies auf die Reaktionsfähigkeit von auswirkt [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Das [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Threading Modell lässt nicht zu, dass Eingaben einen Vorgang im Thread unterbrechen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Dies bedeutet, dass Sie in regelmäßigen Abständen zu den zurückkehren müssen <xref:System.Windows.Threading.Dispatcher> , um ausstehende Eingabeereignisse zu verarbeiten, bevor Sie veraltet sind.

 Betrachten Sie das folgende Beispiel:

 ![Screenshot, der das Threading von Primzahlen zeigt.](./media/threading-model/threading-prime-numbers.png)

 Diese einfache Anwendung zählt ab drei aufwärts und sucht dabei nach Primzahlen. Wenn der Benutzer auf die Schaltfläche " **Start** " klickt, beginnt die Suche. Wenn das Programm eine Primzahl findet, wird die Benutzeroberfläche mit dieser Entdeckung aktualisiert. Der Benutzer kann die Suche zu jedem Zeitpunkt beenden.

 Obwohl es sich um eine einfache Anwendung handelt, könnte die Suche nach Primzahlen endlos fortgesetzt werden, was einige Probleme bereitet.  Wenn wir die gesamte Suche innerhalb des Click-Ereignis Handlers der Schaltfläche behandelt haben, würden wir dem Thread nie die Möglichkeit einräumen, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] andere Ereignisse zu verarbeiten. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Kann nicht auf Eingabe-oder Verarbeitungs Nachrichten reagieren. Sie würde nie neu zeichnen und nie auf Mausklicks auf die Schaltflächen reagieren.

 Wir könnten die Suche nach Primzahlen in einem separaten Thread ausführen, aber dann hätten wir Synchronisierungsprobleme. Mit einem Singlethread-Ansatz können wir die Bezeichnung, die die größte gefundene Primzahl auflistet, direkt aktualisieren.

 Wenn wir die Berechnungs Aufgabe in verwaltbare Blöcke aufteilen, können wir in regelmäßigen Abständen zu den <xref:System.Windows.Threading.Dispatcher> -und-Prozess Ereignissen zurückkehren. Wir können [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] die Möglichkeit zum Neuzeichnen und Verarbeiten von Eingaben bieten.

 Die beste Möglichkeit, die Verarbeitungszeit Zwischenberechnungen und Ereignis Behandlung aufzuteilen, besteht darin, die Berechnung über die zu verwalten <xref:System.Windows.Threading.Dispatcher> . Mithilfe der- <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> Methode können wir Primzahlen Überprüfungen in derselben Warteschlange planen, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aus der Ereignisse gezeichnet werden. In unserem Beispiel planen wir nur eine einzige Primzahlüberprüfung zu einem Zeitpunkt ein. Nach Abschluss der Primzahlüberprüfung planen wir sofort die nächste Überprüfung ein. Diese Überprüfung wird nur fortgesetzt, nachdem ausstehende [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Ereignisse behandelt wurden.

 ![Screenshot, der die Verteiler-Warteschlange anzeigt](./media/threading-model/threading-dispatcher-queue.png)

 Microsoft Word führt die Rechtschreibprüfung mit diesem Mechanismus durch. Die Rechtschreibprüfung erfolgt im Hintergrund mithilfe der Leerlaufzeit des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Threads. Sehen wir uns den Code an.

 Das folgende Beispiel zeigt die XAML, die die Benutzeroberfläche erstellt.

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 Im folgenden Beispiel wird das CodeBehind gezeigt.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 Das folgende Beispiel zeigt den Ereignishandler für das <xref:System.Windows.Controls.Button> .

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 Neben dem Aktualisieren des Texts auf dem <xref:System.Windows.Controls.Button> ist dieser Handler für die Planung der ersten Primzahlen Prüfung zuständig, indem der Warteschlange ein Delegat hinzugefügt wird <xref:System.Windows.Threading.Dispatcher> . Nachdem der Ereignishandler seine Arbeit abgeschlossen hat, wählt der <xref:System.Windows.Threading.Dispatcher> diesen Delegaten für die Ausführung aus.

 Wie bereits erwähnt, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> ist der Member, der <xref:System.Windows.Threading.Dispatcher> zum Planen eines Delegaten für die Ausführung verwendet wird. In diesem Fall wählen wir die <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> Priorität aus. Der <xref:System.Windows.Threading.Dispatcher> führt diesen Delegaten nur aus, wenn keine wichtigen Ereignisse zu verarbeiten sind. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-Reaktionsfähigkeit ist wichtiger als die Zahlenüberprüfung. Wir übergeben auch einen neuen Delegaten, der die Zahlenüberprüfungsroutine darstellt.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 Diese Methode überprüft, ob die nächste ungerade Zahl eine Primzahl ist. Wenn es sich um eine Primzahl handelt, aktualisiert die Methode das direkt, um die Ermittlung `bigPrime` <xref:System.Windows.Controls.TextBlock> widerzuspiegeln. Dies ist möglich, da die Berechnung im selben Thread ausgeführt wird, der für die Erstellung der Komponente verwendet wurde. Hätten wir beschlossen, einen separaten Thread für die Berechnung zu verwenden, müssten wir einen komplizierteren Synchronisierungs Mechanismus verwenden und das Update im Thread ausführen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Wir werden diese Situation im Folgenden zeigen.

 Den gesamten Quellcode für dieses Beispiel finden Sie unter Beispiel für [Single Thread-Anwendung mit langer Ausführungszeit](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication) .

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Behandeln eines blockierenden Vorgangs mit einem Hintergrundthread
 Die Behandlung von blockierenden Vorgängen in einer grafischen Anwendung kann schwierig sein. Wir wollen keine blockierenden Methoden von Ereignishandlern aufrufen, da die Anwendung sonst scheinbar einfriert. Wir können einen separaten Thread verwenden, um diese Vorgänge zu verarbeiten, aber wenn wir fertig sind, müssen wir mit dem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread synchronisieren, da wir die GUI nicht direkt von unserem Arbeits Thread aus ändern können. Wir können <xref:System.Windows.Threading.Dispatcher.Invoke%2A> oder verwenden <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> , um Delegaten in den <xref:System.Windows.Threading.Dispatcher> des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Threads einzufügen. Schließlich werden diese Delegaten mit der Berechtigung zum Ändern von [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementen ausgeführt.

 In diesem Beispiel simulieren wir einen Remoteprozeduraufruf, der eine Wettervorhersage abruft. Wir verwenden zum Ausführen dieses Aufrufes einen separaten Arbeits Thread, und wir planen eine Aktualisierungs Methode im <xref:System.Windows.Threading.Dispatcher> des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Threads, wenn wir fertig sind.

 ![Screenshot, in dem die Wetter Benutzeroberfläche angezeigt wird.](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 Im Folgenden sind einige der Details aufgeführt, die beachtet werden sollten.

- Erstellen des Schaltflächenhandlers

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 Wenn auf die Schaltfläche geklickt wird, wird die Uhr-Zeichnung angezeigt, und wir beginnen mit der Animation. Die Schaltfläche wird deaktiviert. Wir rufen die `FetchWeatherFromServer` -Methode in einem neuen Thread auf und geben dann zurück, sodass <xref:System.Windows.Threading.Dispatcher> Ereignisse verarbeitet werden können, während wir auf die Wettervorhersage warten.

- Abrufen der Wettervorhersage

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 Aus Gründen der Einfachheit verwenden wir in diesem Beispiel keinen Netzwerk-Code. Stattdessen simulieren wir die Verzögerung des Netzwerkzugriffs, indem wir den neuen Thread für vier Sekunden in den Ruhezustand versetzen. In diesem Zeitraum wird der ursprüngliche [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread weiterhin ausgeführt und antwortet auf Ereignisse. Um dies zu zeigen, führen wir eine Animation weiterhin aus, und die Schaltflächen „Minimieren“ und „Maximieren“ funktionieren ebenfalls weiterhin.

 Wenn die Verzögerung abgeschlossen ist und wir nach dem Zufallsprinzip unsere Wettervorhersage ausgewählt haben, ist es an der Zeit, an den Thread zurückzukehren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Dies geschieht durch Planen eines `UpdateUserInterface` [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Aufrufes im Thread mithilfe der des Threads <xref:System.Windows.Threading.Dispatcher> . Wir übergeben eine Zeichenfolge, die das Wetter beschreibt, an diesen eingeplanten Methodenaufruf.

- Aktualisieren der[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 Wenn der <xref:System.Windows.Threading.Dispatcher> im [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread Zeit hat, führt er den geplanten Aufruf von aus `UpdateUserInterface` . Diese Methode hält die Uhr-Animation an und wählt ein Bild aus, um das Wetter zu beschreiben. Sie zeigt dieses Bild an und stellt die Schaltfläche „fetch forecast“ (Wettervorhersage abrufen) wieder her.

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>Mehrere Fenster, mehrere Threads
 Einige [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Anwendungen erfordern mehrere Fenster der obersten Ebene. Es ist durchaus akzeptabel, dass ein Thread/eine <xref:System.Windows.Threading.Dispatcher> Kombination mehrere Fenster verwaltet, aber manchmal haben mehrere Threads einen besseren Job. Dies trifft besonders zu, wenn die Möglichkeit besteht, dass eines der Fenster den Thread für sich beansprucht.

 Windows-Explorer funktioniert auf diese Weise. Jedes neue Explorer-Fenster gehört zum ursprünglichen Prozess, wird jedoch unter der Kontrolle eines unabhängigen Threads erstellt.

 Mithilfe eines- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> Steuer Elements können wir Webseiten anzeigen. Wir können problemlos einen einfachen Ersatz für Internet Explorer erstellen. Wir beginnen mit einer wichtigen Funktion, und zwar der Möglichkeit, ein neues Explorerfenster zu öffnen. Wenn der Benutzer auf die Schaltfläche „Neues Fenster“ klickt, starten wir eine Kopie des Fensters in einem separaten Thread. Auf diese Weise sperren lange andauernde oder blockierende Vorgänge in einem der Fenster nicht alle anderen Fenster.

 In Wirklichkeit verfügt das Webbrowser-Modell über ein eigenes kompliziertes Threadingmodell. Wir haben uns dafür entschieden, da die meisten Leser damit vertraut sein sollten.

 Im folgenden Beispiel wird der Code angezeigt.

 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]

 Die folgenden Threadingsegmente dieses Codes sind für uns in diesem Kontext am interessantesten:

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]

 Diese Methode wird aufgerufen, wenn die Schaltfläche „Neues Fenster“ angeklickt wird. Sie erstellt einen neuen Thread und startet diesen asynchron.

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]

 Diese Methode ist der Ausgangspunkt für den neuen Thread. Wir erstellen ein neues Fenster unter der Kontrolle dieses Threads. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]erstellt automatisch einen neuen <xref:System.Windows.Threading.Dispatcher> , um den neuen Thread zu verwalten. Wir müssen lediglich den starten, um das Fenster funktionsfähig zu machen <xref:System.Windows.Threading.Dispatcher> .

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>Technische Details und Stolpersteine

### <a name="writing-components-using-threading"></a>Schreiben von Komponenten mithilfe von Threading
 Das Entwicklerhandbuch für Microsoft .NET Framework beschreibt ein Muster für die Bereitstellung von asynchronem Verhalten durch eine Komponente für die Clients (siehe [Übersicht über das ereignisbasierte asynchrone Muster](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Nehmen wir beispielsweise an, dass die `FetchWeatherFromServer` Methode in eine wiederverwendbare, nicht grafische Komponente integriert werden soll. Nach dem Standard-Microsoft .NET Framework-Muster würde dies in etwa wie folgt aussehen.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync` würde eine der zuvor beschriebenen Techniken wie z.B. das Erstellen eines Hintergrundthreads verwenden, um die Arbeit asynchron auszuführen und den aufrufenden Thread nicht zu blockieren.

 Einer der wichtigsten Teile dieses Musters ist das Aufrufen der *MethodName* - `Completed` Methode für denselben Thread, der die *MethodName* -Methode aufgerufen hat `Async` , um mit zu beginnen. Dies können Sie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recht einfach tun, indem Sie – speichern, <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> aber die nicht grafische Komponente kann nur in Anwendungen verwendet werden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , nicht in Windows Forms-oder ASP.NET-Programmen.

 Die- <xref:System.Windows.Threading.DispatcherSynchronizationContext> Klasse erfüllt diese Anforderung – stellen Sie sich diese als vereinfachte Version von <xref:System.Windows.Threading.Dispatcher> vor, die auch mit anderen Frameworks funktioniert [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>Geschachtelte Verteilung
 Manchmal ist es nicht möglich, den Thread vollständig zu sperren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Betrachten wir die- <xref:System.Windows.MessageBox.Show%2A> Methode der- <xref:System.Windows.MessageBox> Klasse. <xref:System.Windows.MessageBox.Show%2A>gibt erst zurück, wenn der Benutzer auf die Schaltfläche OK klickt. Es wird jedoch ein Fenster erstellt, das über eine Meldungsschleife verfügen muss, um interaktiv zu sein. Während wir warten, bis der Benutzer auf „OK“ klickt, reagiert das ursprüngliche Anwendungsfenster nicht auf Benutzereingaben. Es verarbeitet jedoch weiterhin Paint-Meldungen. Das ursprüngliche Fenster zeichnet sich selbst neu, wenn es verdeckt war und dann wieder angezeigt wird.

 ![Screenshot, der eine MessageBox mit der Schaltfläche "OK" anzeigt](./media/threading-model/threading-message-loop.png)

 Ein Thread muss für das Meldungsfenster zuständig sein. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] könnte einen neuen Thread nur für das Meldungsfenster erstellen, aber dieser Thread wäre nicht in der Lage, die deaktivierten Elemente im ursprünglichen Fenster zu zeichnen (beachten Sie den bereits erwähnten gegenseitigen Ausschluss). Stattdessen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verwendet ein System eigenes Nachrichten Verarbeitungssystem. Die <xref:System.Windows.Threading.Dispatcher> -Klasse enthält eine spezielle Methode namens <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> , die den aktuellen Ausführungs Punkt einer Anwendung speichert und dann eine neue Nachrichten Schleife startet. Wenn die schsted Message-Schleife abgeschlossen ist, wird die Ausführung nach dem ursprünglichen-Befehl fortgesetzt <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> .

 In diesem Fall <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> behält den Programmkontext beim-Aufrufvorgang bei <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> und startet eine neue Nachrichten Schleife, um das Hintergrund Fenster neu zu zeichnen und Eingaben in das Meldungs Feld Fenster zu behandeln. Wenn der Benutzer auf OK klickt und das Popup Fenster löscht, wird die schsted-Schleife beendet, und die Steuerung wird nach dem Aufrufen von fortgesetzt <xref:System.Windows.MessageBox.Show%2A> .

### <a name="stale-routed-events"></a>Veraltete Routingereignisse
 Das Routing Ereignis System in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] benachrichtigt gesamte Strukturen, wenn Ereignisse ausgelöst werden.

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 Wenn die linke Maustaste über der Ellipse gedrückt wird, `handler2` wird ausgeführt. Nachdem `handler2` abgeschlossen wurde, wird das-Ereignis an das-Objekt weitergegeben <xref:System.Windows.Controls.Canvas> , das `handler1` von zur Verarbeitung verwendet wird. Dies geschieht nur, wenn `handler2` das Ereignis Objekt nicht explizit als behandelt kennzeichnet.

 Es ist möglich, dass die `handler2` Verarbeitung dieses Ereignisses sehr viel Zeit in Anspruch nimmt. `handler2`verwendet möglicherweise <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> , um eine schinstanzschleife zu starten, die für Stunden nicht zurückgibt. Wenn `handler2` das Ereignis nicht als behandelt markiert, wenn diese Nachrichten Schleife beendet ist, wird das Ereignis in der Struktur nach oben weitergegeben, obwohl es sehr alt ist.

### <a name="reentrancy-and-locking"></a>Wiedereintritt und Sperrung
 Der Sperrmechanismus des Common Language Runtime (CLR) verhält sich nicht genau so, wie man sich vorstellen könnte. ein Thread kann davon ausgehen, dass der Vorgang vollständig beendet wird, wenn eine Sperre angefordert wird. In Wirklichkeit empfängt und verarbeitet der Thread weiterhin Meldungen mit hoher Priorität. Dadurch können Deadlocks vermieden und Schnittstellen minimal reaktionsfähig gemacht werden, aber dadurch können auch schwer erkennbare Fehler entstehen.  Der Großteil der Fälle, in denen Sie nichts wissen müssen, aber in seltenen Fällen (in der Regel mit Win32-Fenster Meldungen oder COM-STA-Komponenten) ist dies zu wissen.

 Die meisten Schnittstellen werden nicht mit Thread Sicherheit erstellt, da Entwickler unter der Annahme arbeiten, dass [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nie von mehr als einem Thread darauf zugegriffen wird. In diesem Fall kann es vorkommen, dass ein einzelner Thread Änderungen an der Umgebung zu unerwarteten Zeiten durchführt, wodurch die negativen Auswirkungen, die der <xref:System.Windows.Threading.DispatcherObject> gegenseitige Ausschlussmechanismus lösen soll, entstehen. Betrachten Sie den folgenden Pseudocode:

 ![Das Diagramm, das das wieder eintreten des Threading anzeigt.](./media/threading-model/threading-reentrancy.png "Threadingreentrancy")

 In den meisten Fällen ist dies die richtige Sache, aber es gibt Zeiten, in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denen eine solche unerwartete Wiederaufnahme tatsächlich Probleme verursachen kann. Daher wird zu bestimmten Zeitpunkten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aufgerufen <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A> , wodurch die Lock-Anweisung für diesen Thread so geändert wird, dass die [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Wiedereintritts freie Sperre anstelle der üblichen CLR-Sperre verwendet wird.

 Warum hat das CLR-Team dieses Verhalten gewählt? Dies hatte mit COM-STA-Objekten und dem Finalizerthread zu tun. Wenn für ein Objekt eine Garbage Collection durchgeführt wird, wird die zugehörige- `Finalize` Methode auf dem dedizierten Finalizerthread ausgeführt, nicht auf dem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread. Und darin liegt das Problem, da ein COM-STA-Objekt, das auf dem Thread erstellt wurde, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nur im Thread verworfen werden kann [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Die CLR übernimmt das Äquivalent eines <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (in diesem Fall mit Win32's `SendMessage` ). Wenn der [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Thread jedoch ausgelastet ist, wird der Finalizerthread angehalten, und das COM-STA-Objekt kann nicht verworfen werden. dadurch entsteht ein schwerwiegender Speicherplatz. Das CLR-Team hat also den harten Aufruf getroffen, damit Sperren so funktionieren, wie Sie funktionieren.

 Die Aufgabe für besteht darin, unerwartete Eintritts Übereinstimmung [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zu vermeiden, ohne den Speicherplatz zu wiederholen. aus diesem Grund blockieren wir den erneuten eintreten nicht überall.

## <a name="see-also"></a>Weitere Informationen

- [Single-Threaded Application with Long-Running Calculation Sample (Singlethread-Anwendung mit Beispiel für Berechnung mit langer Laufzeit)](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)
