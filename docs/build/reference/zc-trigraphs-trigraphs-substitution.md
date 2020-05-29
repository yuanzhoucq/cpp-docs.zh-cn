---
title: /Zc:trigraphs（Trigraphs 替换）
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438653"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs（Trigraphs 替换）

指定 **/zc： trigraphs**时，编译器将使用相应的标点字符来替换三元组字符序列。

## <a name="syntax"></a>语法

> **/Zc： trigraphs**[ **-** ]

## <a name="remarks"></a>备注

*三元组*由两个连续的问号（"？："）后跟唯一的第三个字符组成。 C 语言标准支持 trigraphs 对于使用不包含某些标点字符的方便图形表示形式的字符集的源文件。 例如，启用 trigraphs 时，编译器会将 "？= "三元组，使用" # "字符。 通过 c + + 14，trigraphs 支持，如 C 中所示。C + + 17 标准从C++语言中删除 trigraphs。 在C++代码中， **/zc： trigraphs**编译器选项允许将三元组序列替换为相应的标点字符。 **/Zc： trigraphs-** 禁用三元组替换。

默认情况下， **/zc： trigraphs**选项处于关闭状态，并且当指定[/permissive-](permissive-standards-conformance.md)选项时，此选项不受影响。

有关 C/C++ trigraphs 的列表以及演示如何使用 trigraphs 的示例，请参阅[trigraphs](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” **“C/C++”** “命令行”属性页 >  > 。

1. 修改 "**附加选项**" 属性以包括 **/zc： trigraphs**或 **/zc： Trigraphs** ，然后选择 **"确定"** 。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[三字符组](../../c-language/trigraphs.md)<br/>
