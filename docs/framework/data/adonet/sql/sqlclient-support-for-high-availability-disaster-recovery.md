---
title: SqlClient-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung
description: Erfahren Sie mehr über die Unterstützung der SqlClient-Anwendung für hohe Verfügbarkeit, Notfall Wiederherstellung in SQL Server mit AlwaysOn-Verfügbarkeitsgruppen.
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 7693210b7d9387e9b58fcc95febd3df0c70b4743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203435"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>SqlClient-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung

In diesem Thema wird die SqlClient-Unterstützung (in .NET Framework 4,5) für hohe Verfügbarkeit, Notfall Wiederherstellung (AlwaysOn-Verfügbarkeitsgruppen) erläutert.  Die Funktion für AlwaysOn-Verfügbarkeitsgruppen wurde SQL Server 2012 hinzugefügt. Weitere Informationen über AlwaysOn-Verfügbarkeitsgruppen finden Sie in der SQL Server-Onlinedokumentation.  
  
 Sie können jetzt den Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe (für hohe Verfügbarkeit und Notfallwiederherstellung) oder eine SQL Server 2012-Failoverclusterinstanz in der Verbindungseigenschaft angeben. Wenn eine SqlClient-Anwendung mit einer Always On-Datenbank verbunden ist, für die ein Failover ausgeführt wird, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung öffnen, damit ihre Ausführung nach dem Failover fortgesetzt werden kann.  
  
 Wenn Sie keine Verbindung mit einem Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz herstellen und mehrere IP-Adressen einem Hostnamen zugeordnet sind, durchläuft SqlClient nacheinander alle IP-Adressen, die dem DNS-Eintrag zugeordnet sind. Dies kann zeitaufwändig sein, wenn die erste vom DNS-Server zurückgegebene IP-Adresse an keine Netzwerkschnittstellenkarte (NIC) gebunden ist. Beim Herstellen einer Verbindung mit einem Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz versucht SqlClient, Verbindungen mit allen IP-Adressen gleichzeitig herzustellen, und wenn ein Verbindungsversuch erfolgreich war, verwirft der Treiber alle ausstehenden Verbindungsversuche.  
  
> [!NOTE]
> Das Erhöhen des Verbindungstimeouts sowie die Implementierung von Verbindungswiederholungslogik erhöhen die Wahrscheinlichkeit, dass eine Anwendung eine Verbindung zu einer Verfügbarkeitsgruppe herstellt. Da zudem eine Verbindung aufgrund eines Failovers fehlschlagen kann, empfiehlt sich die Implementierung von Verbindungswiederholungslogik, wodurch im Fall einer fehlgeschlagenen Verbindung bis zur erneuten Verbindung Wiederholungsversuche erfolgen.  
  
 Die folgenden Verbindungs Eigenschaften wurden SqlClient in .NET Framework 4,5 hinzugefügt:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Sie können diese Schlüsselwörter für Verbindungszeichenfolgen folgendermaßen programmgesteuert ändern:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> Das Festlegen `MultiSubnetFailover` von auf `true` ist für .NET Framework 4.6.1 oder höhere Versionen nicht erforderlich.
  
## <a name="connecting-with-multisubnetfailover"></a>Verbinden mit MultiSubnetFailover  

 Geben Sie immer `MultiSubnetFailover=True` an, wenn Sie eine Verbindung mit einem SQL Server 2012-Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz herstellen. `MultiSubnetFailover` aktiviert schnelleres Failover für alle Verfügbarkeitsgruppen und die Failoverclusterinstanz in SQL Server 2012 und reduziert die Failoverzeit für einzelne und Multisubnetz-AlwaysOn-Topologien erheblich. Während eines Multisubnetzfailovers versucht der Client Verbindungen parallel. Während eines Subnetzfailovers wird der TCP-Verbindungsversuch aggressiv wiederholt.  
  
 Die `MultiSubnetFailover`-Verbindungseigenschaft gibt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder SQL Server 2012-Failoverclusterinstanz bereitgestellt wird und dass SqlClient versucht, eine Verbindung mit der Datenbank auf der primären SQL Server-Instanz herzustellen, indem eine Verbindung mit allen IP-Adressen versucht wird. Wenn `MultiSubnetFailover=True` für eine Verbindung angegeben wird, wiederholt der Client TCP-Verbindungsversuche schneller als dies bei den standardmäßigen TCP-Neuübertragungsintervallen des Betriebssystems der Fall ist. Auf diese Weise kann die Verbindung nach einem Failover einer AlwaysOn-Verfügbarkeitsgruppe oder einer AlwaysOn-Failoverclusterinstanz schneller wiederhergestellt werden. Diese Einstellung gilt sowohl für Einzelsubnetz- als auch Multisubnetz-Verfügbarkeitsgruppen und -Failoverclusterinstanzen.  
  
 Weitere Informationen zu den Schlüsselwörtern für Verbindungszeichenfolgen, die in SqlClient unterstützt werden, finden Sie unter <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Das Angeben von `MultiSubnetFailover=True` wenn eine Verbindung mit anderen Komponenten als einem Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz hergestellt wird, führt zu verminderter Leistung und wird nicht unterstützt.  
  
 Befolgen Sie beim Herstellen einer Verbindung mit einem Server in einer Verfügbarkeitsgruppe oder einer SQL Server 2012-Failoverclusterinstanz die folgenden Richtlinien:  
  
- Verwenden Sie die `MultiSubnetFailover`-Verbindungseigenschaft, wenn Sie eine Verbindung mit einem Einzelsubnetz oder Multisubnetz herstellen. Dadurch wird die Leistung für beide verbessert.  
  
- Um eine Verbindung mit einer Verfügbarkeitsgruppe herzustellen, geben Sie in der Verbindungszeichenfolge den Verfügbarkeitsgruppenlistener der Verfügbarkeitsgruppe als Server an.  
  
- Ein Verbindungsversuch mit einer mit mehr als 64 IP-Adressen konfigurierten SQL Server-Instanz verursacht einen Verbindungsfehler.  
  
- Das Verhalten einer Anwendung, die die `MultiSubnetFailover`-Verbindungseigenschaft verwendet, wird nicht vom Authentifizierungstyp beeinflusst: SQL Server-Authentifizierung, Kerberos-Authentifizierung oder Windows-Authentifizierung.  
  
- Vergrößern Sie den Wert von `Connect Timeout`, um eine ausreichende Failoverzeit zu konfigurieren und die Anzahl der Verbindungsherstellungsversuche der Anwendung zu reduzieren.  
  
- Verteilte Transaktionen werden nicht unterstützt.  
  
 Wenn das schreibgeschützte Routing nicht in Kraft ist, scheitert das Herstellen einer Verbindung mit einem sekundären Replikatspeicherort in den folgenden Situationen:  
  
1. Wenn der sekundäre Replikatspeicherort nicht zum Akzeptieren von Verbindungen konfiguriert ist.  
  
2. Wenn eine Anwendung `ApplicationIntent=ReadWrite` verwendet (weiter unten erläutert), und der sekundäre Replikatspeicherort für schreibgeschützten Zugriff konfiguriert ist.  
  
 <xref:System.Data.SqlClient.SqlDependency> wird bei schreibgeschützten sekundären Replikaten nicht unterstützt.  
  
 Es kann keine Verbindung hergestellt werden, wenn ein primäres Replikat so konfiguriert ist, dass schreibgeschützte Arbeitslasten abgelehnt werden, und die Verbindungszeichenfolge `ApplicationIntent=ReadOnly` enthält.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aktualisieren zur Verwendung von Multisubnetzclustern aus Datenbankspiegelung  

 Ein Verbindungsfehler (<xref:System.ArgumentException>) tritt auf, wenn die Verbindungsschlüsselwörter `MultiSubnetFailover` und `Failover Partner` in der Verbindungszeichenfolge vorhanden sind oder wenn `MultiSubnetFailover=True` und ein anderes Protokoll als TCP verwendet wird. Es tritt auch ein Fehler (<xref:System.Data.SqlClient.SqlException>) auf, wenn `MultiSubnetFailover` verwendet wird und SQL Server eine Failoverpartnerantwort zurückgibt, die angibt, dass es Teil eines Datenbankspiegelungspaars ist.  
  
 Wenn Sie eine SqlClient-Anwendung aktualisieren, die derzeit Datenbankspiegelung in einem Multisubnetz-Szenario verwendet, müssen Sie die `Failover Partner`-Verbindungseigenschaft entfernen und mit `MultiSubnetFailover`, festgelegt auf `True`, ersetzen, sowie den Servernamen in der Verbindungszeichenfolge mit einem Verfügbarkeitsgruppenlistener ersetzen. Wenn eine Verbindungszeichenfolge `Failover Partner` und `MultiSubnetFailover=True` verwendet, generiert der Treiber einen Fehler. Wenn eine Verbindungszeichenfolge jedoch `Failover Partner` und `MultiSubnetFailover=False` (oder `ApplicationIntent=ReadWrite`) verwendet, verwendet die Anwendung Datenbankspiegelung.  
  
 Der Treiber gibt einen Fehler zurück, wenn die Datenbankspiegelung für die primäre Datenbank in der Verfügbarkeitsgruppe verwendet wird und wenn `MultiSubnetFailover=True` in der Verbindungszeichenfolge angegeben ist, wodurch eine Verbindung mit einer primären Datenbank und nicht mit einem Verfügbarkeitsgruppen-Listener hergestellt wird.  
  
## <a name="specifying-application-intent"></a>Angeben des Anwendungszwecks  

 Im Fall von `ApplicationIntent=ReadOnly` fordert der Client eine Lesearbeitslast an, wenn eine Verbindung mit einer AlwaysOn-Datenbank hergestellt wird. Der Server erzwingt den Versuch zur Verbindungszeit und während einer USE-Datenbankanweisung, aber nur für eine AlwaysOn-aktivierte Datenbank.  
  
 Das `ApplicationIntent`-Schlüsselwort funktioniert nicht mit schreibgeschützten Legacy-Datenbanken.  
  
 Eine Datenbank kann Lesearbeitslasten auf der AlwaysOn-Zieldatenbank zulassen bzw. nicht zulassen. (Dies geschieht über die `ALLOW_CONNECTIONS`-Klausel der Transact-SQL-Anweisungen `PRIMARY_ROLE` und `SECONDARY_ROLE`.)  
  
 Das `ApplicationIntent`-Schlüsselwort wird verwendet, um schreibgeschütztes Routing zu aktivieren.  
  
## <a name="read-only-routing"></a>Schreibgeschütztes Routing  

 Schreibgeschütztes Routing ist eine Funktion, die die Verfügbarkeit eines schreibgeschützten Replikats einer Datenbank sicherstellen kann. So aktivieren Sie schreibgeschütztes Routing:  
  
1. Sie müssen eine Verbindung zum Verfügbarkeitsgruppenlistener einer AlwaysOn-Verfügbarkeitsgruppe herstellen.  
  
2. Das Schlüsselwort der `ApplicationIntent`-Verbindungszeichenfolge muss auf `ReadOnly` festgelegt werden.  
  
3. Die Verfügbarkeitsgruppe muss vom Datenbankadministrator konfiguriert werden, um schreibgeschütztes Routing zu aktivieren.  
  
 Möglicherweise werden bei mehreren Verbindungen mithilfe von schreibgeschütztem Routing nicht alle mit demselben schreibgeschützten Replikat verbunden. Änderungen in der Datenbanksynchronisierung oder Änderungen in der Routingkonfiguration des Servers können zu Clientverbindungen mit anderen schreibgeschützten Replikaten führen. Sie gewährleisten, dass alle schreibgeschützten Anforderungen Verbindungen mit demselben schreibgeschützten Replikat herstellen, indem Sie keinen Verfügbarkeitsgruppenlistener an das Schlüsselwort der `Data Source`-Verbindungszeichenfolge übermitteln. Geben Sie stattdessen den Namen der schreibgeschützten Instanz an.  
  
 Schreibgeschütztes Routing dauert möglicherweise länger als das Herstellen einer primären Verbindung, da schreibgeschütztes Routing zuerst eine primäre Verbindung herstellt und dann nach der besten verfügbaren lesbaren Sekundärverbindung sucht. Deswegen sollten Sie das Anmeldetimeout vergrößern.  
  
## <a name="see-also"></a>Weitere Informationen

- [SQL Server Features und ADO.net](sql-server-features-and-adonet.md)
- [Übersicht über ADO.NET](../ado-net-overview.md)
