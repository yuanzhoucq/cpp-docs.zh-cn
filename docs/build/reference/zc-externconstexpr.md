---
title: '/Zc: externconstexpr （启用 extern constexpr 变量）'
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: 3c18a5310646ea39c0599f709e9fddc3990b7a2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315750"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc: externconstexpr （启用 extern constexpr 变量）

**/Zc: externconstexpr**编译器选项告知编译器为与C++标准，并允许的外部链接`constexpr`变量。 默认情况下，Visual Studio 始终都提供`constexpr`变量内部链接，即使您指定`extern`关键字。

## <a name="syntax"></a>语法

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>备注

**/Zc: externconstexpr**编译器选项将使编译器要应用于通过使用声明的变量的外部链接`extern constexpr`。 在早期版本的 Visual Studio 中，并且默认情况下或者如果 **/Zc:externConstexpr-** 指定，则 Visual Studio 将应用到的内部链接`constexpr`变量，即使`extern`使用关键字。 **/Zc: externconstexpr**选项是从开始在 Visual Studio 2017 更新 15.6 版中提供。 和默认情况下处于关闭状态。 [触发-](permissive-standards-conformance.md)选项不会启用 **/zc: externconstexpr**。

如果标头文件包含声明的变量`extern constexpr`，必须将标记[__declspec （selectany)](../../cpp/selectany.md)以便合并到链接的二进制文件中的单个实例的重复声明。 否则可能会看到链接器错误，例如，LNK2005 违反单个定义规则。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **命令行**属性页。

1. 添加 **/zc: externconstexpr**或 **/Zc:externConstexpr-** 到**附加选项：** 窗格。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[auto 关键字](../../cpp/auto-keyword.md)
