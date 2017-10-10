---
title: "编译器错误 C2299 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4c0b18818ac45dea56d94b6046c8772710f02f56
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2299"></a>编译器错误 C2299
function： 行为更改： 显式专用化不能复制构造函数或复制赋值运算符  
  
 此错误还可能来自于为 Visual c + + 2005年执行的编译器一致性工作： Visual c + + 的早期版本的复制构造函数或复制赋值运算符允许显式专用化。  
  
 若要解决 C2299，不要复制构造函数或赋值运算符的模板函数，但而是采用一个类类型的非模板函数。 通过显式指定模板自变量调用的复制构造函数或赋值运算符的任何代码需要进行删除的模板自变量。  
  
 下面的示例生成 C2299:  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```
