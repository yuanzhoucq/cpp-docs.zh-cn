---
title: "编译器警告 （等级 1） C4358 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4358
dev_langs: C++
helpviewer_keywords: C4358
ms.assetid: a9848f84-14b3-405e-81bf-ee3e91a51511
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e006bed5e805118c394b9107aa5eb91660aa542
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4358"></a>编译器警告（等级 1）C4358
operator： 返回组合的委托的类型不是 void;返回的值是未定义  
  
 两个委托已合并和返回值不是 void。 如果具有非 void 返回值的两个委托结合起来时，编译器不能使用的委托的返回值进行正确分配。  
  
 下面的示例生成 C4358:  
  
```  
// C4358.cpp  
// compile with: /clr /W1  
delegate int D();  
delegate void E();  
  
ref class X {  
   int i;  
public:  
   X(int ii) : i(ii) {}  
   int f() {  
      return i;  
   }  
};  
  
ref class Y {  
   int i;  
public:  
   Y() {}  
   void g() {}  
};  
  
int main() {  
   D^ d = gcnew D(gcnew X(1), &X::f);  
   D^ d2 = gcnew D(gcnew X(2), &X::f);  
  
   d += d2;   // C4358  
   int j = d();   // return value indeterminate  
  
   E^ e = gcnew E(gcnew Y, &Y::g);  
   E^ e2 = gcnew E(gcnew Y, &Y::g);  
   e += e2;   // OK  
}  
```