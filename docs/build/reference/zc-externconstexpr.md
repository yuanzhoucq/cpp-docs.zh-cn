---
title: /Zc:externConstexpr（启用 extern constexpr 变量）
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: 7546ab6d81137a2abb053cd18f0d5d74913c3b00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211900"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>`/Zc:externConstexpr`（启用 extern constexpr 变量）

**`/Zc:externConstexpr`** 编译器选项告知编译器遵循 c + + 标准并允许变量的外部链接 **`constexpr`** 。 默认情况下，即使指定关键字，Visual Studio 也始终提供 **`constexpr`** 变量内部链接 **`extern`** 。

## <a name="syntax"></a>语法

> **`/Zc:externConstexpr`**[**`-`**]

## <a name="remarks"></a>备注

**`/Zc:externConstexpr`** 编译器选项导致编译器将外部链接应用到使用声明的变量 `extern constexpr` 。 在 Visual Studio 的早期版本中，如果 **`/Zc:externConstexpr-`** 指定了，则 Visual studio 将应用内部链接到 **`constexpr`** 变量，即使使用了 **`extern`** 关键字。 **`/Zc:externConstexpr`** 从 Visual Studio 2017 Update 15.6 开始提供选项。 和在默认情况下处于关闭状态。 [`/permissive-`](permissive-standards-conformance.md)选项不启用 **`/Zc:externConstexpr`** 。

如果标头文件包含已声明的变量 `extern constexpr` ，则必须将其标记为，以便 [`__declspec(selectany)`](../../cpp/selectany.md) 将重复的声明合并为链接的二进制文件中的单个实例。 否则，可能会看到链接器错误（例如，LNK2005），以应对单一定义规则的冲突。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 将 **`/Zc:externConstexpr`** 或添加 **`/Zc:externConstexpr-`** 到 "**附加选项：** " 窗格。

## <a name="see-also"></a>另请参阅

[`/Zc`度](zc-conformance.md)<br/>
[`auto`关键字](../../cpp/auto-keyword.md)
