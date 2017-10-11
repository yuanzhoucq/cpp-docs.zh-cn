---
title: "编译器错误 C2245 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2245
dev_langs:
- C++
helpviewer_keywords:
- C2245
ms.assetid: 08aaeadf-10ec-485a-b2a6-6e775289082b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: fc7a27aba6326fddea9684562fbab7f824f6f628
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2245"></a>编译器错误 C2245
将不存在的成员函数“function”指定为友元(成员函数签名与所有重载都不匹配)  
  
 编译器未找到指定为友元的函数。  
  
 下面的示例生成 C2245：  
  
```  
// C2245.cpp  
// compile with: /c  
class B {  
   void f(int i);  
};  
  
class A {  
   int m_i;  
   friend void B::f(char);   // C2245  
   // try the following line instead  
   // friend void B::f(int);  
};  
  
void B::f(int i) {  
   A a;  
   a.m_i = 0;  
}  
```
