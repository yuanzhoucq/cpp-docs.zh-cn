---
title: /Qimprecise_fwaits（移除 Try 块中的 fwaits）
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: eb01d39ccbbdac60d629f95b9eb821ca0f2f5731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662392"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits（移除 Try 块中的 fwaits）

移除`fwait`命令的内部`try`，当你使用时中断[/fp： 除](../../build/reference/fp-specify-floating-point-behavior.md)编译器选项。

## <a name="syntax"></a>语法

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>备注

此选项没有任何影响，如果 **/fp： 除**也未指定。 如果指定 **/fp： 除外**选项，编译器将插入`fwait`命令的每一行中的代码周围`try`块。 这样一来，编译器可标识特定的生成异常的代码行。 **/Qimprecise_fwaits**删除内部`fwait`说明，使仅围绕等待`try`块。 这将改善性能，但编译器将只能够说这`try`块导致了异常，而不是哪一行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)