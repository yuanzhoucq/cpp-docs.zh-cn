---
title: 语法摘要的定义
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 93cf6ffc5daf53a106c9f15a2289e2b52739d72f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222423"
---
# <a name="definitions-for-the-grammar-summary"></a>语法摘要的定义

终止符是语法定义中的终结点。 不提供其他解决方法。 终止符包括保留字和用户定义的标识符的集。

非终止符是语法中的占位符。 它们中的大多数是在此语法摘要中的其他位置定义的。 定义可是递归的。 以下非终止符在 *C++语言参考*的 "[词法约定](../cpp/lexical-conventions.md)" 部分中定义:

*常量*、*常量表达式*、*标识符*、*关键字*、*运算符*、*标点符号*

可选组件由带下标的 <sub>opt</sub> 指示。 例如，下面指示包含在大括号中的可选表达式：

**{** *expression*<sub>opt</sub> **}**

## <a name="see-also"></a>请参阅

[语法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)
