---
ms.openlocfilehash: 97870553d4ec66a569ba63cd945639b03bbbd6df
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539474"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="336a0-101">Kestrel: Standardmäßig unterstützte TLS-Protokollversionen geändert</span><span class="sxs-lookup"><span data-stu-id="336a0-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="336a0-102">Kestrel verwendet jetzt die Standard-TLS-Protokollversionen des Systems, anstatt Verbindungen mit den TLS 1.1- und TLS 1.2-Protokollen wie bisher einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="336a0-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="336a0-103">Diese Änderung ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="336a0-103">This change allows:</span></span>

* <span data-ttu-id="336a0-104">TLS 1.3 wird standardmäßig in Umgebungen verwendet, die diese unterstützen.</span><span class="sxs-lookup"><span data-stu-id="336a0-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="336a0-105">TLS 1.0 wird in einigen Umgebungen wie Windows Server 2016 (Standard) verwendet, was üblicherweise [nicht wünschenswert](/security/engineering/solving-tls1-problem) ist.</span><span class="sxs-lookup"><span data-stu-id="336a0-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="336a0-106">Weitere Informationen finden Sie unter dem Issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="336a0-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="336a0-107">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="336a0-107">Version introduced</span></span>

<span data-ttu-id="336a0-108">Version 5.0 Vorschau 6</span><span class="sxs-lookup"><span data-stu-id="336a0-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="336a0-109">Altes Verhalten</span><span class="sxs-lookup"><span data-stu-id="336a0-109">Old behavior</span></span>

<span data-ttu-id="336a0-110">Kestrel erforderte, dass Verbindungen standardmäßig TLS 1.1 oder TLS 1.2 verwenden.</span><span class="sxs-lookup"><span data-stu-id="336a0-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="336a0-111">Neues Verhalten</span><span class="sxs-lookup"><span data-stu-id="336a0-111">New behavior</span></span>

<span data-ttu-id="336a0-112">Kestrel ermöglicht dem Betriebssystem, das am besten geeignete Protokoll auszuwählen und unsichere Protokolle zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="336a0-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="336a0-113">Der Standardwert für <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> ist nun `SslProtocols.None` statt `SslProtocols.Tls12 | SslProtocols.Tls11`.</span><span class="sxs-lookup"><span data-stu-id="336a0-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="336a0-114">Grund für die Änderung</span><span class="sxs-lookup"><span data-stu-id="336a0-114">Reason for change</span></span>

<span data-ttu-id="336a0-115">Die Änderung sollte bewirken, dass TLS 1.3 und zukünftige TLS-Versionen standardmäßig unterstützt werden, sobald sie verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="336a0-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="336a0-116">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="336a0-116">Recommended action</span></span>

<span data-ttu-id="336a0-117">Sofern in Ihrer Anwendung kein bestimmter Grund dagegen besteht, sollten Sie die neuen Standardwerte verwenden.</span><span class="sxs-lookup"><span data-stu-id="336a0-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="336a0-118">Vergewissern Sie sich, dass Ihr System so konfiguriert ist, dass nur sichere Protokolle zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="336a0-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="336a0-119">Führen Sie eine der folgenden Aktionen durch, um ältere Protokolle zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="336a0-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="336a0-120">Deaktivieren Sie ältere Protokolle wie TLS 1.0 systemweit mithilfe der [Anweisungen für Windows](../../../../docs/framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="336a0-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](../../../../docs/framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="336a0-121">Diese sind derzeit in allen Windows-Versionen standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="336a0-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="336a0-122">Wählen Sie die Protokolle, die Sie im Code unterstützen möchten, manuell wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="336a0-122">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="336a0-123">Leider gibt es keine API zum Ausschließen bestimmter Protokolle.</span><span class="sxs-lookup"><span data-stu-id="336a0-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="336a0-124">Kategorie</span><span class="sxs-lookup"><span data-stu-id="336a0-124">Category</span></span>

<span data-ttu-id="336a0-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="336a0-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="336a0-126">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="336a0-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
