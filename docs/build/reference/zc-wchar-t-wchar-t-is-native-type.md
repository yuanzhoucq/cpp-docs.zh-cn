---
title: "/Zc: wchar_t （wchar_t 是本机类型） |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4970e4aba8bf2d6aebf60f876a4770b18943781
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t（wchar_t 是本机类型）

根据 C++ 标准将 `wchar_t` 分析为内置类型。

## <a name="syntax"></a>语法

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>备注

如果**/zc: wchar_t**处于打开状态，`wchar_t`是内置的整数类型在编译为 c + + 代码的关键字。 如果**/Zc:wchar_t-** （带有一个减号） 指定，或在代码中作为 C 编译，`wchar_t`不是内置类型。 相反，`wchar_t`定义为`typedef`为`unsigned short`规范标头 stddef.h 中。 （Microsoft 实现其定义包含在 stddef.h 包含的另一个标头和其他标准标头中。）

我们不建议**/Zc:wchar_t-**因为 c + + 标准要求`wchar_t`是内置类型。 使用 `typedef` 版本可能导致可移植性问题。 如果你从 Visual c + + 的早期版本升级并遇到编译器错误[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)因为代码尝试将隐式转换`wchar_t`到`unsigned short`，我们建议你更改代码以改为修复此错误，设置的**/Zc:wchar_t-**。

**/Zc: wchar_t**选项位于默认情况下，在 c + + 编译中，且在 C 编译中忽略。 [/ 宽松-](permissive-standards-conformance.md)选项不影响**/zc: wchar_t**。

Microsoft 将 `wchar_t` 作为两位无符号值实现。 它映射到的 Microsoft 专用本机类型`__wchar_t`。 有关详细信息`wchar_t`，请参阅[数据类型范围](../../cpp/data-type-ranges.md)和[基本类型](../../cpp/fundamental-types-cpp.md)。

如果你编写新代码具有与较旧仍将使用的代码进行互操作`typedef`版本`wchar_t`，你可以同时提供重载`unsigned short`和`__wchar_t`变体`wchar_t`，以便可以与链接你的代码使用代码编译**/zc: wchar_t**或如果没有该编译的代码。 否则，你必须提供两个不同版本的库、 一个具有和没有**/zc: wchar_t**启用。 即使在这种情况下，仍建议你使用用来编译新代码的同一编译器来生成旧代码。 不要将使用不同编译器编译的二进制文件混合。

当**/zc: wchar_t**指定，则 **\_WCHAR\_T\_定义**和**\_本机\_WCHAR\_T\_定义**定义了符号。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。

如果你的代码使用编译器 COM 全局函数，因为**/zc: wchar_t**现在在默认情况下，我们建议你更改对 comsupp.lib 的显式引用 (从[注释杂注](../../preprocessor/comment-c-cpp.md)或在命令行） 为对 comsuppw.lib 或 comsuppwd.lib。 (如果必须使用编译**/Zc:wchar_t-**，使用 comsupp.lib。)如果你包含了 comdef.h 头文件，则会为你指定正确的库。 有关编译器 COM 支持的信息，请参阅[编译器 COM 支持](../../cpp/compiler-com-support.md)。

`wchar_t`编译 C 代码时不支持内置类型。 有关使用 Visual c + + 一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **语言**页。

1. 修改**wchar_t 视为内置类型**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
