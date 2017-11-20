---
title: "-std （指定语言标准版本） |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
dev_langs: C++
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d5397af7c83865d833b9a57a9baaf380aa207ca8
ms.sourcegitcommit: 78f3f8208d49b7c1d87f4240f4a1496b7c29333e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="std-specify-language-standard-version"></a>/std （指定语言标准版本）

启用支持从标准的 c + + 语言的指定版本的 c + + 语言功能。

## <a name="syntax"></a>语法

> /std: [c + + 14 | c + + 17 | 最新 c + +]

## <a name="remarks"></a>备注

**/Std**选项用于控制特定于版本的 ISO c + + 编程语言的代码的编译过程中启用的标准功能。 选择此选项可以禁用针对的某些新的语言和库功能，可能会中断现有代码的语言的特定版本符合标准的支持。 默认情况下， **/std:c + + 14**指定，则这将禁用语言和标准的 c + + 语言的更高版本中找到的标准库功能。 使用**/std:c + + 17**启用 C + + 17 标准特定功能和行为。 若要显式启用最新受支持的编译器和标准库功能，请使用**/std:c + + 最新**。

默认值**/std:c + + 14**选项启用 C + + 14 实现的功能由 Visual c + + 编译器的集。 编译器和标准库支持的更改的功能或新的语言标准，除了某些 C + + 17 功能已在以前版本的 Visual c + + 编译器中实现较高版本中，将禁用此选项。 为了避免破坏对已进行了依赖项从 Visual Studio 2015 Update 2 开始提供的功能的用户的更改，这些功能保持启用状态时**/std:c + + 14**指定选项：

- [针对自动使用大括号内的初始值设定项列表规则](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [模板-参数模板的类型名称](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [删除三字符组](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [命名空间和枚举器的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [u8 字符文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

有关其他信息的 C + + 14 和 C + + 17 功能启用时**/std:c + + 14**是指定，请参阅中的说明[Visual c + + 语言一致性](../../visual-cpp-language-conformance.md)。
  
**/Std:c + + 17**选项启用完整的 C + + 17 功能集由 Visual c + + 编译器实现。 此选项在 C + + 17 后禁用编译器和标准库支持的更改的功能或新的 c + + 标准的工作草案和缺陷更新版本中。  
  
**/Std:c + + 最新**选项启用 c + + 语言和库实现的功能由 Visual c + +，来最大跟踪组 C + + 20 的工作草案和缺陷最新更新的 c + + 标准不包括在 C + + 17 中。 使用此开关获取 post-支持的编译器和标准库的 C + + 17 语言功能。 有关受支持的语言和库功能的列表，请参阅[有关 Visual c + + 的新增](../../what-s-new-for-visual-cpp-in-visual-studio.md)。 **/Std:c + + 最新**选项不会启用功能受**/ 实验**切换。  
  
**/Std**实际上在 c + + 编译过程的选项可以通过使用检测到[ \_MSVC\_LANG](../../preprocessor/predefined-macros.md)预处理器宏。 有关详细信息，请参阅[预处理器宏](../../preprocessor/predefined-macros.md)。

**/Std:c + + 14**和**/std:c + + 最新**选项为 Visual c + + 2015 Update 3 中的开始提供。 **/Std:c + + 17**选项是 Visual c + + 2017 版本 15.3 中的开始提供。 如上所述，某些 C + + 17 标准行为通过**/std:c + + 14**选项，但所有其他 C + + 17 功能启用的**/std:c + + 17**。
  
> [!NOTE]
> 具体取决于 Visual c + + 编译器版本或更新级别某些 C + + 14 或 C + + 17 功能可能未完全实现或完全符合的指定时**/std:c + + 14**或**/std:c + + 17**选项。 例如，Visual c + + 2017 RTM 编译器不完全支持 C + + 14 一致`constexpr`，表达式 SFINAE 或 2 阶段名称查找。 发行版本的 Visual c + + 中的 c + + 语言一致性的概述，请参阅[Visual c + + 语言一致性](../../visual-cpp-language-conformance.md)。 
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**配置属性**， **C/c + +**，**语言**。  
  
3.  在**c + + 语言标准**，选择语言标准，以支持从下拉控件中，然后选择**确定**或**应用**以保存所做的更改。  
  
## <a name="see-also"></a>请参阅  
  
[编译器选项](../../build/reference/compiler-options.md)   
[设置编译器选项](../../build/reference/setting-compiler-options.md)   
