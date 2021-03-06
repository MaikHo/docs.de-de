---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: b004acb0c1c7d145c59a1e3a88ef7f1d405a91c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400557"
---
# <a name="-optionexplicit"></a>-optionexplicit
Führt dazu, dass der Compiler Fehler meldet, wenn Variablen nicht deklariert werden, bevor sie verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumente  
 `+` &#124; `-`  
 Dies ist optional. Geben Sie `-optionexplicit+` an, um die explizite Variablendeklaration erforderlich zu machen. Die `-optionexplicit+`-Option ist der Standardwert und ist identisch mit `-optionexplicit`. Die `-optionexplicit-`-Option ermöglicht die implizite Deklaration von Variablen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Quellcodedatei eine [Option Explicit-Anweisung](../../language-reference/statements/option-explicit-statement.md) enthält, überschreibt die Anweisung die Einstellung des `-optionexplicit`-Befehlszeilencompilers.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>So legen Sie -optionexplicit in der integrierten Entwicklungsumgebung in Visual Studio fest  
  
1. Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.
  
2. Klicken Sie auf die Registerkarte **Kompilieren**.  
  
3. Ändern Sie den Wert im Feld **Option Explicit** entsprechend.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code wird kompiliert, wenn `-optionexplicit-` verwendet wird.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Siehe auch

- [Visual Basic-Befehlszeilencompiler](index.md)
- [-optioncompare](optioncompare.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [Beispiele für Kompilierungsbefehlszeilen](sample-compilation-command-lines.md)
- [Option Explicit-Anweisung](../../language-reference/statements/option-explicit-statement.md)
- [VB-Standard, Projekte, Dialogfeld „Optionen“](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
