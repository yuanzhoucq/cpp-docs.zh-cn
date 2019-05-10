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
ms.openlocfilehash: 9609bc484310fbc9999182add384eb4e438378bf
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446241"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto（推导变量类型）

**/Zc: auto [-]** 编译器选项告知编译器如何使用[auto 关键字](../../cpp/auto-keyword.md)声明变量。 如果指定默认选项 **/zc: auto**，编译器会从其初始化表达式声明的变量的类型推导。 如果指定 **/Zc:auto-**，编译器将变量分配给自动存储类。

## <a name="syntax"></a>语法

> **/Zc:auto**[**-**]

## <a name="remarks"></a>备注

C++ 标准为 `auto` 关键字定义了初始和修订的含义。 在 Visual Studio 2010 之前的关键字声明自动存储类; 中的变量也就是说，变量的具有本地生存期。 从 Visual Studio 2010 开始，关键字将推导声明的初始化表达式中的某个变量的类型。 使用 **/zc: auto [-]** 编译器选项，以告知编译器要使用的初始或修订的含义`auto`关键字。 **/Zc: auto**选项默认为打开。 [触发-](permissive-standards-conformance.md)选项不会更改的默认设置 **/zc: auto**。

如果编译器将发出适当的诊断消息的使用`auto`关键字，这不符合当前 **/zc: auto**编译器选项。 有关详细信息，请参阅[auto 关键字](../../cpp/auto-keyword.md)。 有关使用视觉对象的一致性问题的详细信息C++，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **命令行**属性页。

1. 添加 **/zc: auto**或 **/Zc:auto-** 到**附加选项：** 窗格。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[auto 关键字](../../cpp/auto-keyword.md)
