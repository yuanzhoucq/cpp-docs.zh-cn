---
title: 调用 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27c18c83b623ce1a22ffcb5e1a9f1ce98ee6eb20
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="invoke"></a>INVOKE
在给定的地址调用过程*表达式*，并将参数传递到堆栈上或在寄存器中根据语言类型的标准调用约定。  
  
## <a name="syntax"></a>语法  
  
```  
  
INVOKE   
expression [[, arguments]]  
```  
  
## <a name="remarks"></a>备注  
 每个自变量传递给过程可能是表达式、 一个注册对中或地址表达式 (表达式前面`ADDR`)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)