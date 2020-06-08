---
title: /std（指定语言标准版本）
ms.date: 06/04/2020
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: ddb0fc9ad4880ed317a28d7aec5eba1669eabbc5
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507061"
---
# <a name="std-specify-language-standard-version"></a>/std（指定语言标准版本）

从 C++ 语言标准的指定版本启用支持的 C++ 语言功能。

## <a name="syntax"></a>语法

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**]

## <a name="remarks"></a>注解

此 **`/std`** 选项在 Visual Studio 2017 和更高版本中可用。 它用于控制在代码编译期间启用的特定于版本的 ISO c + + 编程语言标准功能。 此选项允许你禁用对某些新语言和库功能的支持：可能会破坏符合特定语言标准版本的现有代码的支持。 默认情况下， **`/std:c++14`** 指定，这将禁用在更高版本的 c + + 语言标准中找到的语言和标准库功能。 使用 **`/std:c++17`** 启用 c + + 17 标准特定功能和行为。 若要显式启用当前实现的编译器和标准库功能建议用于下一草案标准，请使用 **`/std:c++latest`** 。 所有 c + + 20 功能都需要 **`/std:c++latest`** ; 实现完成后， **`/std:c++20`** 将启用一个新选项。

默认 **`/std:c++14`** 选项启用由 MSVC 编译器实现的 c + + 14 功能集。 此选项将禁用编译器和标准库支持，以对在较新版本的语言标准中更改或新增的功能禁用该功能。 它不会禁用先前版本的 MSVC 编译器已经实现的 c + + 17 功能。 若要避免对已对 Visual Studio 2015 Update 2 之前或之前的功能具有依赖关系的用户进行重大更改，则在指定选项时，这些功能仍保持启用状态 **`/std:c++14`** ：

- [针对自动使用大括号内的初始值设定项列表的规则](https://wg21.link/n3922)

- [模板-参数模板的类型名称](https://wg21.link/n4051)

- [删除三字符组](https://wg21.link/n4086)

- [命名空间和枚举器的属性](https://wg21.link/n4266)

- [u8 字符文本](https://wg21.link/n4267)

当你指定可用时，将启用哪一列表 c + + 14 和 c + + 17 功能 **`/std:c++14`** 。 有关详细信息，请参阅[Microsoft c + + 语言一致性表](../../overview/visual-cpp-language-conformance.md)中的说明。

**`/std:c++17`** 选项启用 MSVC 编译器实现的一组完整的 c + + 17 功能。 此选项对 c + + 17 之后新增或更改的功能禁用编译器和标准库支持。 这包括 c + + 标准的工作草稿和缺陷更新版本中的 C + + 17 更改。

**`/std:c++latest`** 选项可启用当前在编译器和库中实现的 C + + 17 语言和库功能。 这些功能可能包括 c + + 20 个工作草案的更改、c + + 17 中未包含的缺陷更新以及草案标准的实验性提议。 有关支持的语言和库功能列表，请参阅 [Visual C++ 的新增功能](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md)。 **`/std:c++latest`** 选项不会启用交换机保护的功能 **`/experimental`** ，但可能需要启用它们。

> [!IMPORTANT]
> 启用的编译器和库功能 **`/std:c++latest`** 表示可能出现在将来的 c + + 标准中的功能，以及已批准的 c + + 20 功能。 未经批准的功能可能会在不经通知的情况下进行中断性变更或删除，并按原样提供。

**`/std`** 可以通过使用[ \_ MSVC \_ LANG](../../preprocessor/predefined-macros.md)预处理器宏来检测 c + + 编译过程中有效的选项。 有关详细信息，请参阅 [预处理器宏](../../preprocessor/predefined-macros.md)。

**`/std:c++14`** **`/std:c++latest`** 从 Visual Studio 2015 Update 3 开始提供和选项。 **`/std:c++17`** 从 Visual Studio 2017 版本15.3 开始，可以使用选项。 如上所述，某些 c + + 17 标准行为是通过选项启用的 **`/std:c++14`** ，但所有其他 c + + 17 功能都是通过启用的 **`/std:c++17`** 。 在实现完成之前，c + + 20 功能处于启用状态 **`/std:c++latest`** 。

> [!NOTE]
> 根据 MSVC 编译器版本或更新级别，在指定选项时，c + + 17 功能可能未完全实现或完全一致 **`/std:c++17`** 。 有关 Visual C++ 中的 c + + 语言一致性概述，请参阅[Microsoft c + + 语言一致性表](../../overview/visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 依次选择“配置属性”、“C/C++”和“语言”************。

1. 在“C++ 语言标准”中，从下拉控件中选择要支持的语言标准，然后选择“确定”或“应用”以保存更改************。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
