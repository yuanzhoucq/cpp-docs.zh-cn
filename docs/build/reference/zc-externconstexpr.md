---
title: "/Zc:externConstexpr （启用 extern constexpr 变量） |Microsoft 文档"
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:externConstexpr
dev_langs:
- C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84037e5e8a942d51175d97957d0c05bd6f4aa29d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr （启用 extern constexpr 变量）

**/Zc:externConstexpr**编译器选项告知编译器符合 c + + 标准，并允许为外部链接`constexpr`变量。 默认情况下，Visual Studio 始终为`constexpr`变量内部链接，即使你指定`extern`关键字。

## <a name="syntax"></a>语法

> /Zc:externConstexpr [-]

## <a name="remarks"></a>备注

**/Zc:externConstexpr**编译器选项将导致编译器要应用于通过使用声明的变量的外部链接`extern constexpr`。 **/Zc:externConstexpr**选项是在 Visual Studio 2017 更新 15.5 中开始提供。 在早期版本的 Visual Studio 中，并按默认或如果**/Zc:externConstexpr-**指定，则 Visual Studio 将应用到的内部链接`constexpr`变量即使`extern`使用关键字。

如果标头文件包含声明的变量`extern constexpr`，它必须进行标记[__declspec （selectany)](../../cpp/selectany.md)以便重复声明合并到链接的二进制文件中的单个实例。 否则可能会看到链接器错误，例如，LNK2005 有关违反单个定义规则。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 下**配置属性**，展开**C/c + +** ，然后选择**命令行**。

1. 添加**/Zc:externConstexpr**或**/Zc:externConstexpr-**到**其他选项：**窗格。

## <a name="see-also"></a>请参阅

[/Zc （一致性）](../../build/reference/zc-conformance.md)  
[auto 关键字](../../cpp/auto-keyword.md)