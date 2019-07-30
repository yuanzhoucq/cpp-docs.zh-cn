---
title: /Zc:wchar_t（wchar_t 是本机类型）
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 962bb2aaa2f05ad0dc4c9c86cd5cc9694cfad98b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446158"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t（wchar_t 是本机类型）

根据 C++ 标准将 `wchar_t` 分析为内置类型。

## <a name="syntax"></a>语法

> **/Zc:wchar_t**[ **-** ]

## <a name="remarks"></a>备注

如果 **/zc: wchar_t**为 on 时，`wchar_t`是编译为代码中的内置整型类型的关键字C++。 如果 **/zc: wchar_t-** （带有一个减号） 指定，或在代码中作为 C 编译，`wchar_t`不是内置类型。 相反，`wchar_t`指`typedef`为`unsigned short`规范标头 stddef.h 中。 （Microsoft 实现将其定义中包含通过 stddef.h 的另一个标头和其他标准标头。）

我们不建议 **/zc: wchar_t-** 由于C++标准要求`wchar_t`是内置类型。 使用 `typedef` 版本可能导致可移植性问题。 如果从 Visual Studio 的早期版本升级并遇到编译器错误[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)因为代码尝试将隐式转换`wchar_t`到`unsigned short`，我们建议更改代码以修复此错误，而不是设置 **/zc: wchar_t-** 。

**/Zc: wchar_t**选项在默认情况下位于C++编译，并且将忽略在 C 编译中。 [触发-](permissive-standards-conformance.md)选项不会影响 **/zc: wchar_t**。

Microsoft 将 `wchar_t` 作为两位无符号值实现。 它映射到特定于 Microsoft 的本机类型`__wchar_t`。 有关详细信息`wchar_t`，请参阅[数据类型范围](../../cpp/data-type-ranges.md)并[基本类型](../../cpp/fundamental-types-cpp.md)。

如果你编写新代码具有与仍使用较旧代码进行互操作`typedef`新版`wchar_t`，可以同时提供重载`unsigned short`和`__wchar_t`的变体`wchar_t`，以便你的代码可以与链接使用代码编译 **/zc: wchar_t**或如果没有该编译的代码。 否则，你必须提供两个不同版本的库、 一个具有和没有 **/zc: wchar_t**启用。 即使在这种情况下，仍建议你使用用来编译新代码的同一编译器来生成旧代码。 不要将使用不同编译器编译的二进制文件混合。

当 **/zc: wchar_t**指定，则 **\_WCHAR\_T\_定义**并 **\_本机\_WCHAR\_T\_定义** 定义了符号。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。

如果你的代码使用编译器 COM 全局函数，因为 **/zc: wchar_t**现在在默认情况下，我们建议您更改对 comsupp.lib 的显式引用 (从[注释杂注](../../preprocessor/comment-c-cpp.md)或在命令行） 到 comsuppw.lib 或 comsuppwd.lib。 (如果必须使用进行编译 **/zc: wchar_t-** ，使用 comsupp.lib。)如果你包含了 comdef.h 头文件，则会为你指定正确的库。 有关编译器 COM 支持的信息，请参阅[编译器 COM 支持](../../cpp/compiler-com-support.md)。

`wchar_t`编译 C 代码时不支持内置类型。 有关使用视觉对象的一致性问题的详细信息C++，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++**  > **语言**页。

1. 修改**将 wchar_t 视为内置类型**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
