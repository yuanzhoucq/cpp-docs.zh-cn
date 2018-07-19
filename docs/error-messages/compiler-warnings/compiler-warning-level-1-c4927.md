---
title: 编译器警告 （等级 1） C4927 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4927
dev_langs:
- C++
helpviewer_keywords:
- C4927
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 403b3953dccfcdf5a30dbb230018a3968f8ef44b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290129"
---
# <a name="compiler-warning-level-1-c4927"></a>编译器警告（等级 1）C4927
非法转换则隐式应用了多个用户定义的转换  
  
 多个用户定义的转换隐式应用于单个值-编译器未找到显式转换，但未找到的转换，使用它。  
  
 下面的示例生成 C4927:  
  
```  
// C4927.cpp  
// compile with: /W1  
struct B  
{  
   operator int ()  
   {  
      return 0;  
   }  
};  
  
struct A  
{  
   A(int i)  
   {  
   }  
  
   /*  
   // uncomment this constructor to resolve  
   A(B b)  
   {  
   }  
   */  
};  
  
A f1( B& b)  
{  
   return A(b);  
}  
  
B& f2( B& b)  
{  
   return b;  
}  
  
A f()  
{  
   B b;  
   return A(b);   // ok  
   return f1(b);  // ok  
   return b;      // C4927  
   return B(b);   // C4927  
   return f2(b);  // C4927  
}  
  
int main()  
{  
   B b;  
   A a = b;  
   A a2(b);  
}  
```