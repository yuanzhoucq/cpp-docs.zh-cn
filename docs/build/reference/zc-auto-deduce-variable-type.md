---
title: /Zc:auto（推导变量类型）
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: 866cccb490136e951effb1f8da20877c8d5ec763
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217176"
---
# <a name="zcauto-deduce-variable-type"></a>`/Zc:auto`（推导变量类型）

**`/Zc:auto`** 编译器选项告知编译器如何使用[ `auto` 关键字](../../cpp/auto-keyword.md)来声明变量。 如果指定默认选项， **`/Zc:auto`** 则编译器会从其初始化表达式中推导声明的变量的类型。 如果指定 **`/Zc:auto-`** ，则编译器会将该变量分配给自动存储类。

## <a name="syntax"></a>语法

> **`/Zc:auto`**[**`-`**]

## <a name="remarks"></a>备注

C + + 标准定义关键字的原始和修订的含义 **`auto`** 。 在 Visual Studio 2010 之前，关键字在自动存储类中声明变量;即具有本地生存期的变量。 从 Visual Studio 2010 开始，关键字推导声明的初始化表达式中的变量的类型。 使用 **`/Zc:auto`** 编译器选项告知编译器使用关键字的修订含义 **`auto`** 。 **`/Zc:auto`** 默认情况下，此选项处于启用状态。 [`/permissive-`](permissive-standards-conformance.md)选项不会更改的默认设置 **`/Zc:auto`** 。

如果使用 **`auto`** 关键字与当前编译器选项冲突，则编译器会发出适当的诊断消息 **`/Zc:auto`** 。 有关详细信息，请参阅[ `auto` 关键字](../../cpp/auto-keyword.md)。 有关 Visual C++ 的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 将 **`/Zc:auto`** 或添加 **`/Zc:auto-`** 到 "**附加选项：** " 窗格。

## <a name="see-also"></a>另请参阅

[`/Zc`度](zc-conformance.md)<br/>
[`auto`关键字](../../cpp/auto-keyword.md)
