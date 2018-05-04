---
title: '-Zc: auto （推导变量类型） |Microsoft 文档'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caa64f64b75145c850c6f6393570dc3f9ba0b0d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto（推导变量类型）

**/Zc: auto [-]** 编译器选项指示编译器如何使用[auto 关键字](../../cpp/auto-keyword.md)来声明变量。 如果指定默认选项， **/zc: auto**，编译器会将从其初始化表达式声明的变量的类型推导。 如果指定 **/Zc:auto-**，编译器会将分配到自动存储类变量。

## <a name="syntax"></a>语法

> **/Zc:auto**[**-**]  

## <a name="remarks"></a>备注

C++ 标准为 `auto` 关键字定义了初始和修订的含义。 之前[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，关键字声明自动存储类中的变量; 也就是说，一个变量，具有本地生存期。 从开始[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，关键字中推导声明的初始化表达式中的某个变量的类型。 使用 **/zc: auto [-]** 编译器选项，以告知编译器要使用的原始或修订的含义`auto`关键字。 **/Zc: auto**选项默认处于启用。 [/ 宽松-](permissive-standards-conformance.md)选项不会更改的默认设置 **/zc: auto**。

编译器会发出适当的诊断消息，如果你使用`auto`关键字，这不符合当前 **/zc: auto**编译器选项。 有关详细信息，请参阅[auto 关键字](../../cpp/auto-keyword.md)。 有关使用 Visual c + + 一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 添加 **/zc: auto**或 **/Zc:auto-** 到**其他选项：**窗格。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
[auto 关键字](../../cpp/auto-keyword.md)
