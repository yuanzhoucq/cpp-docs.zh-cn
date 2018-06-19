---
title: '/Zc: trigraphs （trigraphs 替换） |Microsoft 文档'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e465b62944b360d6fdb09da1230f3353658437b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379866"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs（Trigraphs 替换）

当 **/zc: trigraphs**指定，编译器将通过使用相应的标点字符来替换三元组字符序列。

## <a name="syntax"></a>语法

> **/Zc:trigraphs**[**-**]  

## <a name="remarks"></a>备注

A*三元组*包含两个连续问号 ("??") 跟一个唯一的第三个字符。 标准的 C 语言支持使用不包含某些标点字符的方便图形表示形式的字符集的源文件三元组。 例如，启用三字符组后，编译器将取代"??="使用 '#' 字符三元组。 通过 C + + 14 中，三元组支持如下所示 c。从 c + + 语言，C + + 17 标准中删除三字符组。 在 c + + 代码中， **/zc: trigraphs**编译器选项将替换为三元组序列通过相应的标点字符。 **/Zc:trigraphs-** 禁用三元组替换。

**/Zc: trigraphs**选项默认情况下，处于关闭状态和选项不是受影响时[/ 宽松-](permissive-standards-conformance.md)指定选项。

C/c + + 三字符组和的示例，演示如何使用三字符组的列表，请参阅[三元组](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: trigraphs**或 **/Zc:trigraphs-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
[三字符组](../../c-language/trigraphs.md)<br/>
