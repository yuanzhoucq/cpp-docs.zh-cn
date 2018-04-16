---
title: -Og （全局优化） |Microsoft 文档
ms.custom: ''
ms.date: 09/22/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs:
- C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 196e89a958ce49bf5e0087d98d2f40ada210cc87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="og-global-optimizations"></a>/Og（全局优化）

已否决。 提供局部和全局优化自动寄存器分配，并循环优化。 我们建议你使用[/O1 （最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或[/O2 （最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)相反。

## <a name="syntax"></a>语法

> /Og

## <a name="remarks"></a>备注

**/Og**已弃用。 现在默认情况下通常启用这些优化。 优化的详细信息，请参阅[/O1、 /O2 （最小化大小、 最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或[/Ox （启用最速度优化）](../../build/reference/ox-full-optimization.md)。

下列优化下有**/Og**:

- 本地和全局公共子表达式消除

     此优化的公共子表达式的值计算一次。 在下面的示例中，如果的值`b`和`c`三个表达式之间没有更改，编译器可以分配的计算`b + c`到临时变量，用替换的变量`b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

     对于本地公共子表达式优化，编译器将检查公共子表达式的代码的一小部分。 对于全局公共子表达式优化，编译器将搜索全部函数中的公共子表达式。

- 自动注册分配

     此优化允许编译器存储经常使用的变量和子表达式在寄存器中;`register`关键字将被忽略。

- 循环优化

     此优化从循环的主体中删除固定的子表达式。 最佳循环包含仅通过循环每次执行更改其值的表达式。 在下面的示例中，表达式`x + y`不会更改在循环体中：

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

     优化之后，`x + y`计算一次而不是每次执行循环时：

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

     当编译器可以假定没有别名，则进行设置时，才更有效循环优化[__restrict](../../cpp/extension-restrict.md)， [noalias](../../cpp/noalias.md)，或[限制](../../cpp/restrict.md)。

    > [!NOTE]
    > 你可以启用或禁用函数逐个函数地使用全局优化`optimize`杂注一起和`g`选项。

 有关相关信息，请参阅[/Oi （生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)和[/Ox （启用最速度优化）](../../build/reference/ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 输入中的编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)

[编译器选项](../../build/reference/compiler-options.md)

[设置编译器选项](../../build/reference/setting-compiler-options.md)