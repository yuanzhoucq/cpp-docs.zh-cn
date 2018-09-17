---
title: -Oi （生成内部函数） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs:
- C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527f326d629bc8d41efcd73a938994570bed4d2e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725908"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi（生成内部函数）

替换某些函数调用与内部函数或其他特殊形式的函数，可帮助你的应用程序运行得更快。

## <a name="syntax"></a>语法

```
/Oi[-]
```

## <a name="remarks"></a>备注

使用内部函数的程序的速度更快是因为它们没有函数调用的开销，但由于创建的其他代码可能更大。

请参阅[内部函数](../../preprocessor/intrinsic.md)的函数具有内部形式的详细信息。

**/Oi**只是一个请求到编译器的一些函数调用替换内部函数; 编译器可能会调用该函数 （极不替换为函数调用内部函数） 如果将导致更好的性能。

**x86 特定**

内部函数的浮点函数不执行任何特殊检查输入值并因此工作在有限范围内的输入，并且具有不同的异常处理和具有相同名称的库例程边界条件。 使用真正的内部形式表示的丢失和 IEEE 异常处理丢失`_matherr`和`errno`功能; 后者意味着丢失 ANSI 一致性。 但是，这些内部形式可以显著加快浮点密集型程序，并且许多程序的符合性问题的操作是几乎没有任何价值。

可以使用[Za](../../build/reference/za-ze-disable-language-extensions.md)编译器选项来重写的则返回 true 的内部浮点选项的生成。 在此情况下，函数将生成为库例程，后者将自变量直接传递到浮点芯片，而不是将自变量推送到程序堆栈。

**结束 x86 特定**

此外使用[内部函数](../../preprocessor/intrinsic.md)若要创建内部函数，或[函数 （C/c + +）](../../preprocessor/function-c-cpp.md)来显式强制函数调用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**优化**属性页。

1. 修改**启用内部函数**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>。

## <a name="see-also"></a>请参阅

[/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[编译器内部函数](../../intrinsics/compiler-intrinsics.md)