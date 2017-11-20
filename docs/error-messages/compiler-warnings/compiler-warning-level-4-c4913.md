---
title: "编译器警告 （等级 4） C4913 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4913
dev_langs: C++
helpviewer_keywords: C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71e9021e91f98b2d6b6e90590d964056cf562f69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4913"></a>编译器警告（等级 4）C4913
**存在用户定义的二进制运算符“,”，但没有重载可以转换所有操作数，使用了默认的内置二进制运算符“,”**  
  
 对内置逗号运算符的调用发生在同样具有重载的逗号运算符的程序中；你认为可能已发生的转换没有发生。  
  
 下面的示例生成 C4913：  
  
```  
// C4913.cpp  
// compile with: /W4  
struct A  
{  
};  
  
struct S  
{  
};  
  
struct B  
{  
   // B() { }  
   // B(S &s) { s; }  
};  
  
B operator , (A a, B b)     
{  
   a;  
   return b;  
}  
  
int main()  
{  
   A a;  
   B b;  
   S s;  
  
   a, b;   // OK calls user defined operator  
   a, s;   // C4913 uses builtin comma operator  
           // uncomment the conversion code in B to resolve.  
}  
```