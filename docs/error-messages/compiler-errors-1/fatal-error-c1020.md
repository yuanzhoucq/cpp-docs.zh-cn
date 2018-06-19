---
title: 错误 C1020 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1020
dev_langs:
- C++
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c70727b5e0d83b03099b637e0f768f65d271b05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224634"
---
# <a name="fatal-error-c1020"></a>错误 C1020
意外的 #endif  
  
 `#endif` 指令有没有匹配的 `#if`、 `#ifdef`或 `#ifndef` 指令。 确保每个 `#endif` 具有匹配的指令。  
  
 下面的示例生成 C1020：  
  
```  
// C1020.cpp  
#endif     // C1020  
```  
  
 可能的解决方法：  
  
```  
// C1020b.cpp  
// compile with: /c  
#if 1  
#endif  
```