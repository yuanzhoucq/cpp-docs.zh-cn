---
title: /experimental： module （启用模块支持）
description: 使用/experimental： module 编译器选项可为模块启用实验编译器支持。
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 82cce127ad5a2f87d11e4a653035bd80ea9f5001
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294454"
---
# <a name="experimentalmodule-enable-module-support"></a>/experimental： module （启用模块支持）

启用对模块的实验性编译器支持，如草案 c + + 20 标准所指定。

## <a name="syntax"></a>语法

> **/experimental： module**[ **-** ]

## <a name="remarks"></a>备注

可以通过使用 **/experimental： module**编译器选项和[/std： c + + 最新](std-specify-language-standard-version.md)选项，启用实验性模块支持。 您可以使用 **/experimental： module-** 显式禁用模块支持。

从 Visual Studio 2015 Update 1 开始提供此选项。 从 Visual Studio 2019 版本16.2，草稿 c + + 20 标准模块未在 Microsoft C++编译器中完全实现。 你可以使用模块功能创建单分区模块，并导入 Microsoft 提供的标准库模块。 模块和使用它的代码必须使用相同的编译器选项编译。

有关模块以及如何使用和创建模块的详细信息，请参阅[中C++模块概述](../../cpp/modules-cpp.md)。

下面是一个编译器命令行选项示例，用于从源文件*ixx*创建导出模块：

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 将**配置**下拉箭头设置为 "**所有配置**"。

1. 选择 "**配置属性** > " " > **C/C++** **语言**" 属性页。

1. 修改 "**启用C++模块（实验）** " 属性，然后选择 **"确定"** 。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)
