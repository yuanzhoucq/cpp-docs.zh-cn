---
title: "整数的降级 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 30af1eb47bc459cccf9ad08c36d05a3fe7b31bf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="demotion-of-integers"></a>整数的降级
**ANSI 3.2.1.2**：在值无法表示的情况下，将整数转换为较短的带符号整数的结果，或者将无符号整数转换为同等长度的带符号整数的结果  
  
 当 **long** 整数强制转换为 **short** 时，或者 **short** 转换为 `char` 时，将保留最低有效字节。  
  
 例如，此行  
  
```  
short x = (short)0x12345678L;  
```  
  
 将值 0x5678 赋给 `x`，此行  
  
```  
char y = (char)0x1234;  
```  
  
 将值 0x34 赋给 `y`。  
  
 当带符号变量转换无符号变量（或相反）时，位模式保持不变。 例如，将 -2 (0xFE) 强制转换为无符号值将生成 254（也是 0xFE）。  
  
## <a name="see-also"></a>请参阅  
 [整数](../c-language/integers.md)