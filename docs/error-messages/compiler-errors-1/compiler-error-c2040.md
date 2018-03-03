---
title: "编译器错误 C2040 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f102b1fea23c89debc86970d7548ba7da152cd37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2040"></a>编译器错误 C2040
“运算符”:“identifier1”与“identifier2”的间接级别不同  
  
 涉及指定操作数的表达式具有不兼容的操作数类型或隐式转换的操作数类型。 如果这两个操作数都是算术的，或两个都是非算术的（如数组或指针），使用时将不做更改。 如果一个操作数是算术的而另一个不是算术的，则算术操作数将转换为非算术操作数的类型。  
  
 此示例生成 C2040，并演示如何对其进行修复。  
  
```  
// C2040.cpp  
// Compile by using: cl /c /W3 C2040.cpp  
bool test() {  
   char c = '3';  
   return c == "3"; // C2446, C2040  
   // return c == '3'; // OK  
}  
```