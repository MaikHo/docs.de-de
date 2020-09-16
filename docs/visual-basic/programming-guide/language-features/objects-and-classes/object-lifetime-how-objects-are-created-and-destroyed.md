---
title: 'Objektlebensdauer: Erstellen und Zerstören von Objekten'
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: a32a5d075b5b1d02632c80216e7c2c12920bf4a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544140"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Objektlebensdauer: Erstellen und Zerstören von Objekten (Visual Basic)

Erstellt mit dem `New`-Schlüsselwort eine Instanz einer Klasse, ein Objekt. Initialisierungsaufgaben müssen häufig für neue Objekte ausgeführt werden, bevor sie verwendet werden. Gebräuchliche Initialisierungsaufgaben umfassen das Öffnen von Dateien, Verbinden mit Datenbanken und das Lesen von Werten von Registrierungsschlüsseln. Visual Basic steuert die Initialisierung neuer Objekte mithilfe von Prozeduren, die als *Konstruktoren* bezeichnet werden (spezielle Methoden, die die Kontrolle über die Initialisierung ermöglichen).

Nachdem ein Objekt den Gültigkeitsbereich verlässt, wird es von der common Language Runtime (CLR) freigegeben. Visual Basic steuert die Freigabe von Systemressourcen mit Prozeduren, die als *desystemdektoren*bezeichnet Konstruktoren und Destruktoren unterstützen gemeinsam die Erstellung stabiler und vorhersehbarer Klassenbibliotheken.

## <a name="using-constructors-and-destructors"></a>Verwenden von Konstruktoren und Destruktoren

Konstruktoren und Destruktoren steuern die Erstellung und Zerstörung von Objekten. Die `Sub New` -und- `Sub Finalize` Prozeduren in Visual Basic Objekte initialisieren und zerstören; Sie ersetzen die `Class_Initialize` -und-Methoden, die `Class_Terminate` in Visual Basic 6,0 und früheren Versionen verwendet werden.

### <a name="sub-new"></a>Sub New

Der `Sub New`-Konstruktor kann nur einmal während der Erstellung der Klasse ausgeführt werden. Es kann nicht als explizit an einer beliebigen Stelle aufgerufen werden, außer in der ersten Codezeile eines anderen Konstruktors von derselben Klasse oder von einer abgeleiteten Klasse. Weiterhin wird der Code in der `Sub New`-Methode immer vor jedem anderen Code in einer Klasse ausgeführt. Visual Basic implizit einen `Sub New` Konstruktor zur Laufzeit erstellt, wenn Sie nicht explizit eine `Sub New` Prozedur für eine Klasse definieren.

Um einen Konstruktor für eine Klasse zu erstellen, erstellen Sie eine Prozedur mit dem Namen `Sub New` an einer beliebigen Stelle in der Klassendefinition. Zum Erstellen eines parametrisierten Konstruktors legen Sie die Namen und Datentypen der Argumente von `Sub New` so fest, wie Sie die Argumente für eine beliebige andere Prozedur angeben würden, wie im folgenden Code:

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Konstruktoren sind häufig überladen, wie im folgenden Code:

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Wenn Sie eine von einer anderen Klasse abgeleitete Klasse definieren, muss die erste Zeile eines Konstruktors ein Aufruf an den Konstruktor der Basisklasse sein, es sei denn die Basisklasse verfügt über einen zugreifbaren Konstruktor, der keine Parameter annimmt. Ein Aufruf der Basisklasse mit dem oben stehenden Konstruktor wäre zum Beispiel `MyBase.New(s)`. Andernfalls `MyBase.New` ist optional, und die Visual Basic Runtime ruft Sie implizit auf.

Nachdem Sie den Code zum Aufrufen des Konstruktors des übergeordneten Objekts geschrieben haben, können Sie einen beliebigen zusätzlichen Initialisierungscode dem `Sub New`-Verfahren hinzufügen. `Sub New` kann Argumente annehmen, wenn Sie als parametrisierter Konstruktor aufgerufen wird. Diese Parameter werden von der den Konstruktor aufrufenden Prozedur übergeben, zum Beispiel `Dim AnObject As New ThisClass(X)`.

### <a name="sub-finalize"></a>Sub Finalize

Vor der Freigabe von Objekten ruft die CLR automatisch die `Finalize`-Methode für das Objekt auf, das ein `Sub Finalize`-Verfahren definiert Die `Finalize`-Methode kann Code enthalten, der direkt vor der Zerstörung eines Objekts ausgeführt werden muss, z. B. Code zum Schließen von Dateien und Speichern von Zustandsinformationen. Es gibt leichte Leistungseinbußen für die Ausführung von `Sub Finalize`, sodass Sie eine `Sub Finalize`-Methode nur definieren sollten, wenn Sie Objekte explizit freigeben müssen.

> [!NOTE]
> Der Garbage Collector in der CLR kann nicht *verwaltete Objekte*, Objekte, die das Betriebssystem direkt außerhalb der CLR-Umgebung ausführt, nicht freigeben (und kann nicht). Dies liegt daran, dass unterschiedliche nicht verwaltete Objekte auf verschiedene Arten freigegeben werden müssen. Diese Informationen ist nicht direkt dem nicht verwalteten Objekt zugeordnet; Sie muss in der Dokumentation für das Objekt vorhanden sein. Eine Klasse, die nicht verwaltete Objekte verwendet, muss diese in ihrer `Finalize`-Methode freigeben.

Der `Finalize`-Destruktor ist eine geschützte Methode, die nur über die zugehörige Klasse oder über abgeleitete Klassen aufgerufen werden kann. Das System ruft `Finalize` automatisch auf, wenn ein Objekt zerstört wird, daher sollten Sie `Finalize` nicht explizit von außerhalb einer `Finalize`-Implementierung einer abgeleiteten Klasse aufrufen müssen.

Im Gegensatz zu `Class_Terminate`, das ausgeführt wird, sobald ein Objekt auf nichts festgelegt wurde, gibt es in der Regel eine Verzögerung zwischen dem Zeitpunkt, an dem ein Objekt seinen Gültigkeitsbereich verliert und wenn Visual Basic den `Finalize`-Destruktor aufruft. Visual Basic .NET ermöglicht eine zweite Art von Dekonstruktor, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , der jederzeit explizit aufgerufen werden kann, um Ressourcen sofort freizugeben.

> [!NOTE]
> Eine `Finalize`-Destruktor sollte keine Ausnahmen auslösen, da die Anwendung sie nicht behandeln kann und sie das Beenden der Anwendung verursachen können.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Wie Neue und Finalize-Methoden in einer Klassenhierarchie arbeiten

Wenn eine Instanz einer Klasse erstellt wird, versucht die common Language Runtime (CLR), eine Prozedur mit dem Namen `New` auszuführen, wenn es in diesem Objekt vorhanden ist. `New` ist eine Art von Prozedur `constructor` , die als bezeichnet wird und zum Initialisieren neuer Objekte verwendet wird, bevor ein anderer Code in einem-Objekt ausgeführt wird. Ein `New`-Konstruktor kann verwendet werden, um Dateien zu öffnen, Verbindungen mit Datenbanken herzustellen, Variablen zu initialisieren und sich um andere Aufgaben zu kümmern, die ausgeführt werden, bevor ein Objekt verwendet werden kann.

Wenn eine Instanz einer abgeleiteten Klasse erstellt wird, wird der `Sub New`-Konstruktor der Basisklasse zuerst ausgeführt, gefolgt von Konstruktoren in abgeleiteten Klassen. Dies geschieht, da die erste Codezeile in einem `Sub New`-Konstruktor die Syntax `MyBase.New()` verwendet, um den Konstruktor der Klasse direkt über sich selbst in der Klassenhierarchie aufzurufen. Der `Sub New`-Konstruktor wird dann für jede Klasse in der Klassenhierarchie aufgerufen, bis der Konstruktor für die Basisklasse erreicht wird. An dieser Stelle wird der Code im Konstruktor für die Basisklasse ausgeführt, gefolgt vom Code in jedem Konstruktor in allen abgeleiteten Klassen und der Code in den meisten abgeleiteten Klassen wird als letztes ausgeführt.

![Screenshot, der klassenhierarchienkonstruktoren und Vererbung zeigt](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Wenn ein Objekt nicht mehr benötigt wird, ruft die CLR die <xref:System.Object.Finalize%2A>-Methode für dieses Objekt auf, bevor der Speicher freigegeben wird. Die <xref:System.Object.Finalize%2A> -Methode wird `destructor` genannt, weil es Bereinigungsaufgaben führt, z. B. Speichern von Zustandsinformationen, Schließen von Dateien und Verbindungen mit Datenbanken sowie andere Aufgaben, die vor der Freigabe eines Objekts ausgeführt werden müssen.

![Screenshot, der den Finalize-methodendekonstruktor anzeigt.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>IDisposable-Schnittstelle

Klasseninstanzen steuern oft nicht von der CLR verwaltete Ressourcen, z. B. Windows-Handles und Datenbankverbindungen. Diese Ressourcen müssen in der `Finalize`-Methode der Klasse beseitigt werden, sodass sie freigegeben werden, wenn das Objekt vom Garbage Collector zerstört wird. Der Garbage Collector zerstört Objekte jedoch nur, wenn die CLR mehr freien Arbeitsspeicher erfordert. Dies bedeutet, dass die Ressourcen erst freigegeben werdn, nachdem das Objekt längst den Gültigkeitsbereich verlassen hat.

Zur Ergänzung der Garbagecollection können die Klassen einen Mechanismus für die aktive Verwaltung von Systemressourcen bereitstellen, wenn sie die <xref:System.IDisposable>-Schnittstelle implementieren. <xref:System.IDisposable> verfügt über eine Methode, <xref:System.IDisposable.Dispose%2A> , die von Clients aufgerufen werden soll, wenn die Verwendung eines-Objekts beendet wird. Sie können die <xref:System.IDisposable.Dispose%2A>-Methode verwenden, um Ressourcen sofort freizugeben und Aufgaben wie das Schließen von Dateien und Datenbankverbindungen durchzuführen. Im Gegensatz zum `Finalize`-Destruktor, wird die <xref:System.IDisposable.Dispose%2A>-Methode nicht automatisch aufgerufen. Clients einer Klasse müssen explizit <xref:System.IDisposable.Dispose%2A> aufrufen, wenn Ressourcen sofort freigegeben werden sollen.

### <a name="implementing-idisposable"></a>Implementieren von IDisposable

Eine Klasse, die die <xref:System.IDisposable>-Schnittstelle implementiert, sollte diese Codeabschnitte enthalten:

- Ein Feld, um den Überblick zu behalten, ob das Objekt entsorgt wurde:

  ```vb
  Protected disposed As Boolean = False
  ```

- Eine Überladung von der <xref:System.IDisposable.Dispose%2A>, die die Ressourcen der Klasse freigibt. Diese Methode sollte durch die <xref:System.IDisposable.Dispose%2A> und `Finalize`-Methoden der Basisklasse aufgerufen werden:

  ```vb
  Protected Overridable Sub Dispose(ByVal disposing As Boolean)
      If Not Me.disposed Then
          If disposing Then
              ' Insert code to free managed resources.
          End If
          ' Insert code to free unmanaged resources.
      End If
      Me.disposed = True
  End Sub
  ```

- Eine Implementierung von <xref:System.IDisposable.Dispose%2A>, die nur den folgenden Code enthält:

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- Eine Überschreibung der `Finalize`-Methode, die nur folgenden Code enthält:

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>Ableiten von einer Klasse, die IDisposable implementiert

Eine Klasse, die von einer Basisklasse abgeleitet wird, die die <xref:System.IDisposable>-Schnittstelle implementiert, muss keine Basismethoden überschreiben, es sei denn, sie verwendet zusätzliche Ressourcen, die freigegeben werden müssen. In diesem Fall sollte die abgeleitete Klasse die `Dispose(disposing)`-Methode der Basisklasse überschreiben, um die Ressourcen der abgeleiteten Klasse freizugeben. Diese Überschreibung muss die `Dispose(disposing)`-Methode der Basisklasse aufrufen.

```vb
Protected Overrides Sub Dispose(ByVal disposing As Boolean)
    If Not Me.disposed Then
        If disposing Then
            ' Insert code to free managed resources.
        End If
        ' Insert code to free unmanaged resources.
    End If
    MyBase.Dispose(disposing)
End Sub
```

Eine abgeleitete Klasse darf nicht die <xref:System.IDisposable.Dispose%2A>- und `Finalize`-Methode der Basisklasse überschreiben. Wenn diese Methoden aus einer Instanz der abgeleiteten Klasse aufgerufen werden, ruft die Basisklassenimplementierung dieser Methoden die Überschreibung der `Dispose(disposing)`-Methode auf.

## <a name="garbage-collection-and-the-finalize-destructor"></a>Garbagecollection und der Finalize-Destruktor

Der .NET Framework verwendet das *Garbage Collection* System der Referenz Ablauf Verfolgung, um nicht verwendete Ressourcen regelmäßig freizugeben. In Visual Basic 6,0 und früheren Versionen wurde ein anderes System namens *Verweis Zählung* verwendet, um Ressourcen zu verwalten. Obwohl beide Systeme dieselbe Funktion automatisch ausführen, gibt es einige wichtige Unterschiede.

Die CLR zerstört Objekte in regelmäßigen Abständen, wenn das System feststellt, dass diese Objekte nicht mehr benötigt werden. Objekte werden schneller freigegeben, wenn die Systemressourcen knapp und ansonsten seltener sind. Die Verzögerung zwischen dem Zeitpunkt, an dem ein Objekt seinen Gültigkeitsbereich verliert, und der Freigabe durch der CLR bedeutet, dass im Unterschied zu Objekten in Visual Basic 6.0 und früheren Versionen, Sie genau bestimmen können, wann das Objekt zerstört wird. In einer solchen Situation werden Objekte als *nicht deterministische Lebensdauer*bezeichnet. In den meisten Fällen ändert die nicht deterministische Lebensdauer nicht das Schreiben von Anwendungen, solange beachtet wird, dass der `Finalize`-Destruktor möglicherweise nicht sofort nach Verlust des Gültigkeitsbereichs eines Objekts ausgeführt wird.

Ein weiterer Unterschied zu Garbage Collection-Systemen betrifft die Verwendung von `Nothing`. Zur Nutzung der Verweiszählung in Visual Basic 6.0 und früheren Versionen, wiesen Programmierer Objektvariablen zuweilen `Nothing` zu, um die Verweise, die diese Variablen gehalten haben, freizugeben. Wenn die Variable den letzten Verweis auf das Objekt gehalten hat, wurden die Ressourcen des Objekts sofort freigegeben. In späteren Versionen von Visual Basic und in einigen Fällen, in denen dieses Verfahren noch von Bedeutung ist, führt die Ausführung nie dazu, dass das referenzierte Objekt seine Ressourcen sofort freigibt. Um Ressourcen sofort freizugeben, verwenden Sie die <xref:System.IDisposable.Dispose%2A> -Methode des Objekts, falls verfügbar. Legen Sie für die Variable `Nothing` nur fest, wenn ihre Lebensdauer im Bezug zur Dauer, die der Garbage Collector zum Auffinden verwaister Objekte benötigt, lang ist.

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable.Dispose%2A>
- [Initialisierung und Beendigung von Komponenten](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [New-Operator](../../../language-reference/operators/new-operator.md)
- [Bereinigen von nicht verwalteten Ressourcen](../../../../standard/garbage-collection/unmanaged.md)
- [Schweigen](../../../language-reference/nothing.md)
