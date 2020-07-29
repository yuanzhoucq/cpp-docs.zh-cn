---
title: /Zc:trigraphs（Trigraphs 替换）
description: 用于控制对 trigraphs 的一致性支持的 Microsoft c + + 编译器选项。
ms.date: 07/25/2020
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: e24f3d2f0064c3acc04b4c3774f47f6e442d5ddd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211848"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>`/Zc:trigraphs`（Trigraphs 替换）

**`/Zc:trigraphs`** 指定时，编译器将使用相应的标点字符替换三元组字符序列。

## <a name="syntax"></a>语法

> **`/Zc:trigraphs`**[**`-`**]

## <a name="remarks"></a>备注

*三元组*包含两个连续的问号（ **`??`** ），后跟一个唯一的第三个字符。 C 语言标准支持 trigraphs 对于使用不包含某些标点字符的方便图形表示形式的字符集的源文件。 例如，启用 trigraphs 时，编译器将 **`??=`** 使用字符替换三元组 **`#`** 。 通过 c + + 14，trigraphs 支持，如 C 中所示。C + + 17 标准将从 c + + 语言中删除 trigraphs。 在 c + + 代码中， **`/Zc:trigraphs`** 编译器选项通过相应的标点字符启用三元组序列的替换。 **`/Zc:trigraphs-`** 禁用三元组替换。

**`/Zc:trigraphs`** 默认情况下，此选项处于关闭状态，并且在指定选项时不会影响选项 [`/permissive-`](permissive-standards-conformance.md) 。

有关 C/c + + trigraphs 的列表以及演示如何使用 trigraphs 的示例，请参阅[trigraphs](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包含 **`/Zc:trigraphs`** 或 **`/Zc:trigraphs-`** ，然后选择 **"确定"**。

## <a name="see-also"></a>另请参阅

[`/Zc`度](zc-conformance.md)<br/>
[三字符组](../../c-language/trigraphs.md)
