---
title: 编译器错误 C2500 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c05ffd59e415375dd3c7f94ae9bc377c0fc2b9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2500"></a>编译器错误 C2500
identifier1: identifier2 已直接基类  
  
 类或结构的基类列表中多次出现。  
  
 直接基是基础列表中所述。 间接基类是基类的基础列表中的类之一。  
  
 一个类不能多次指定为直接基类。 类可以用作间接基类不止一次。  
  
 下面的示例生成 C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```