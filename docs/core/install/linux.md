---
title: Installieren von .NET Core auf Linux-Distributionen
description: Erfahren Sie, welche Linux-Distributionen die Installation von .NET Core unter Linux unterstützen.
author: adegeo
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: 368ee879e5ab9027bd37c3ced12ed377276de507
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863772"
---
# <a name="install-net-core-on-linux"></a>Installieren von .NET Core unter Linux

> [!div class="op_single_selector"]
>
> - [Installieren unter Windows](windows.md)
> - [Installieren unter macOS](macos.md)
> - [Installieren unter Linux](linux.md)

.NET Core ist für verschiedene Linux-Distributionen verfügbar. Für die meisten Linux-Plattformen und -Distributionen gibt es jedes Jahr eine Hauptversion. Die meisten bieten einen Paket-Manager, der zur Installation von .NET Core genutzt wird. In diesem Artikel wird beschrieben, was derzeit unterstützt wird und welcher Paket-Manager verwendet wird.

Der Rest dieses Artikels ist eine Übersicht über die einzelnen Linux-Hauptdistributionen, die .NET Core unterstützt. Alle .NET Core-Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) erreicht oder die Linux-Distribution das Ende ihrer Lebensdauer erreicht.

Eine LTS-Version (Long-Term Release) bietet bestmögliche Kompatibilität.

## <a name="unsupported-releases"></a>Nicht unterstützte Versionen

Die folgenden Versionen von .NET Core werden ❌ nicht mehr unterstützt. Die Downloads dafür bleiben weiterhin veröffentlicht:

- 3.0
- 2.2
- 2.0

Diese Versionen ohne Support werden in den folgenden Abschnitten nicht näher beschrieben, und Ihre Laufzeit kann variieren, wenn Sie versuchen, sie zu installieren.

## <a name="alpine"></a>Alpine

Es sind keine Installationsprogramme für Alpine vorhanden. Sie müssen entweder das [Installationsskript](linux-alpine.md#scripted-install) verwenden oder die Anweisungen zur [manuellen Installation](linux-alpine.md#manual-install) befolgen.

Die folgende Tabelle enthält die derzeit unterstützten .NET Core-Releases sowie die Versionen von Alpine, unter denen sie unterstützt werden. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) oder die Version von [Alpine das Ende ihrer Lebensdauer](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases) erreicht.

- ✔️ gibt an, dass die Version von Alpine oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von Alpine oder .NET Core in diesem Alpine-Release nicht unterstützt wird.
- Wenn sowohl eine Version von Alpine als auch eine Version von .NET Core mit ✔️ versehen sind, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3.12](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [3.11](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [3.10](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [3.9](linux-alpine.md)   | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [3.8](linux-alpine.md)   | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter Alpine](linux-alpine.md).

## <a name="centos"></a>CentOS

CentOS 7 nutzt Yum als Paket-Manager, CentOS 8 verwendet DNF.

Die folgende Tabelle enthält die derzeit unter CentOS 7 und CentOS 8 unterstützten .NET Core-Versionen. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) erreicht oder die Version von CentOS nicht mehr unterstützt wird.

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter CentOS](linux-centos.md).

## <a name="debian"></a>Debian

Debian verwendet APT (Advanced Package Tool) als Paket-Manager.

Die folgende Tabelle enthält die derzeit unterstützten .NET Core-Versionen und Versionen von Debian, unter denen sie unterstützt werden. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) oder die Version von [Debian das Ende ihrer Lebensdauer erreicht](https://wiki.debian.org/DebianReleases).

- ✔️ gibt an, dass die Version von Debian oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von Debian oder .NET Core in dieser Debian-Version nicht unterstützt wird.
- Wenn sowohl eine Version von Debian als auch eine Version von .NET Core über ✔️ verfügen, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter Debian](linux-debian.md).

## <a name="fedora"></a>Fedora

Fedora verwendet DNF als Paket-Manager.

Die folgende Tabelle enthält die derzeit unterstützten .NET Core-Versionen und Versionen von Fedora, unter denen sie unterstützt werden. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) oder die Version von [Fedora das Ende ihrer Lebensdauer erreicht](https://fedoraproject.org/wiki/End_of_life).

- ✔️ gibt an, dass die Version von Fedora oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von Fedora oder .NET Core in dieser Fedora-Version nicht unterstützt wird.
- Wenn sowohl eine Version von Fedora als auch eine Version von .NET Core über ✔️ verfügen, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 Preview |
| ❌ [29](linux-fedora.md#fedora-29-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 Preview |
| ❌ [28](linux-fedora.md#fedora-28-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ❌ [27](linux-fedora.md#fedora-27-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter Fedora](linux-fedora.md).

## <a name="opensuse"></a>openSUSE

openSUSE verwendet zypper als Paket-Manager.

Die folgende Tabelle enthält die derzeit unter openSUSE 15 unterstützten .NET Core-Versionen. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) erreicht oder die Version von openSUSE nicht mehr unterstützt wird.

- ✔️ gibt an, dass die Version von openSUSE oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von openSUSE oder .NET Core in dieser openSUSE-Version nicht unterstützt wird.
- Wenn sowohl eine Version von openSUSE als auch eine Version von .NET Core über ✔️ verfügen, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter openSUSE](linux-opensuse.md).

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) verwendet yum (RHEL 7) und DNF (RHEL 8) als Paket-Manager.

Die folgende Tabelle enthält die derzeit unter RHEL 7 und RHEL 8 unterstützten .NET Core-Versionen. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) erreicht oder die Version von RHEL nicht mehr unterstützt wird.

- ✔️ gibt an, dass die Version von RHEL oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von RHEL oder .NET Core in dieser RHEL-Version nicht unterstützt wird.
- Wenn sowohl eine Version von RHEL als auch eine Version von .NET Core über ✔️ verfügen, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter RHEL](linux-rhel.md).

## <a name="sles"></a>SLES

SLES verwendet zypper als Paket-Manager.

Die folgende Tabelle enthält die derzeit unter SLES 12 SP2 and SLES 15 unterstützten .NET Core-Versionen. Diese Versionen werden weiterhin unterstützt, bis entweder die Version von [.NET Core das Ende des Supports](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) erreicht oder die Version von SLES nicht mehr unterstützt wird.

- ✔️ gibt an, dass die Version von SLES oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von SLES oder .NET Core in dieser SLES-Version nicht unterstützt wird.
- Wenn sowohl eine Version von SLES als auch eine Version von .NET Core über ✔️ verfügen, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter SLES](linux-sles.md).

## <a name="ubuntu"></a>Ubuntu

Ubuntu verwendet APT (Advanced Package Tool) als Paket-Manager.

Die folgende Tabelle zeigt den Supportstatus von Ubuntu und .NET Core.

- ✔️ gibt an, dass die Version von Ubuntu oder .NET Core weiterhin unterstützt wird.
- ❌ gibt an, dass die Version von Ubuntu oder .NET Core in dieser Ubuntu-Version nicht unterstützt wird.
- Wenn sowohl eine Version von Ubuntu als auch eine Version von .NET Core über ✔️ verfügen, wird diese Kombination aus Betriebssystem und .NET unterstützt.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (nur manuelle Installation) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [19.10](linux-ubuntu.md#1910-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [19.04](linux-ubuntu.md#1904-)       | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 Preview |
| ❌ [18.10](linux-ubuntu.md#1810-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ✔️ [18.04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ❌ [16.10](linux-ubuntu.md#1610-)       | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ✔️ [16.04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

Weitere Informationen finden Sie unter [Installieren von .NET Core unter Ubuntu](linux-ubuntu.md).

## <a name="next-steps"></a>Nächste Schritte

- [Überprüfen, ob .NET Core bereits installiert ist](how-to-detect-installed-versions.md?pivots=os-linux)
- [Tutorial: Erstellen einer neuen App mit Visual Studio Code](../tutorials/with-visual-studio-code.md)
- [Tutorial: Containerisieren einer .NET Core-App](../docker/build-container.md)
