---
title: /GL（全程序优化）
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 6251209dac74a504bb0635f0c544c39935090a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292128"
---
# <a name="gl-whole-program-optimization"></a>/GL（全程序优化）

启用全程序优化。

## <a name="syntax"></a>语法

```
/GL[-]
```

## <a name="remarks"></a>备注

全程序优化允许编译器在程序中的所有模块上执行优化的信息。 对不全程序优化的情况下执行优化每个模块编译 （单位） 的基础。

全程序优化默认情况下处于关闭状态，必须显式启用。 但是，还有可能要明确禁用其与 **/gl-隐式**。

使用所有模块的信息，编译器可以：

- 优化函数边界间的寄存器的使用。

- 更好地跟踪对全局数据，允许加载和存储的数量减少的修改。

- 更好地的跟踪一组可能的项修改通过指针取消引用，请减少数量的加载和存储。

- 即使另一个模块中定义的函数的模块中函数进行内联。

使用生成的.obj 文件 **/GL**将不可用到此类链接器实用程序进行[EDITBIN](editbin-reference.md)并[DUMPBIN](dumpbin-reference.md)。

如果编译您的程序与 **/GL**并[/c](c-compile-without-linking.md)，应使用 /LTCG 链接器选项来创建输出文件。

[/ZI](z7-zi-zi-debug-information-format.md)不能用于 **/GL**

使用生成的文件格式 **/GL**当前版本中可能无法读取视觉对象的后续版本C++。 不应提供与生成的.obj 文件组成的.lib 文件 **/GL**除非您是愿意提供视觉对象的所有版本的.lib 文件的副本C++在你希望用户使用，现在和将来。

使用生成的.obj 文件 **/GL**预编译标头文件不应该用于生成的.lib 文件，除非将生成在同一台计算机上链接的.lib 文件 **/GL** .obj 文件。 在链接时，将需要从.obj 文件的预编译的头文件的信息。

有关可用优化和全程序优化的限制的详细信息，请参阅[/LTCG](ltcg-link-time-code-generation.md)。  **/GL**还可以按配置优化; 请参阅 /LTCG。  在编译时的配置文件引导式优化，如果希望从按配置优化的函数，必须使用进行编译[/Gy](gy-enable-function-level-linking.md)或隐含 /Gy 编译器选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 请参阅[/LTCG （链接时间代码生成）](ltcg-link-time-code-generation.md)有关如何指定的信息 **/GL**开发环境中。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
