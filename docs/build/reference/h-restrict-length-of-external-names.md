---
title: -H （限制外部名称长度） |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /h
dev_langs:
- C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4881ba20e999b13e2a7841161a775eac69638f6
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861013"
---
# <a name="h-restrict-length-of-external-names"></a>/H（限制外部名称长度）

已否决。 限制外部名称的长度。

## <a name="syntax"></a>语法

> **/H**<em>数</em>

## <a name="arguments"></a>自变量

*数量*<br/>
指定在程序中允许的外部名称的最大长度。

## <a name="remarks"></a>备注

默认情况下，外部 （公共） 名称的长度为 2047 个字符。 这适用于 C 和 c + + 程序。 使用 **/H**只能减少标识符的最大长度，而不增加。 之间有空格 **/H**并*数*是可选的。

如果程序包含外部名称长度超过*数*，会忽略多余字符。 如果编译的程序而无需 **/H** ，然后如果标识符包含超过 2047 个字符，编译器将生成[致命错误 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。

长度限制包括任何编译器创建的前导下划线 (**\_**) 或 at 符号 (**\@**)。 这些字符是标识符的一部分，占用有效位置。

- 编译器将添加前导下划线 (**\_**) 到名称修改`__cdecl`（默认值） 和`__stdcall`注册时调用约定和前导 (**\@**) 修改名称为`__fastcall`调用约定。

- 编译器将参数大小信息追加到名称修改`__fastcall`和`__stdcall`调用约定，并将类型信息添加到 c + + 名称。

您可能会发现 **/H**有用：

- 创建混合语言或可移植程序时。

- 当您使用工具，从而限制了在外部标识符的长度。

- 当你想要限制在调试版本中使用符号的空间量。

下面的示例演示如何使用 **/H**如果标识符限制长度，则过多，实际上可能引入错误：

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

您还必须是使用时应谨慎 **/H**由于预定义的编译器的标识符选项。 如果最大标识符长度太小，某些预定义的标识符将无法解析，以及某些库函数调用。 例如，如果`printf`使用函数和选项 **/H5**指定在编译时，该符号 **_prin**将创建以引用`printf`，这将不会找到和在库中。

利用 **/H**与不兼容[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

**/H**自 Visual Studio 2005 选项已弃用; 已增加最大长度限制以及 **/H**不再需要。 有关不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入中的编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
