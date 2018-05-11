---
title: 语法摘要的定义 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d6c84354332b4d01ca07f672024fe9b488cd0a2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="definitions-for-the-grammar-summary"></a>语法摘要的定义
终止符是语法定义中的终结点。 不提供其他解决方法。 终止符包括保留字和用户定义的标识符的集。  
  
非终止符是语法中的占位符。 它们中的大多数是在此语法摘要中的其他位置定义的。 定义可是递归的。 在中定义以下非终止符[词法约定](../cpp/lexical-conventions.md)部分*c + + 语言参考*:  
  
`constant`*常量表达式*，*标识符*，*关键字*， `operator`， `punctuator`  
  
可选组件由带下标的 opt 指示。 例如，下面指示包含在大括号中的可选表达式：  
  
**{** *表达式*选择 **}**  
  
## <a name="see-also"></a>请参阅  
[语法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)