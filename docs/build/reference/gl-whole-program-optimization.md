---
title: /GL（全程序优化）
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 875865a32dcb80cb8a6d8fa53646260f3d9413a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439650"
---
# <a name="gl-whole-program-optimization"></a>/GL（全程序优化）

启用全程序优化。

## <a name="syntax"></a>语法

```
/GL[-]
```

## <a name="remarks"></a>备注

全程序优化允许编译器对程序中的所有模块的信息进行优化。 如果没有完整的程序优化，将基于每个模块（编译单位）执行优化。

全程序优化默认情况下处于关闭状态，必须显式启用。 但是，也可以通过 **/GL-** 显式禁用该方法。

对于所有模块的信息，编译器可以：

- 优化跨函数边界使用寄存器。

- 更好地跟踪全局数据的修改，从而减少加载和存储的数量。

- 更好地跟踪由指针取消引用修改的可能的项集，从而减少加载和存储的数目。

- 即使在另一个模块中定义函数时，也会在模块中内联该函数。

使用 **/gl**生成的 .obj 文件将不会提供给[EDITBIN](editbin-reference.md)和[DUMPBIN](dumpbin-reference.md)这样的链接器实用工具。

如果使用 **/gl**和[/c](c-compile-without-linking.md)编译程序，则应使用/ltcg 链接器选项来创建输出文件。

[/Zi](z7-zi-zi-debug-information-format.md)不能与 **/gl**一起使用

在当前版本中使用 **/gl**生成的文件格式可能无法通过 Visual C++的后续版本读取。 你不应提供由使用 **/gl**生成的 .obj 文件组成的 .lib 文件，除非你愿意为所有版本的视觉对象C++发送 .lib 文件的副本，而你希望你的用户现在和将来都能使用。

使用 **/gl**和预编译头文件生成的 .obj 文件不应用于生成 .lib 文件，除非该 .lib 文件将链接到生成 **/gl** .obj 文件的同一计算机上。 链接时需要 .obj 文件的预编译头文件中的信息。

有关中提供的优化和全程序优化的限制的详细信息，请参阅[/ltcg](ltcg-link-time-code-generation.md)。  **/Gl**还可以提供按配置优化;请参阅/LTCG。  在针对按配置优化进行编译时，如果想要从按配置优化的函数进行排序，则必须使用[/gy](gy-enable-function-level-linking.md)或表示/Gy. 的编译器选项进行编译

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 有关如何在开发环境中指定 **/gl**的信息，请参阅[/ltcg （链接时间代码生成）](ltcg-link-time-code-generation.md) 。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
