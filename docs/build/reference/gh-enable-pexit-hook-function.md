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
ms.openlocfilehash: 9be8573f5f9c344d2675bd7c9fc7d8beb3c8cffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527642"
---
# <a name="gh-enable-pexit-hook-function"></a>/GH（启用 _pexit 挂钩函数）

调用`_pexit`函数每个方法或函数的末尾。

## <a name="syntax"></a>语法

```
/GH
```

## <a name="remarks"></a>备注

`_pexit`函数不是任何库的一部分，并将由你提供的定义`_pexit`。

除非您打算显式调用`_pexit`，不需要提供原型。 该函数必须看起来似乎具有以下原型，并且必须在进入时推送所有寄存器的内容，在退出时弹出未更改的内容：

```
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit` 类似于`_penter`; 请参阅[/Gh (启用 _penter 挂钩函数)](../../build/reference/gh-enable-penter-hook-function.md)以举例说明如何编写`_pexit`函数。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)