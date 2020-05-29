---
title: /GH（启用 _pexit 挂钩函数）
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749236"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH（启用 _pexit 挂钩函数）

在每个方法`_pexit`或函数的末尾调用函数。

## <a name="syntax"></a>语法

```
/GH
```

## <a name="remarks"></a>备注

该`_pexit`函数不是任何库的一部分，由您提供`_pexit`的定义。

除非您计划显式调用`_pexit`，否则不需要提供原型。 该函数必须显示为具有以下原型，并且必须在输入时推送所有寄存器的内容，并在退出时弹出未更改的内容：

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`类似于`_penter`;有关如何编写`_pexit`函数的示例，请参阅[/Gh（启用_penter挂钩函数）。](gh-enable-penter-hook-function.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行” **** 属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
