---
title: /experimental：预处理器（启用预处理器一致性模式）
description: 使用/experimental：预处理器编译器选项启用标准相容预处理器的实验性编译器支持。
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754039"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental：预处理器（启用预处理器一致性模式）

使用此选项，可使基于令牌的实验性预处理器更严格符合 c + + 11 标准，包括 C99 预处理器功能。 有关详细信息，请参阅[MSVC 实验预处理器概述](../../preprocessor/preprocessor-experimental-overview.md)。

## <a name="syntax"></a>语法

> **/experimental：预处理器**[ **-** ]

## <a name="remarks"></a>备注

使用 **/experimental：预处理器**编译器选项可以启用试验性相容预处理器。 可以使用 **/experimental：预处理器-** 选项显式指定传统预处理器。

从 Visual Studio 2017 版本15.8 开始，可以使用 **/experimental：预处理器**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 修改 "**附加选项**" 属性以包含 **/experimental：预处理器**，然后选择 **"确定"** 。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)
