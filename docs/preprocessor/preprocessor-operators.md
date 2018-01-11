---
title: "预处理器运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f28d2eba75636d6000f909ffe4527ca2b037dd85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="preprocessor-operators"></a>预处理器运算符
有四种预处理器特定运算符的上下文中使用`#define`指令 （请参阅以下列表了解每个摘要）。 在接下来三个部分讨论了对 stringizing、 charizing，和标记粘贴运算符。 有关信息**定义**运算符，请参阅[#if、 #elif，#else 和 #endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
|运算符|操作|  
|--------------|------------|  
|[字符串化运算符 （#）](../preprocessor/stringizing-operator-hash.md)|导致相应的实际参数括在双引号内|  
|[Charizing 运算符 (#@)](../preprocessor/charizing-operator-hash-at.md)|导致相应的自变量以括在单引号引起来并被视为一个字符 （Microsoft 专用）|  
|[标记粘贴运算符 （#）](../preprocessor/token-pasting-operator-hash-hash.md)|允许作为实际参数用于将连接在一起形成其他令牌的令牌|  
|[定义的运算符](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|简化了编写某些宏指令中的复合表达式|  
  
## <a name="see-also"></a>请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)   
 [预定义的宏](../preprocessor/predefined-macros.md)   
 [C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)