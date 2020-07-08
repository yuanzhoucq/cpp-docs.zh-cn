---
title: /Gh（启用 _penter 挂钩函数）
description: 描述用于调用提供的 _penter 函数的/Gh 编译器选项。
ms.date: 07/06/2020
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 96597d964e6a341aa25f4d52d34974949eb7b096
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058576"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh（启用 _penter 挂钩函数）

导致 `_penter` 在每个方法或函数开始时调用函数。

## <a name="syntax"></a>语法

> **`/Gh`**

## <a name="remarks"></a>备注

`_penter`函数不是任何库的一部分。 你需要为提供定义 `_penter` 。

除非你打算显式调用 `_penter` ，否则不需要提供原型。 函数必须推送进入的所有寄存器的内容，并在退出时弹出未更改的内容。 它必须如下所示：

```cpp
void __declspec(naked) __cdecl _penter( void );
```

此声明不适用于64位项目。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="example"></a>示例

在用 **/Gh**编译的情况下，下面的代码演示如何调用两次; 进入函数时，一次进入 `_penter` `main` 函数 `x` 。 该示例由两个源文件组成，分别进行编译。

```cpp
// local_penter.cpp
// compile with: cl /EHsc /c local_penter.cpp
// processor: x86
#include <stdio.h>

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```cpp
// Gh_compiler_option.cpp
// compile with: cl /EHsc /Gh Gh_compiler_option.cpp local_penter.obj
// processor: x86
#include <stdio.h>

void x() {}

int main() {
   x();
}
```

运行时，将 `_penter` 在进入和时调用本地函数 `main` `x` ：

```Output

In a function!
In a function!
```

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[`/GH`（启用 _pexit 挂钩函数）](gh-enable-pexit-hook-function.md)
