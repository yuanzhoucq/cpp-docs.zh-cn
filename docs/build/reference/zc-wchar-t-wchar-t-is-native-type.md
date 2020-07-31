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
ms.openlocfilehash: 114ed4a279b66571c0dc81fc1139dcdc59c17eae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234310"
---
# <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t（wchar_t 是本机类型）

**`wchar_t`** 根据 c + + 标准分析为内置类型。

## <a name="syntax"></a>语法

> **/Zc： wchar_t**[ **-** ]

## <a name="remarks"></a>备注

如果 **/zc： wchar_t**为 on， **`wchar_t`** 则为编译为 c + + 的代码中的内置整型类型的关键字。 如果 **/zc： wchar_t** （带有减号的），或在编译为 C 的代码中， **`wchar_t`** 则不是内置类型。 相反， **`wchar_t`** **`typedef`** **`unsigned short`** 在规范标头 stddef.h 中将定义为 for。 （Microsoft 实现在 stddef.h 和其他标准标头包含的另一个标头中定义它。）

不建议使用 **/zc： wchar_t-** 因为 c + + 标准要求 **`wchar_t`** 是内置类型。 使用此 **`typedef`** 版本可能导致可移植性问题。 如果从 Visual Studio 的早期版本升级并遇到编译器错误[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) ，因为代码尝试将隐式转换 **`wchar_t`** 为，所以 **`unsigned short`** 建议你更改代码以修复错误，而不是设置 **/zc： wchar_t-**。

默认情况下， **/zc： wchar_t**选项是在 c + + 编译中启用的，并且在 c 编译中将被忽略。 [/Permissive-](permissive-standards-conformance.md)选项不影响 **/zc： wchar_t**。

Microsoft 实现 **`wchar_t`** 为一个2字节无符号值。 它映射到特定于 Microsoft 的本机类型 **`__wchar_t`** 。 有关的详细信息 **`wchar_t`** ，请参阅[数据类型范围](../../cpp/data-type-ranges.md)和[基本类型](../../cpp/fundamental-types-cpp.md)。

如果编写的新代码必须与仍然使用版本的早期代码进行互操作 **`typedef`** **`wchar_t`** ，则可以提供的 **`unsigned short`** 和 **`__wchar_t`** 变体的重载 **`wchar_t`** ，以便可以将代码与使用 **/zc： wchar_t**编译的代码进行链接，或在不使用它的情况下编译代码。 否则，你必须提供两个不同的库版本，一个用于，一个没有 **/zc： wchar_t**启用。 即使在这种情况下，仍建议你使用用来编译新代码的同一编译器来生成旧代码。 不要将使用不同编译器编译的二进制文件混合。

指定 **/zc： wchar_t**时，将定义** \_ wchar \_ t \_ **定义的和** \_ 本机 \_ wchar \_ t \_ 定义**的符号。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。

如果你的代码使用编译器 COM 全局函数，因为 **/zc： wchar_t**现在默认处于启用状态，所以建议你将对 comsupp.lib 的显式引用（从[注释杂注](../../preprocessor/comment-c-cpp.md)或命令行）更改为 comsuppw.lib 或 comsuppwd.lib。 （如果必须使用 **/zc： wchar_t**进行编译，请使用 comsupp.lib。）如果包含 comdef.h 头文件，则会为你指定正确的库。 有关编译器 COM 支持的详细信息，请参阅[编译器 Com 支持](../../cpp/compiler-com-support.md)。

**`wchar_t`** 编译 C 代码时，不支持内置类型。 有关 Visual C++ 的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **语言**" 页。

1. 修改 "将**Wchar_t 视为内置类型**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
