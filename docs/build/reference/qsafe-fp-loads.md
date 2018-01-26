---
title: /Qsafe_fp_loads | Microsoft Docs
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e079e084c641318c9bec0820263487139b4d5076
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

要求对浮点值使用整数移动指令，并禁用特定浮点加载优化。

## <a name="syntax"></a>语法

> **/Qsafe_fp_loads**

## <a name="remarks"></a>备注

**/ Qsafe_fp_loads**选项仅适用于编译器面向 x86; 它不是面向 x64 或 ARM 的编译器中可用。

**/ Qsafe_fp_loads**强制编译器使用整数移动指令而不是浮点移动指令内存和 MMX 之间移动数据寄存器。 多个控制路径中可加载的浮点值可能导致加载异常（例如 NaN 值）时，此选项还禁用这些值的寄存器加载优化。

此选项将重写[/fp： 除](../../build/reference/fp-specify-floating-point-behavior.md)。 **/ Qsafe_fp_loads**指定由指定的编译器行为子集**/fp： 除**。

**/ Qsafe_fp_loads**与不兼容[/clr](../../build/reference/clr-common-language-runtime-compilation.md)和[/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md)。 有关浮点点编译器选项的详细信息，请参阅[/fp （指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入中的编译器选项**其他选项**框。 选择**确定**以应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)  
[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
