---
title: /std （指定语言标准版本）
ms.date: 11/26/2018
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 32c63240f578b6170ae351cdf0cd1628167464b6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779737"
---
# <a name="std-specify-language-standard-version"></a>/std （指定语言标准版本）

启用支持C++中的指定版本的语言功能C++语言标准。

## <a name="syntax"></a>语法

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>备注

**/Std**选项是可用在 Visual Studio 2017 及更高版本。 它用来控制特定于版本的 ISOC++编程语言标准功能在你的代码的编译过程中启用。 此选项可以禁用的某些新的语言和库功能可能会中断现有代码符合特定版本的语言标准的支持。 默认情况下 **/std: c + + 14**指定时，它表示禁用语言和标准库功能的更高版本中找到C++语言标准。 使用 **/std: c + + 17**启用 C + + 17 标准特定功能和行为。 若要显式启用的当前实现中编译器和标准库功能为下一步的标准草案建议，请使用 **/std: c + + 最新**。

默认值 **/std: c + + 14**选项启用 C + + 14 实现的功能由 MSVC 编译器的集。 此选项将禁用编译器和标准库支持的功能的更改或新的较新版本的标准，除了一些 C + + 17 实现的功能已在以前版本的 MSVC 编译器的语言中。 若要避免重大更改的用户已采用了从 Visual Studio 2015 Update 2 开始提供功能的依赖关系，这些功能保持启用状态时 **/std: c + + 14**指定选项：

- [针对自动使用大括号内的初始化列表规则](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [模板-参数模板中的 typename](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [删除三字符组](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [命名空间和枚举器的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [u8 字符文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

有关其他信息的 C + + 14 和 C + + 17 功能启用时 **/std: c + + 14**是指定，请参阅中的说明[VisualC++语言一致性](../../overview/visual-cpp-language-conformance.md)。

**/Std: c + + 17**选项启用 C + + 17 功能实现的 MSVC 编译器的完整集。 对于在 C++17 之后的工作草案版本及 C++ 标准版缺陷更新中更改或新增的功能，此选项会禁用编译器和标准库支持。

**/Std: c + + 最新**选项启用 post-C + + 17 中编译器和库当前实现的语言和库功能。 其中可能包括从 C + + 20 工作草案和缺陷更新的功能C++C + + 17，以及实验的征求建议书草稿标准中未包括的标准。 有关受支持的语言和库功能的列表，请参阅[What's New for Visual C++ ](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md)。 **/Std: c + + 最新**选项不会启用功能受 **/ 实验性**开关，但可能需要启用它们。

> [!IMPORTANT]
> 启用的编译器和库功能 **/std: c + + 最新**作为提供的是并不支持。 它们可能进行重大更改或删除，恕不另行通知。 这些信息旨在以标准的下一版本中可能会显示的语言功能的预览版的形式，但标准是正在进行的工作。 使用 **/std: c + + 17**若要使用最新的 ISO 中的功能C++标准。

**/Std**期间有效选项C++可以通过使用检测到编译[ \_MSVC\_LANG](../../preprocessor/predefined-macros.md)预处理器宏。 有关详细信息，请参阅[预处理器宏](../../preprocessor/predefined-macros.md)。

**/Std: c + + 14**并 **/std: c + + 最新**选项为视觉对象中的开始提供C++2015年更新 3。 **/Std: c + + 17**选项是视觉对象中的开始提供C++2017年版本 15.3。 如上所述，某些 c++17 标准情况下启用行为 **/std: c + + 14**选项，但所有其他 C + + 17 功能情况下会启用 **/std: c + + 17**。

> [!NOTE]
> 根据 MSVC 编译器版本或更新级别，某些 C + + 14 或 C + + 17 功能可能未完全实现或完全符合的指定时 **/std: c + + 14**或 **/std: c + + 17**选项。 例如，视觉对象C++2017 RTM 编译器不完全支持 C + + 符合的 14 `constexpr`，表达式 SFINAE 或 2 阶段名称查找。 有关的概述C++视觉对象中的语言一致性C++的发行版本中，请参阅[VisualC++语言一致性](../../overview/visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性**， **C /C++**，**语言**。

1. 在中**C++语言标准**，选择语言标准，以支持从下拉列表控件，然后选择**确定**或**应用**以保存所做的更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
