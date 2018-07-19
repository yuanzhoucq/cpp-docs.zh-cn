---
title: ML 非致命错误 A2006 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d2f7df00d1c0658ee8301fbde1efe2522b52fc
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054850"
---
# <a name="ml-nonfatal-error-a2006"></a>ML 非致命错误 A2006
**未定义的符号： 标识符**  
  
 尝试使用未定义的符号。  
  
 可能发生下列情况之一：  
  
-   未定义符号。  
  
-   字段不是结构的指定的成员。  
  
-   未包含的包含文件中定义了符号。  
  
-   在未使用的外部符号[EXTERN](../../assembler/masm/extern-masm.md)或[EXTERNDEF](../../assembler/masm/externdef.md)指令。  
  
-   符号名称时拼写错误。  
  
-   本地代码标签引用其作用域之外。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)