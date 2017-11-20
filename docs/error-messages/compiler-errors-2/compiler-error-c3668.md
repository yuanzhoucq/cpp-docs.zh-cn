---
title: "编译器错误 C3668 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3668
dev_langs: C++
helpviewer_keywords: C3668
ms.assetid: 53a96698-bde4-4447-95b5-b5108291f60c
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5db5144aac56112522f7ac707bd1b5f252929dc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3668"></a>编译器错误 C3668
method： 重写说明符替代方法未进行重写任何基类方法  
  
 尝试重写不存在函数的函数。  
  
 有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3668。  
  
```  
// C3668.cpp  
// compile with: /c  
__interface I {  
   void f(int);   // virtual by default  
};  
  
class J {  
public:  
   void g(int);  
   virtual void h(int);  
};  
  
struct R : I,J {  
   virtual void f() override {}   // C3668  
   virtual void f(int) override {}   // OK  
  
   virtual void g(int) override {}   // C3668  
   virtual void h(int) override {}   // OK  
};  
```