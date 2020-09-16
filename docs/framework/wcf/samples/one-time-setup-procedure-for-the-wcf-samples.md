---
title: Einmaliges Setupverfahren für Windows Communication Foundation-Beispiele
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: bf25ea4734bad007fa3ac19df0664932d981519c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548116"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Einmaliges Setupverfahren für Windows Communication Foundation-Beispiele

Die meisten Windows Communication Foundation (WCF)-Beispiele werden in Internetinformationsdienste (IIS) gehostet und aus einem gemeinsamen virtuellen Verzeichnis ausgeführt. Mit diesem einmaligen Setup Verfahren wird ein Ordner auf dem Datenträger erstellt. Außerdem wird den IIS ein virtuelles Verzeichnis mit dem Namen **Service Model Samples**hinzugefügt.

Das virtuelle Verzeichnis **Service Model Samples** wird zum entwickeln und Ausführen aller Beispiele verwendet, die einen IIS-gehosteten Dienst verwenden. Dies ist das einzige virtuelle Verzeichnis, das zum Ausführen der Beispiele erforderlich ist. Durch die Erstellung eines Beispiels werden alle zuvor bereitgestellten Dienste in diesem virtuellen Verzeichnis ersetzt. Nur das zuletzt erstellte Beispiel wird bereitgestellt und ist dann in diesem virtuellen Verzeichnis verfügbar.

> [!NOTE]
> Sie müssen alle Befehle unter einem lokalen Administratorkonto ausführen. Wenn Sie Windows 7, Windows Vista oder Windows Server 2008 R2 verwenden, müssen Sie auch die Eingabeaufforderung mit erhöhten Rechten ausführen. Klicken Sie hierzu mit der rechten Maustaste auf das Symbol für die Eingabeaufforderung, und klicken Sie dann auf **als Administrator ausführen**. Alle Befehle in diesem Thema müssen an einer Eingabeaufforderung ausgeführt werden, die über die richtigen Pfadeinstellungen verfügt.  Dies kann am einfachsten sichergestellt werden, wenn Sie die Visual Studio-Eingabeaufforderung verwenden. Klicken Sie zum Öffnen dieser Eingabeaufforderung auf **Start**, wählen Sie **Alle Programme**, Scrollen Sie nach unten zu **Visual Studio 2010**, wählen Sie **Visual Studio-Tools**aus, klicken Sie mit der rechten Maustaste auf **Visual Studio-Eingabeaufforderung (2010)**, und klicken Sie dann auf **als Administrator** Wenn Sie eine Visual Studio Express Edition installiert haben, ist diese Eingabeaufforderung nicht verfügbar. In diesem Fall müssen Sie dem Systempfad "C:\Windows\Microsoft.Net\Framework\v4.0" hinzufügen.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Einmaliges Setupverfahren für WCF-Beispiele

1. Stellen Sie sicher, dass ASP.net eingerichtet ist. Weitere Informationen zum Einrichten von ASP.net finden Sie unter Hosting- [Anweisungen für den Internet Informationsdienst](internet-information-service-hosting-instructions.md).

2. Stellen Sie sicher, dass .NET Framework 4 installiert ist. Suchen Sie im folgenden Verzeichnis nach v 4.0 (oder höher): **\WINDOWS\Microsoft.NET\Framework**

3. Stellen Sie sicher, dass Visual Studio 2012 oder höher installiert ist, oder wenn das Betriebssystem Windows Server 2008 SP2 oder höher ist.

4. Führen Sie die folgenden Befehle aus: Weitere Informationen zum Ausführen dieser Befehle finden Sie unter der IIS- [gehostete Dienst schlägt fehl](/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Wenn IIS neu installiert wird, müssen die folgenden Befehle noch einmal ausgeführt werden.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Wenn Sie den Befehl ausführen `aspnet_regiis –i –enable` , wird der Standard-App-Pool mit .NET Framework 4 ausgeführt, was zu Inkompatibilitäts Problemen für andere Anwendungen auf demselben Computer führen kann.

5. Befolgen Sie die Anweisungen in der [Firewall](firewall-instructions.md) , um die von den Beispielen verwendeten Ports zu aktivieren.

6. Überprüfen Sie das folgende Standardverzeichnis: \<InstallDrive> :**\ WF_WCF_Samples**. Wenn die Beispiele bereits installiert wurden, ist dies das Standardverzeichnis.

7. Wenn die Beispiele nicht installiert sind, installieren Sie Sie [über Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF)-Beispiele für .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

8. Nachdem Sie die Beispiele installiert haben, wechseln Sie zu: \<InstallDrive> :**\ WF_WCF_Samples \wcf\setup \\ ** .

9. Führen Sie die **Setupvroot.bat** Batchdatei aus. Es werden folgende Schritte ausgeführt:

    - In IIS wird ein virtuelles Verzeichnis mit dem Namen ServiceModelSamples erstellt.

    - Es werden die neuen Datenträgerverzeichnisse %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples und %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin erstellt.

    Wenn Sie diese Verzeichnisse manuell einrichten möchten, lesen Sie die [Anweisungen zum Einrichten des virtuellen Verzeichnisses](virtual-directory-setup-instructions.md). Um alle in diesem Schritt vorgenommenen Änderungen rückgängig zu machen, führen Sie cleanupvroot.bat aus, sobald die Beispiele nicht mehr benötigt werden.

    > [!NOTE]
    > Diese Prozedur muss nur einmal auf einem Computer ausgeführt werden, es sei denn, cleanupvroot.bat wird ausgeführt.

10. Sie müssen dem Konto, unter dem Sie die Beispiele erstellen, und dem Netzwerkdienstbenutzer die Berechtigung zum Ändern von %SystemDrive%\inetpub\wwwroot zuweisen. Beim Erstellen wird bei einigen im Internet gehosteten Beispielen möglicherweise versucht, die kompilierten Binärdateien an den oben genannten Speicherort zu kopieren. Wenn Sie nicht die entsprechenden Berechtigungen festgelegt haben, können die Beispiele nicht erstellt werden. Alternativ können Sie die Berechtigungen unverändert lassen und die SDK-Eingabeaufforderung oder die Visual Studio-Eingabeaufforderung (2012) als Administrator ausführen oder die Beispiele in Visual Studio 2012 erstellen, die ebenfalls als Administrator ausgeführt werden.

    > [!NOTE]
    > Wenn dieser Schritt nicht ausgeführt wird, lässt sich keines der von IIS gehosteten Beispiele erstellen. Legen Sie die Berechtigungen unbedingt richtig fest, oder führen Sie die SDK-Eingabeaufforderung und Visual Studio-Eingabeaufforderung (2012) als Administrator aus.

11. Erstellen Sie das Verzeichnis C:\logs auf dem Computer. Möglicherweise wird es bei einigen Beispielen vorausgesetzt. Stellen Sie sicher, dass das entsprechende Konto Schreibzugriff auf diesen Ordner hat. Für Windows 7, Windows Vista und Windows Server 2008 R2 ist dieses Konto der **Netzwerkdienst**. Für Windows Server 2008 lautet das Konto NT-Autorität \ Netzwerkdienst. Für Windows XP und Windows Server 2003 lautet das Konto ASPNET.

12. Führen Sie die Datei "Setupcerttool.bat" aus. Diese Datei befindet sich im  \<InstallPath> Ordner "\ WF_WCF_Samples \wcf\setup\".  Mit diesem Skript werden folgende Aufgaben ausgeführt:

    - Erstellen des Tools FindPrivateKey

    - Erstellen eines Verzeichnisses mit dem Namen %ProgramFiles%\ServiceModelSampleTools

    - Kopieren Sie das neue Tool FindPrivateKey in dieses Verzeichnis.

    Dieses Tool ist für Beispiele erforderlich, die Zertifikate verwenden und in IIS gehostet werden.

    > [!NOTE]
    > Entfernen Sie aus Sicherheitsgründen die Definition des virtuellen Verzeichnisses und die in den vorhergehenden Setupschritten gewährten Berechtigungen, indem Sie die Batchdatei Cleanupvroot.bat nach Abschluss der Beispiele ausführen.

13. Für selbst gehostete Beispiele (nicht in IIS gehostet) ist auf dem Computer die Berechtigung zum Registrieren von HTTP-Adressen für die Überwachung erforderlich. Die Berechtigung für eine HTTP-Namespacereservierung wird von dem Benutzerkonto übernommen, das zum Ausführen des Beispiels verwendet wird. Standardmäßig verfügen Administratorkonten über die Berechtigung zum Registrieren von HTTP-Adressen. Nicht-Administratorkonten muss die Berechtigung für die von den Beispielen verwendeten HTTP-Namespaces gewährt werden. Weitere Informationen zum Konfigurieren von Namespacereservierungen finden Sie unter [Configuring HTTP and HTTPS (Konfigurieren von HTTP und HTTPS)](../feature-details/configuring-http-and-https.md).

14. Für einige Beispiele ist Message Queuing erforderlich. Installationsanweisungen finden Sie unter [Installieren von Message Queuing (MSMQ)](installing-message-queuing-msmq.md) .

    > [!NOTE]
    > Stellen Sie sicher, dass der MSMQ-Dienst gestartet wurde, bevor Sie Beispiele ausführen, für die Message Queuing erforderlich ist.

15. Einige Beispiele erfordern Zertifikate. S. [Installationsanleitung für IIS-Serverzertifikate (Internetinformationsdienste)](iis-server-certificate-installation-instructions.md).
