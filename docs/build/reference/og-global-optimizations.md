---
title: /Og（全局优化）
description: 介绍了弃用的 MSVC 编译器选项/Og，以前用于启用全局优化。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: c1cab53ccb391bd7d6ca7660e2750f53aa7c72e4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180846"
---
# <a name="og-global-optimizations"></a>`/Og` (全局优化) 

已弃用。 提供本地和全局优化、自动注册分配和循环优化。 建议使用[ `/O1` (最小化大小) ](o1-o2-minimize-size-maximize-speed.md)或[ `/O2` () 最大化速度](o1-o2-minimize-size-maximize-speed.md)。

## <a name="syntax"></a>语法

> **`/Og`**

## <a name="remarks"></a>备注

**`/Og`** 已弃用。 默认情况下，在启用任何优化后，将默认启用这些优化。 有关优化的详细信息，请参阅[ `/O1` `/O2` (最小化大小、最大化速度) ](o1-o2-minimize-size-maximize-speed.md)或[ `/Ox` (启用大多数速度优化) ](ox-full-optimization.md)。

下提供了以下优化 **`/Og`** ：

- 本地和全局公共子表达式消除

   在此优化中，将计算通用子表达式的值一次。 在下面的示例中，如果 `b` `c` 在三个表达式之间没有更改的值，则编译器可将的计算分配 `b + c` 给临时变量，并将该变量用于 `b + c` ：

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   对于本地公共子表达式优化，编译器将检查常见子表达式的代码的简短部分。 对于全局公共子表达式优化，编译器会在整个函数中搜索常见子表达式。

- 自动注册分配

   此优化允许编译器将经常使用的变量和子表达式存储在寄存器中;`register`忽略关键字。

- 循环优化

   此优化从循环主体中删除固定子表达式。 最佳循环只包含其值在每次执行循环时都发生更改的表达式。 在下面的示例中，表达式 `x + y` 在循环体中不会发生更改：

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   优化之后， `x + y` 只计算一次（而不是每次执行循环）：

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   当编译器可以假设没有别名（您通过、或设置）时，循环优化更 [`__restrict`](../../cpp/extension-restrict.md) 有效 [`noalias`](../../cpp/noalias.md) [`restrict`](../../cpp/restrict.md) 。

   > [!NOTE]
   > 可以通过将 `optimize` 杂注与选项一起使用来启用或禁用每个函数的全局优化 `g` 。

有关相关信息，请参阅[ `/Oi` (生成内部函数) ](oi-generate-intrinsic-functions.md)并[ `/Ox ` (启用大多数速度优化) ](ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
