---
title: Breaking Changes bei der Kryptografie
description: Listet die Breaking Changes bei der Kryptografie in .NET Core auf.
ms.date: 04/22/2020
ms.openlocfilehash: 34098027c4cbe5e5fb31a22d981af706e07cb7da
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556024"
---
# <a name="cryptography-breaking-changes"></a>Breaking Changes bei der Kryptografie

Auf dieser Seite sind die folgenden Breaking Changes dokumentiert:

| Unterbrechende Änderung | Eingeführt in Version |
| - | :-: |
| [BEGIN TRUSTED CERTIFICATE-Syntax nicht mehr für Stammzertifikate unter Linux unterstützt](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [EnvelopedCms verwendet standardmäßig AES-256-Verschlüsselung](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [Die Mindestgröße für die Generierung von RSAOpenSsl-Schlüsseln wurde heraufgesetzt](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3.0 zieht OpenSSL 1.1.x OpenSSL 1.0.x vor](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [Der boolesche Parameter von SignedCms.ComputeSignature wird beachtet](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
