---
title: Datums- und Zeitdaten
description: Informationen zu Datentypen für die Behandlung von Datums-und Uhrzeit Informationen finden Sie in der .NET Framework Datenanbieter für SQL Server.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 6fe047fc672a2b42f886e81dcace91042a552932
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156315"
---
# <a name="date-and-time-data"></a>Datums- und Zeitdaten

SQL Server 2008 bietet neue Datentypen für Datums- und Uhrzeitinformationen. Die neuen Datentypen umfassen getrennte Typen für Datum und Uhrzeit sowie erweiterte Datentypen mit größerem Umfang, mehr Präzision und besserer Berücksichtigung von Zeitzonen. Ab .NET Framework Version 3.5 Service Pack (SP) 1 bietet der .NET Framework-Datenanbieter für SQL Server (<xref:System.Data.SqlClient>) vollständige Unterstützung für alle neuen Funktionen der SQL Server 2008-Datenbank-Engine. Sie müssen .NET Framework 3.5 SP1 (oder höher) installieren, um diese neuen Funktionen mit SqlClient zu verwenden.  
  
 SQL Server-Versionen vor SQL Server 2008 hatten nur zwei Datentypen für das Arbeiten mit Datums- und Uhrzeitwerten: `datetime` und `smalldatetime`. Beide Datentypen enthalten sowohl einen Datumswert als auch einen Uhrzeitwert, wodurch es schwierig ist, nur mit den Datums- oder nur mit den Uhrzeitwerten zu arbeiten. Außerdem unterstützen diese Datentypen nur Datumsangaben nach Einführung des gregorianischen Kalenders in England im Jahr 1753. Eine weitere Einschränkung besteht darin, dass diese älteren Datentypen keine Zeitzonen berücksichtigen, was es schwierig macht, mit Daten zu arbeiten, die aus mehreren Zeitzonen stammen.  
  
 Eine vollständige Dokumentation der SQL Server-Datentypen finden Sie in der SQL Server-Onlinedokumentation. In der folgenden Tabelle sind die versionsspezifischen Einsteigerthemen für Datums- und Uhrzeitdaten aufgeführt.  
  
 **SQL Server-Dokumentation**  
  
1. [Verwenden von Datums- und Uhrzeitdaten](/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Neue Datums-/Uhrzeitdaten in SQL Server 2008  

 In der folgenden Tabelle werden die Datums- und Uhrzeit-Datentypen beschrieben.  
  
|SQL Server-Datentyp|Beschreibung|  
|--------------------------|-----------------|  
|`date`|Der Bereich der gültigen Werte für den `date`-Datentyp reicht vom 1. Januar 0001 bis zum 31. Dezember 9999 mit einer Genauigkeit von einem Tag. Der Standardwert ist der 1. Januar 1900. Die Speichergröße beträgt 3 Byte.|  
|`time`|Der `time`-Datentyp speichert reine Uhrzeitwerte im 24-Stunden-Format. Der `time`-Datentyp hat einen Bereich von 00:00:00.0000000 bis 23:59:59.9999999 mit einer Genauigkeit von 100 Nanosekunden. Der Standardwert ist 00:00:00.0000000 (Mitternacht). Der `time`-Datentyp unterstützt benutzerdefinierte Sekundenbruchteilgenauigkeit, und die Speichergröße variiert je nach angegebener Genauigkeit zwischen 3 und 6 Bytes.|  
|`datetime2`|Der Datentyp `datetime2` kombiniert den Bereich und die Genauigkeit der Datentypen `date` und `time` zu einem einzelnen Datentyp.<br /><br /> Die Standardwerte und Formate für Zeichenfolgenliterale sind identisch mit denen, die in den Datentypen `date` und `time` definiert sind.|  
|`datetimeoffset`|Der `datetimeoffset`-Datentyp besitzt alle Funktionen von `datetime2`, verfügt darüber hinaus aber auch über eine als Abweichung (Offset) von der koordinierten Weltzeit angegebene Zeitzonenangabe. Der Zeitzonenoffset wird wie folgt dargestellt: [+&#124;-] HH:MM. Bei HH handelt es sich um zwei Ziffern im Bereich von 00 bis 24, die die Anzahl der Stunden im Zeitzonenoffset darstellen. Bei MM handelt es sich um zwei Ziffern im Bereich von 00 bis 59, die die Anzahl der zusätzlichen Minuten im Zeitzonenoffset darstellen. Uhrzeitformate werden mit einer Genauigkeit von bis zu 100 Nanosekunden unterstützt. Das obligatorische Plus- oder Minuszeichen gibt an, ob der Zeitzonenoffset von der UTC (Universal Time Coordinate oder Greenwich Mean Time) addiert oder subtrahiert wird, um die Ortszeit zu erhalten.|  
  
> [!NOTE]
> Weitere Informationen über die Verwendung des `Type System Version`-Schlüsselworts finden Sie unter <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Datumsformat und Datumsreihenfolge  

 Wie SQL Server Datums- und Uhrzeitwerte analysiert, hängt nicht nur von der Typsystem- und Serverversion ab, sondern auch von der Standardsprache und den Formateinstellungen des Servers. Eine Datumszeichenfolge, die für die Datumsformate einer Sprache funktioniert, wird möglicherweise nicht erkannt, wenn die Abfrage über eine Verbindung erfolgt, die eine andere Sprach- und Datumsformateinstellung verwendet.  
  
 Die Transact-SQL-Anweisung SET LANGUAGE legt implizit das DATEFORMAT fest, das die Reihenfolge der Datumsteile bestimmt. Sie können die Transact-SQL-Anweisung SET DATEFORMAT für eine Verbindung verwenden, um Datumswerte eindeutig zu bestimmen, indem Sie die Datumsteile in der Reihenfolge MTJ, TMJ, JMT, JTM, MJT oder TJM sortieren.  
  
 Wenn Sie kein DATEFORMAT für die Verbindung angeben, verwendet SQL Server die der Verbindung zugeordnete Standardsprache. Beispiel: Die Datumszeichenfolge 01/02/03 würde auf einem Server mit der Spracheinstellung „Englisch (USA)“ als MTJ (Januar 2, 2003) und auf einem Server mit der Spracheinstellung „Englisch (UK)“ als TMJ (1. Februar 2003) interpretiert. Das Jahr wird mithilfe der SQL Server-Regel für das Umstellungsjahr bestimmt, die das Umstellungsdatum für die Zuweisung des Jahrhundertwerts definiert. Weitere Informationen finden Sie unter Option "Umstellungs Jahr für Angaben mit [zwei Ziffern](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option)".  
  
> [!NOTE]
> Das Datumsformat JTM wird bei der Konvertierung aus einem Zeichenfolgenformat in `date`, `time`, `datetime2` oder `datetimeoffset` nicht unterstützt.  
  
 Weitere Informationen zum Interpretieren von Datums-und uhrzeitanzeit SQL Server finden [Sie unter Verwenden von Datums-und Uhrzeit Daten](/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Datentypen und Parameter zur Angabe von Datum und Uhrzeit  

 Die folgenden Enumerationen wurden <xref:System.Data.SqlDbType> hinzugefügt, um die neuen Datums- und Uhrzeitdatentypen zu unterstützen.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Sie können den Datentyp eines <xref:System.Data.SqlClient.SqlParameter> mithilfe einer der voranstehenden <xref:System.Data.SqlDbType>-Enumerationen angeben.

> [!NOTE]
> Sie können die `DbType`-Eigenschaft von `SqlParameter` nicht auf `SqlDbType.Date` festlegen.

 Der Typ eines <xref:System.Data.SqlClient.SqlParameter> kann auch generisch angegeben werden, indem die <xref:System.Data.SqlClient.SqlParameter.DbType%2A>-Eigenschaft eines `SqlParameter`-Objekts auf einen bestimmten <xref:System.Data.DbType>-Enumerationswert festgelegt wird. Zur Unterstützung der Datentypen `datetime2` und `datetimeoffset` wurden <xref:System.Data.DbType> die im Folgenden aufgeführten Enumerationswerte hinzugefügt:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Diese neuen Enumerationen ergänzen die Enumerationen `Date`, `Time` und `DateTime`, die bereits in früheren .NET Framework-Versionen vorhanden waren.  
  
 Der .NET Framework-Datenanbietertyp eines Parameterobjekts wird vom .NET Framework-Typ des Werts des Parameterobjekts oder vom `DbType` des Parameterobjekts hergeleitet. Es wurden keine neuen <xref:System.Data.SqlTypes>-Datentypen eingeführt, um die neuen Datums- und Uhrzeitdatentypen zu unterstützen. In der folgenden Tabelle werden die Zuordnungen zwischen den Datums- und Uhrzeitdatentypen von SQL Server 2008 und den CLR-Datentypen beschrieben.  
  
|SQL Server-Datentyp|.NET Framework-Typ|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|Date|Date|  
|time|System.TimeSpan|Time|Time|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|Datetime|Datetime|  
|smalldatetime|System.DateTime|Datetime|Datetime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter-Eigenschaften  

 In der folgenden Tabelle werden `SqlParameter`-Eigenschaften beschrieben, die für Datums- und Uhrzeitdatentypen relevant sind.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Ruft ab oder legt fest, ob ein Wert NULL sein kann. Wenn Sie den Parameterwert NULL an den Server senden, müssen Sie <xref:System.DBNull> anstelle von `null` (`Nothing` in Visual Basic) angeben. Weitere Informationen zu Daten Bank Nullen finden Sie unter [Behandeln von NULL-Werten](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Ruft die maximale Anzahl von Stellen ab, die verwendet werden, um den Wert darzustellen, oder legt diese fest. Diese Einstellung wird für Datums -und Uhrzeitdatentypen ignoriert.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Ruft die Anzahl der Dezimalstellen für die Auflösung des Uhrzeitteils des Werts für `Time`, `DateTime2` und `DateTimeOffset` ab, oder legt diese fest. Der Standardwert ist 0, was bedeutet, dass die tatsächliche Skala vom Wert hergeleitet und an den Server gesendet wird.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Wird für Datums -und Uhrzeitdatentypen ignoriert.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Ruft den Parameterwert ab oder legt ihn fest.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Ruft den Parameterwert ab oder legt ihn fest.|  
  
> [!NOTE]
> Uhrzeitwerte, die kleiner als 0 oder größer oder gleich 24 Stunden sind, lösen eine <xref:System.ArgumentException> aus.  
  
### <a name="creating-parameters"></a>Erstellen von Parametern  

 Sie können ein <xref:System.Data.SqlClient.SqlParameter>-Objekt erstellen, indem Sie dessen Konstruktor verwenden, oder Sie fügen es zu einer <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A>-Auflistung hinzu, indem Sie die `Add`-Methode der <xref:System.Data.SqlClient.SqlParameterCollection> aufrufen. Die `Add`-Methode verwendet als Eingabe entweder Konstruktorargumente oder ein vorhandenes Parameterobjekt.  
  
 Die nächsten Abschnitte in diesem Thema enthalten Beispiele zum Angeben von Datums- und Uhrzeitparametern. Weitere Beispiele für das Arbeiten mit Parametern finden Sie unter [Konfigurieren von Parametern und Parameter Datentypen](../configuring-parameters-and-parameter-data-types.md) und [DataAdapter-Parametern](../dataadapter-parameters.md).  
  
### <a name="date-example"></a>Datumsbeispiel  

 Das folgende Codefragment zeigt, wie ein `date`-Parameter angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Uhrzeitbeispiel  

 Das folgende Codefragment zeigt, wie ein `time`-Parameter angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Datetime2-Beispiel  

 Das folgende Codefragment zeigt, wie ein `datetime2`-Parameter mit Datums- und Uhrzeitteilen angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>DateTimeOffSet-Beispiel  

 Das folgende Codefragment zeigt, wie ein `DateTimeOffSet`-Parameter mit einem Datum, einer Uhrzeit und dem Zeitzonenoffset 0 angegeben werden kann.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  

 Sie können Parameter auch mithilfe der `AddWithValue`-Methode von <xref:System.Data.SqlClient.SqlCommand> angeben, wie im folgenden Codefragment gezeigt. Die `AddWithValue`-Methode ermöglicht jedoch nicht, <xref:System.Data.SqlClient.SqlParameter.DbType%2A> oder <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> für den Parameter anzugeben.  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 Der `@date`-Parameter kann den Datentypen `date`, `datetime` oder `datetime2` auf dem Server zugewiesen werden. Wenn Sie mit den neuen `datetime`-Datentypen arbeiten, müssen Sie die <xref:System.Data.SqlDbType>-Eigenschaft des Parameters explizit auf den Datentyp der Instanz festlegen. Das Verwenden von <xref:System.Data.SqlDbType.Variant> oder implizite Bereitstellen von Parameterwerten kann zu Problemen bei der Abwärtskompatibilität der Datentypen `datetime` und `smalldatetime` führen.  
  
 Die folgende Tabelle zeigt, welche `SqlDbTypes` von welchen CLR-Typen abgeleitet werden:  
  
|CLR-Typ|Abgeleiteter SqlDbType|  
|--------------|------------------------|  
|Datetime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Abrufen von Datums- und Uhrzeitdaten  

 In der folgenden Tabelle werden die Methoden zum Abrufen von Datums- und Uhrzeitwerten in SQL Server 2008 beschrieben.  
  
|SqlClient-Methode|Beschreibung|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Ruft den angegebenen Spaltenwert als <xref:System.DateTime>-Struktur ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Ruft den angegebenen Spaltenwert als <xref:System.DateTimeOffset>-Struktur ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Gibt den Typ zurück, der der zugrunde liegende anbieterspezifische Typ des Felds ist. Gibt für neue Datums- und Uhrzeittypen die gleichen Typen wie `GetFieldType` zurück.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Ruft den Wert der angegebenen Spalte ab. Gibt für die neuen Datums- und Uhrzeittypen die gleichen Typen wie `GetValue` zurück.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Ruft die Werte im angegebenen Array ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Ruft den Spaltenwert als <xref:System.Data.SqlTypes.SqlString> ab. Eine <xref:System.InvalidCastException> tritt auf, wenn die Daten nicht als `SqlString` ausgedrückt werden können.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Ruft Spaltendaten als ihren standardmäßigen `SqlDbType` ab. Gibt für die neuen Datums- und Uhrzeittypen die gleichen Typen wie `GetValue` zurück.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Ruft die Werte im angegebenen Array ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Ruft den Spaltenwert als Zeichenfolge ab, wenn „Type System Version“ auf SQL Server 2005 festgelegt ist. Eine <xref:System.InvalidCastException> tritt auf, wenn die Daten nicht als Zeichenfolge ausgedrückt werden können.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Ruft den angegebenen Spaltenwert als <xref:System.TimeSpan>-Struktur ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Ruft den angegebenen Spaltenwert als zugrunde liegenden CLR-Typ ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Ruft Spaltenwerte in einem Array ab.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Gibt eine <xref:System.Data.DataTable> zurück, die die Metadaten des Resultsets beschreibt.|  
  
> [!NOTE]
> Die neue Datums- und Uhrzeitwerte für `SqlDbTypes` werden nicht für Code unterstützt, der in SQL Server prozessintern ausgeführt wird. Eine Ausnahme wird ausgelöst, wenn einer dieser Typen an den Server übergeben wird.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Angeben von Datums- und Uhrzeitwerten als Literale  

 Sie können Datums- und Uhrzeitdatentypen angeben, indem Sie eine Vielzahl verschiedener Formate für Literalzeichenfolgen verwenden, die SQL Server dann zur Laufzeit auswertet und in interne Datums-/Uhrzeitstrukturen konvertiert. SQL Server erkennt Datums- und Uhrzeitdaten, die in einfache Anführungszeichen (') eingeschlossen sind. Die folgenden Beispiele veranschaulichen einige Formate:  
  
- Alphabetische Datumsformate wie `'October 15, 2006'`.  
  
- Numerische Datumsformate wie `'10/15/2006'`.  
  
- Ungetrennte Zeichenfolgenformate wie `'20061015'`, die als 15. Oktober 2006 interpretiert werden, wenn Sie das ISO-Standarddatumsformat verwenden.  
  
> [!NOTE]
> Sie finden die vollständige Dokumentation aller Formate von Literalzeichenfolgen und anderer Features der Datums- und Uhrzeitdatentypen in der SQL Server-Onlinedokumentation.  
  
 Uhrzeitwerte, die kleiner als 0 oder größer oder gleich 24 Stunden sind, lösen eine <xref:System.ArgumentException> aus.  
  
## <a name="resources-in-sql-server-books-online"></a>Ressourcen in der SQL Server-Onlinedokumentation  

 Weitere Informationen zum Arbeiten mit Datums-und Uhrzeitwerten in SQL Server finden Sie in den folgenden Ressourcen in SQL Server-Onlinedokumentation.  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Datums- und Uhrzeitdatentypen und zugehörige Funktionen (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Bietet eine Übersicht über alle Transact-SQL-Datentypen und -Funktionen zur Angabe des Datums und der Uhrzeit.|  
|[Verwenden von Datums- und Uhrzeitdaten](/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Stellt Informationen zu den Datentypen und Funktionen zur Angabe des Datums und der Uhrzeit sowie Beispiele für deren Verwendung bereit.|  
|[Datentypen (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|Beschreibt System Datentypen in SQL Server.|  
  
## <a name="see-also"></a>Weitere Informationen

- [SQL Server-Datentypzuordnungen](../sql-server-data-type-mappings.md)
- [Konfigurieren von Parametern und Parameterdatentypen](../configuring-parameters-and-parameter-data-types.md)
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
- [Übersicht über ADO.NET](../ado-net-overview.md)
