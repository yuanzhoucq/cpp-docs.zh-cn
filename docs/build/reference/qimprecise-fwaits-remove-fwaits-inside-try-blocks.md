---
title: /Qimprecise_fwaits（移除 Try 块中的 fwaits）
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 40683382686ea64a80563f3f29b7d3523f4144a8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819709"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits（移除 Try 块中的 fwaits）

移除`fwait`命令的内部`try`，当你使用时中断[/fp： 除](fp-specify-floating-point-behavior.md)编译器选项。

## <a name="syntax"></a>语法

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>备注

此选项没有任何影响，如果 **/fp： 除**也未指定。 如果指定 **/fp： 除外**选项，编译器将插入`fwait`命令的每一行中的代码周围`try`块。 这样一来，编译器可标识特定的生成异常的代码行。 **/Qimprecise_fwaits**删除内部`fwait`说明，使仅围绕等待`try`块。 这将改善性能，但编译器将只能够说这`try`块导致了异常，而不是哪一行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
