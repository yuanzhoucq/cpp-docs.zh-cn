---
title: "编译器错误 C2162 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2162
dev_langs: C++
helpviewer_keywords: C2162
ms.assetid: 34923628-d35e-48ab-9072-b95e3b5f6b45
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a9595542a9509a50fb83d72575a03b27691637e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2162"></a>编译器错误 C2162
预期的宏形参  
  
 字符串化运算符 （#） 后面的标记不是正式参数名称。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2162:  
  
```  
// C2162.cpp  
// compile with: /c  
#include <stdio.h>  
  
#define print(a) printf_s(b)   // OK  
#define print(a) printf_s(#b)    // C2162  
```