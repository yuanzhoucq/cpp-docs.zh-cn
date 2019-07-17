---
title: /std（指定语言标准版本）
ms.date: 05/16/2019
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 9bdeb92e03b3ae00258ac48a29cec42ef7e18e81
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241210"
---
# <a name="std-specify-language-standard-version"></a>/std（指定语言标准版本）

从 C++ 语言标准的指定版本启用支持的 C++ 语言功能。

## <a name="syntax"></a>语法

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>备注

“/std”选项在 Visual Studio 2017 及更高版本中提供  。 它用于控制在编译代码期间启用的特定于版本的 ISO C++ 编程语言标准功能。 此选项可禁用对某些新语言和库功能的支持，这些功能可能会破坏符合特定语言标准版本的现有代码。 默认情况下，指定了“/std:c++14”，这将禁用更高版本 C++ 语言标准中的语言和标准库功能  。 使用“/std:c++17”启用 C++17 标准特定的功能和行为  。 若要显式启用当前实施的编译器和为下一个草案标准建议的标准库功能，请使用“/std:c++latest”  。 所有 C + + 个 20 功能都需要 **/std: c + + 最新**; 实现完成后，新 **/std: c + + 20**选项将启用。

默认的“/std:c++14”选项启用由 MSVC 编译器实现的 C++14 功能集  。 此选项禁用更新版语言标准中更改或新增功能的编译器和标准库支持，已在 MSVC 编译器的以前版本中实现的一些 C++17 功能除外。 为避免对已经依赖 Visual Studio 2015 Update 2 中可用功能的用户进行中断性更改，在指定“/std:c++14”选项时，这些功能仍保持启用状态  ：

- [针对自动使用大括号内的初始值设定项列表的规则](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [模板-参数模板的类型名称](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [删除三字符组](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [命名空间和枚举器的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [u8 字符文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

有关在指定“/std:c++14”时启用哪些 C++14 和 C++17 功能的其他信息，请参阅 [Visual C++ 语言一致性](../../overview/visual-cpp-language-conformance.md)中的注释  。

“/std:c++17”选项启用 MSVC 编译器实现的整组 C++17 功能  。 对于在 C++17 之后的工作草案版本及 C++ 标准版缺陷更新中更改或新增的功能，此选项会禁用编译器和标准库支持。

“/std:c++latest”选项启用编译器和库中当前实现的 post-C++17 语言和库功能  。 这些可能包括 C++20 工作草案中的功能和 C++17 中未包含的 C++ 标准的缺陷更新，以及草案标准的实验建议。 有关支持的语言和库功能列表，请参阅 [Visual C++ 的新增功能](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md)。 “/std:c++latest”选项不启用由“/experimental”开关保护的功能，但可能需要启用它们   。

> [!IMPORTANT]
> 由“/std:c++latest”启用的编译器和库功能代表了未来 C++ 标准中可能出现的功能，以及已批准的 C++20 功能  。 未经批准的功能可能会在不经通知的情况下进行中断性变更或删除，并按原样提供。 

可以使用 [\_MSVC\_LANG](../../preprocessor/predefined-macros.md) 预处理器宏来检测在 C++ 编译期间有效的“/std”选项  。 有关详细信息，请参阅 [预处理器宏](../../preprocessor/predefined-macros.md)。

从 Visual Studio 2015 Update 3 开始，可以使用“/std:c++14”和“/std:c++latest”选项   。 从 Visual Studio 2017 15.3 版开始，可以使用“/std:c++17”选项  。 如上所述，“/std:c++14”选项启用某些 C++17 标准行为，而“/std:c++17”启用所有其他 C++17 功能   。 “/std:latest”启用 C++20 功能，直到实现完成  。

> [!NOTE]
> 根据 MSVC 编译器版本或更新级别，当指定“/std:c++17”选项时，C++17 功能可能无法完全实现或完全符合  。 有关 Visual C++ 中 C++ 语言一致性（按发布版本）的概述，请参阅 [Visual C++ 语言一致性](../../overview/visual-cpp-language-conformance.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 依次选择“配置属性”、“C/C++”和“语言”    。

1. 在“C++ 语言标准”中，从下拉控件中选择要支持的语言标准，然后选择“确定”或“应用”以保存更改    。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
