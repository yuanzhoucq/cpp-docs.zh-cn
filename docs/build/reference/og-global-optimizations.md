---
title: /Og（全局优化）
ms.date: 09/22/2017
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
ms.openlocfilehash: 5e45273b6b609f1bf78504a519c1fb98e2147f76
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818526"
---
# <a name="og-global-optimizations"></a>/Og（全局优化）

已否决。 提供本地和全局优化自动寄存器分配和循环优化。 我们建议你使用任一[/O1 （最小化大小）](o1-o2-minimize-size-maximize-speed.md)或[/o2 （最大化速度）](o1-o2-minimize-size-maximize-speed.md)改为。

## <a name="syntax"></a>语法

> /Og

## <a name="remarks"></a>备注

**/Og**已弃用。 现在默认情况下通常启用这些优化。 优化的详细信息，请参阅[/o1，/o2 （最小化大小、 最大化速度）](o1-o2-minimize-size-maximize-speed.md)或[/Ox （启用最速度优化）](ox-full-optimization.md)。

以下优化下有 **/Og**:

- 本地和全局公共子表达式消除

   在这种优化，一次计算公共子表达式的值。 在以下示例中，如果的值`b`并`c`三个表达式之间没有更改，编译器可以分配的计算`b + c`给临时变量，并将其替换为变量`b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   对于本地公共子表达式优化，编译器将检查公共子表达式的代码的一小部分。 对于全局公共子表达式优化，编译器将搜索整个函数的公共子表达式。

- 自动注册分配

   这种优化允许将经常使用变量和子表达式编译器在寄存器中;`register`关键字将被忽略。

- 循环优化

   这种优化从循环主体中删除固定的子表达式。 最佳的循环包含仅通过循环的每次执行更改其值的表达式。 在下面的示例中，表达式`x + y`不会更改在循环体中：

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   优化之后，`x + y`计算一次而不是每次执行循环：

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   编译器可以假定没有别名，与设置时，循环优化是更有效[__restrict](../../cpp/extension-restrict.md)， [noalias](../../cpp/noalias.md)，或[限制](../../cpp/restrict.md)。

   > [!NOTE]
   > 可以启用或禁用函数的函数使用全局优化`optimize`一起使用的杂注`g`选项。

有关相关信息，请参阅[/Oi （生成内部函数）](oi-generate-intrinsic-functions.md)并[/Ox （启用最速度优化）](ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 输入中的编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
