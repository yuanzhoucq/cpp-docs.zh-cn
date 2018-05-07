---
title: 编译器错误 C3736 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3736
dev_langs:
- C++
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4268e8f01d01147351cb1e9810c05eae0ef215
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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