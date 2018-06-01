---
title: /Zc:__cplusplus （启用更新的 __cplusplus 宏）
ms.custom: ''
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:__cplusplus
dev_langs:
- C++
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a796794c0086b09c15ee88442e0fea4d1b114d98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705708"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus （启用更新的 __cplusplus 宏）

**/Zc:__cplusplus**编译器选项启用 **\_ \_cplusplus**预处理器宏来报告新的 c + + 语言标准支持的更新的值。 默认情况下，Visual Studio 始终返回值"199711 L"  **\_ \_cplusplus**预处理器宏。

## <a name="syntax"></a>语法

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>备注

**\_ \_Cplusplus**预处理器宏通常用于向报表支持 c + + 标准的特定版本。 由于大量现有代码看起来取决于匹配"199711 L"此宏的值，编译器不会更改宏的值，除非您显式选择在使用 **/Zc:__cplusplus**编译器选项。 **/Zc:__cplusplus**选项是从 Visual Studio 2017 版本 15.7，并且默认情况下处于关闭状态。 在早期版本的 Visual Studio 中，并且默认情况下，或者如果 **/Zc:__cplusplus-** ，Visual Studio 返回"199711 L"的值为指定 **\_ \_cplusplus**预处理器宏。 [/ 宽松-](permissive-standards-conformance.md)选项不会启用 **/Zc:__cplusplus**。

当 **/Zc:__cplusplus**启用选项，通过报告的值 **\_ \_cplusplus**宏依赖于[/std](std-specify-language-standard-version.md)版本交换机设置。 下表显示宏的可能值：

|/Zc:__cplusplus 交换机|/std:c++ 交换机|__cplusplus 值|
|-|-|-|
Zc:__cplusplus|/std:c + + 14 （默认值）|201402 L
Zc:__cplusplus|/std:c + + 17|201703 L
Zc:__cplusplus|/std:c + + 最新|201704 L
Zc:__cplusplus-（禁用）|任意值|199711 L
未指定|任意值|199711 L

编译器不支持 C + + 98、 C + + 03 中，或 C + + 11 标准交换机。

对于更细粒度的编译器工具集更改检测，使用[_MSC_VER](../../preprocessor/predefined-macros.md)预定义的宏。 在 Visual Studio 2017 和更高版本中的每个工具集更新的情况下，此内置的宏的值会增加数值。 [_MSVC_LANG](../../preprocessor/predefined-macros.md)预定的义宏报告的标准版本是否 **/Zc:__cplusplus**选项是启用还是禁用。 当 **/Zc:__cplusplus**启用，则`__cplusplus == _MSVC_LANG`。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 添加 **/Zc:__cplusplus**或 **/Zc:__cplusplus-** 到**其他选项：** 窗格。

## <a name="see-also"></a>请参阅

- [/Zc（一致性）](zc-conformance.md)
- [/std （标准的指定语言的版本）](std-specify-language-standard-version.md)
- [预定义的宏](../../preprocessor/predefined-macros.md)
