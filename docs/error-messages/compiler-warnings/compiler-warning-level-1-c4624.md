---
title: 编译器警告 （等级 1） C4624 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4624
dev_langs:
- C++
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d11bc5c8b5034fa305a22ba893c62faff18cc38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4624"></a>编译器警告（等级 1）C4624
“derived class”：析构函数隐式定义为已删除，因为基类析构函数不可访问或已删除  
  
 基类中的析构函数不可访问或已删除，因而没有为派生类生成析构函数。 任何在堆栈上创建此类型对象的尝试都将导致编译器错误。  
  
 下面的示例生成 C4624，并演示如何修复此错误：  
  
```  
// C4624.cpp  
// compile with: /W1 /c  
class B {  
// Uncomment the following line to fix.  
// public:  
   ~B();  
};  
  
class D : public B {};   // C4624 B's destructor not public  
```