---
title: '/Zc: __cplusplus （启用更新的 __cplusplus 宏）'
ms.date: 05/30/2018
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 89545f541f32374a47dce7f87958e61873c1b47c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315711"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc: __cplusplus （启用更新的 __cplusplus 宏）

**/Zc: __cplusplus**编译器选项启用 **\_ \_cplusplus**预处理器宏来报告更新的值的最新C++语言标准的支持。 默认情况下，Visual Studio 始终为返回的值"199711 L"  **\_ \_cplusplus**预处理器宏。

## <a name="syntax"></a>语法

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>备注

 **\_ \_Cplusplus**预处理器宏通常用来将报表支持特定版本的C++标准。 许多现有代码看起来依赖于此宏匹配"199711 L"的值，因为编译器不会更改宏的值，除非显式选择在使用 **/zc: __cplusplus**编译器选项。 **/Zc: __cplusplus**选项在 Visual Studio 2017 版本 15.7，从开始提供，默认情况下处于关闭状态。 在早期版本的 Visual Studio 中，并且默认情况下，或者如果 **/Zc:__cplusplus-** 指定，则 Visual Studio 将返回"199711 L"的值为 **\_ \_cplusplus**预处理器宏。 [触发-](permissive-standards-conformance.md)选项不会启用 **/zc: __cplusplus**。

当 **/zc: __cplusplus**启用了选项，通过报告的值 **\_ \_cplusplus**宏依赖于[/std](std-specify-language-standard-version.md) version 开关设置。 此表显示了该宏的可能值：

|/Zc: __cplusplus 开关|/std:c++ 开关|__cplusplus value|
|-|-|-|
Zc:__cplusplus|/std: c + + 14 （默认值）|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus-（禁用）|任意值|199711L
未指定|任意值|199711L

编译器不支持 C + + 98、 C + + 03，或 C + + 11 标准交换机。

对于更精细地检测到编译器工具集的更改，使用[_MSC_VER](../../preprocessor/predefined-macros.md)预定义的宏。 此内置的宏的值是在 Visual Studio 2017 和更高版本中的每个工具集更新时增加。 [_MSVC_LANG](../../preprocessor/predefined-macros.md)预定义的宏报告标准版本是否 **/zc: __cplusplus**选项是启用还是禁用状态。 当 **/zc: __cplusplus**已启用， `__cplusplus == _MSVC_LANG`。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **命令行**属性页。

1. 添加 **/zc: __cplusplus**或 **/Zc:__cplusplus-** 到**附加选项：** 窗格。

## <a name="see-also"></a>请参阅

- [/Zc（一致性）](zc-conformance.md)
- [/std （指定语言标准版本）](std-specify-language-standard-version.md)
- [预定义的宏](../../preprocessor/predefined-macros.md)
