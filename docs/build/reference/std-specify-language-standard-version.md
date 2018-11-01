---
title: /std （指定语言标准版本）
ms.date: 11/16/2017
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 28796826a7c312b92b3ec0510513ad4804800ca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476032"
---
# <a name="std-specify-language-standard-version"></a>/std （指定语言标准版本）

启用支持从指定版本的 c + + 语言标准 c + + 语言功能。

## <a name="syntax"></a>语法

> /std: [c + + 14 | c + + 17 | 最新 c + +]

## <a name="remarks"></a>备注

**/Std**选项是可用在 Visual Studio 2017 及更高版本。 它用于控制特定于版本的 ISO c + + 编程语言标准功能在你的代码的编译过程中启用。 此选项可以禁用的某些新的语言和库功能可能会中断现有代码符合特定版本的语言标准的支持。 默认情况下 **/std: c + + 14**指定时，它表示禁用语言和标准库中提供功能更高版本的 c + + 语言标准。 使用 **/std: c + + 17**启用 C + + 17 标准特定功能和行为。 若要显式启用最新受支持的编译器和标准库功能，请使用 **/std: c + + 最新**。

默认值 **/std: c + + 14**选项启用 C + + 14 功能由 Visual c + + 编译器实现的集。 此选项将禁用编译器和标准库支持的功能的更改或新的较新版本的标准，除了某些 c++17 功能已在以前版本的 Visual c + + 编译器中实现的语言中。 若要避免重大更改的用户已采用了从 Visual Studio 2015 Update 2 开始提供功能的依赖关系，这些功能保持启用状态时 **/std: c + + 14**指定选项：

- [针对自动使用大括号内的初始化列表规则](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [模板-参数模板中的 typename](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [删除三字符组](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [命名空间和枚举器的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [u8 字符文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

有关其他信息的 C + + 14 和 C + + 17 功能启用时 **/std: c + + 14**是指定，请参阅中的说明[Visual c + + 语言一致性](../../visual-cpp-language-conformance.md)。

**/Std: c + + 17**选项启用完整的 C + + 17 功能集由 Visual c + + 编译器实现。 对于在 C++17 之后的工作草案版本及 C++ 标准版缺陷更新中更改或新增的功能，此选项会禁用编译器和标准库支持。

**/Std: c + + 最新**选项使实现一组 c + + 语言和库功能由 Visual c + + 来跟踪最新 C + + 20 工作草案和缺陷更新的 c + + 标准不包括在 C + + 17 中。 使用此开关获取发布-支持的编译器和标准库的 C + + 17 语言功能。 有关受支持的语言和库功能的列表，请参阅[What's New for Visual c + +](../../what-s-new-for-visual-cpp-in-visual-studio.md)。 **/Std: c + + 最新**选项不会启用功能受 **/ 实验性**切换。

**/Std**可以通过使用检测选项实际上在 c + + 编译期间[ \_MSVC\_LANG](../../preprocessor/predefined-macros.md)预处理器宏。 有关详细信息，请参阅[预处理器宏](../../preprocessor/predefined-macros.md)。

**/Std: c + + 14**并 **/std: c + + 最新**选项是在 Visual c + + 2015 Update 3 开始提供。 **/Std: c + + 17**选项是在 Visual c + + 2017 版本 15.3 开始提供。 如上所述，某些 c++17 标准情况下启用行为 **/std: c + + 14**选项，但所有其他 C + + 17 功能情况下会启用 **/std: c + + 17**。

> [!NOTE]
> 具体取决于 Visual c + + 编译器版本或更新级别，某些 C + + 14 或 C + + 17 功能可能未完全实现或完全符合的指定时 **/std: c + + 14**或 **/std: c + + 17**选项。 例如，Visual c + + 2017 RTM 编译器不完全支持 C + + 14 符合`constexpr`，表达式 SFINAE 或 2 阶段名称查找。 Visual c + + 中的发行版的 c + + 语言一致性的概述，请参阅[Visual c + + 语言一致性](../../visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性**， **C/c + +**，**语言**。

1. 在中**c + + 语言标准**，选择语言标准，以支持从下拉列表控件，然后选择**确定**或**应用**以保存所做的更改。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
