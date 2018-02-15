---
title: "ML 非致命错误 A2133 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adc1929f14b5264717936f1a4aebb8dabd2e439d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非致命错误 A2133
**注册值覆盖 INVOKE**  
  
 寄存器作为自变量传递给过程，但生成的代码[INVOKE](../../assembler/masm/invoke.md)以将其他自变量传递销毁寄存器的内容。  
  
 AX、 AL、 AH、 EAX、 DX、 DL、 DH 和 EDX 寄存器可能通过汇编程序，用于执行数据转换。  
  
 使用不同的注册。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)