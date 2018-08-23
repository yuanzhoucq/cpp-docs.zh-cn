---
title: 预处理器运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fca1c097a01f34fb2cc708489338391dfced982f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541357"
---
# <a name="preprocessor-operators"></a>预处理器运算符
四个预处理器特定运算符的上下文中使用`#define`指令 （请参阅以下有关每个摘要列表）。 字符串化、 charizing，和标记粘贴运算符接下来的三各节所述。 有关的信息`defined`运算符，请参阅[#if、 #elif，#else 和 #endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
|运算符|操作|  
|--------------|------------|  
|[字符串化运算符 （#）](../preprocessor/stringizing-operator-hash.md)|导致相应的实际参数括在双引号内|  
|[Charizing 运算符 (#@)](../preprocessor/charizing-operator-hash-at.md)|导致相应的参数括在单引号内并被视为字符 （Microsoft 专用）|  
|[标记粘贴运算符 （#）](../preprocessor/token-pasting-operator-hash-hash.md)|允许作为实际参数用于将连接在一起形成其他令牌的令牌|  
|[定义的运算符](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|简化了某些宏指令中的复合表达式写入|  
  
## <a name="see-also"></a>请参阅  
 
[预处理器指令](../preprocessor/preprocessor-directives.md)   
[预定义的宏](../preprocessor/predefined-macros.md)   
[C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)