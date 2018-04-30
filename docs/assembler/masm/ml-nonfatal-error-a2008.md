---
title: ML 非致命错误 A2008 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50f7329f698d23f875a29bc316067c39e8d1b8c1
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2008"></a>ML 非致命错误 A2008
**语法错误：**  
  
 在当前的位置标记导致语法错误。  
  
 可能发生下列情况之一：  
  
-   点前缀已添加到或指令中省略。  
  
-   保留的字 (如**C**或**大小**) 用作标识符。  
  
-   使用不提供当前处理器或协处理器所选内容的指令。  
  
-   比较运行时运算符 (如`==`) 而不是关系运算符的条件的程序集语句中使用 (如[EQ](../../assembler/masm/operator-eq.md))。  
  
-   指令提供太少操作数。  
  
-   使用已过时的指令。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)