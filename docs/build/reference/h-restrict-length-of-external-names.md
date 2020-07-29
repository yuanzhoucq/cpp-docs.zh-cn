---
title: /H（限制外部名称长度）
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 9a8976700cfb0f333c2715c573aa2d239e2a8e3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218983"
---
# <a name="h-restrict-length-of-external-names"></a>/H（限制外部名称长度）

已否决。 限制外部名称的长度。

## <a name="syntax"></a>语法

> **/H**<em>数字</em>

## <a name="arguments"></a>参数

*数字*<br/>
指定程序中允许的外部名称的最大长度。

## <a name="remarks"></a>备注

默认情况下，外部（公共）名称的长度为2047个字符。 这适用于 C 和 c + + 程序。 使用 **/h**只能减少允许的最大标识符长度，而不能增加。 **/H**和*number*之间的空格是可选的。

如果程序包含的外部名称的长度超过了*number*，则会忽略多余的字符。 如果编译程序时不使用 **/h**并且标识符包含2047个以上的字符，则编译器将生成[错误 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。

长度限制包括任何编译器创建的前导下划线（ **\_** ）或 at 符号（ **\@** ）。 这些字符是标识符的一部分，并且会占用很大的位置。

- 编译器将前导下划线（）添加 **\_** 到由 **`__cdecl`** （默认）和调用约定修改的名称 **`__stdcall`** 中，并将前导 at 符号（ **\@** ）添加到由调用约定修改的名称 **`__fastcall`** 。

- 编译器将自变量大小信息追加到由调用约定修改的名称 **`__fastcall`** **`__stdcall`** ，并将类型信息添加到 c + + 名称。

你可能会发现 **/h**有用：

- 创建混合语言或便携式程序时。

- 使用限制外部标识符长度限制的工具时。

- 希望限制符号在调试生成中使用的空间量时。

下面的示例演示如果标识符长度的限制太大，使用 **/h**实际上会引入错误：

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

使用 **/h**选项时，您还必须小心，因为预定义的编译器标识符。 如果最大标识符长度太小，某些预定义的标识符将无法解析以及某些库函数调用。 例如，如果使用了 `printf` 函数，并且在编译时指定了选项 **/H5** ，则将创建符号 **_prin**以便引用 `printf` ，并且将在库中找不到此符号。

使用 **/h**与[/Gl （全程序优化）](gl-whole-program-optimization.md)不兼容。

不推荐使用 **/h**选项，因为 Visual Studio 2005;最大长度限制已增加，不再需要 **/h** 。 有关弃用的编译器选项的列表，请参阅[按类别列出的编译器选项](compiler-options-listed-by-category.md)中的不**推荐使用和已删除编译器选项**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
