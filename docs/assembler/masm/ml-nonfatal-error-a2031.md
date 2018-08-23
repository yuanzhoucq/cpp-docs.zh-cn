---
title: ML 非致命错误 A2031 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab35776944604f3133254532d2631460c755983
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057141"
---
# <a name="ml-nonfatal-error-a2031"></a>ML 非致命错误 A2031
**必须是索引或基本寄存器**  
  
 尝试使用未在内存表达式中的基 / 索引寄存器的寄存器。  
  
 例如，以下表达式会导致此错误：  
  
```  
[ax]  
[bl]  
```  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)