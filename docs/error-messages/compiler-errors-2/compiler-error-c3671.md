---
title: "编译器错误 C3671 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3671
dev_langs:
- C++
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b64c8be94bc6eb89fea04d7edee342e0015b8a9b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3671"></a>编译器错误 C3671
function_1： 函数不重写 function_2  
  
 使用显式重写语法时，编译器将生成错误，如果函数未重写。  请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3671。  
  
```  
// C3671.cpp  
// compile with: /clr /c  
ref struct S {  
   virtual void f();  
};  
  
ref struct S1 : S {  
   virtual void f(int) new sealed = S::f;   // C3671  
   virtual void f() new sealed = S::f;  
};  
```
