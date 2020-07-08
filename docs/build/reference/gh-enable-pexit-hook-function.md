---
title: /GH（启用 _pexit 挂钩函数）
description: 描述用于设置本地 _pexit 挂钩函数的/GH 编译器选项。
ms.date: 07/06/2020
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: b8fc355503055af8b928874ced39cb8224901d3e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058602"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH（启用 _pexit 挂钩函数）

`_pexit`在每个方法或函数的末尾调用函数。

## <a name="syntax"></a>语法

> **`/GH`**

## <a name="remarks"></a>备注

`_pexit`函数不是任何库的一部分。 你需要为提供定义 `_pexit` 。

除非你打算显式调用 `_pexit` ，否则不需要提供原型。 函数必须推送进入的所有寄存器的内容，并在退出时弹出未更改的内容。 它必须如下所示：

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

此声明不适用于64位项目。

`_pexit`类似于 `_penter` ; 有关如何编写函数的示例，请参见[ `/Gh` （启用 _penter 挂钩函数）](gh-enable-penter-hook-function.md) `_penter` 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[`/Gh`（启用 _penter 挂钩函数）](gh-enable-penter-hook-function.md)
