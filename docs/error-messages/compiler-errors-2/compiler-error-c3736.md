---
title: "编译器错误 C3736 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3736
dev_langs:
- C++
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0c2d7f548a1795221a72d0ac7be01e8ed87fa6ce
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3736"></a>编译器错误 C3736
event： 必须是一种方法，或在托管事件中 （可选） 的数据成员  
  
 本机和 COM 事件必须是方法。 .NET 事件也可以是数据成员。  
  
 下面的示例生成 C3736:  
  
```  
// C3736.cpp  
struct A {  
   __event int e();  
};  
  
struct B {  
   int f;   // C3736  
   // The following line resolves the error.  
   // int f();  
   B(A* a) {  
      __hook(&A::e, a, &B::f);  
   }  
};  
  
int main() {  
}  
```
