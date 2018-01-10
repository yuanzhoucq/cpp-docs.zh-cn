---
title: "ML 非致命错误 A2133 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2133
dev_langs: C++
helpviewer_keywords: A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64619e6e14ce0268516c6c688c9a2bdeb5ea7a11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非致命错误 A2133
**注册值覆盖 INVOKE**  
  
 寄存器作为自变量传递给过程，但生成的代码[INVOKE](../../assembler/masm/invoke.md)以将其他自变量传递销毁寄存器的内容。  
  
 AX、 AL、 AH、 EAX、 DX、 DL、 DH 和 EDX 寄存器可能通过汇编程序，用于执行数据转换。  
  
 使用不同的注册。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)