---
title: /Zc:trigraphs（Trigraphs 替换）
ms.date: 03/06/2018
f1_keywords:
- /Zc
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 7a20123603030dfe719cd8990018f795df137981
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315997"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs（Trigraphs 替换）

当 **/zc: trigraphs**指定，则编译器将三元组字符序列替换使用相应的标点字符。

## <a name="syntax"></a>语法

> **/Zc:trigraphs**[**-**]

## <a name="remarks"></a>备注

一个*三元组*包含两个连续的问号 ("??") 后接唯一的第三个字符。 C 语言标准支持使用不包含某些标点字符的方便图形表示形式的字符集的源代码文件的三字符组。 例如，当启用三元组时，编译器会将"??="使用 '#' 字符三元组。 通过 C + + 14，三元祖支持如下所示 c。C + + 17 标准删除三字符组从C++语言。 在C++代码中， **/zc: trigraphs**编译器选项启用三元组序列替换由相应的标点字符。 **/Zc:trigraphs-** 禁用三元组替换。

**/Zc: trigraphs**选项默认情况下处于关闭状态，该选项将不会受到影响时[触发的](permissive-standards-conformance.md)指定选项。

有关 C 的列表 /C++三元组和的示例，演示如何使用三字符组，请参阅[三元祖](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: trigraphs**或 **/Zc:trigraphs-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[三字符组](../../c-language/trigraphs.md)<br/>
