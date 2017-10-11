---
title: "编译器错误 C3648 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3648
dev_langs:
- C++
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5be1886ad2404f0c0eb30cb5511111e4e8e97180
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3648"></a>编译器错误 C3648
此显式重写语法要求 /clr:oldSyntax  
  
在编译的最新的托管语法时，编译器找到显式重写对于以前的版本不再受支持的语法。  
  
有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3648:  
  
```  
// C3648.cpp  
// compile with: /clr  
public interface struct I {  
   void f();  
};  
  
public ref struct R : I {  
   virtual void I::f() {}   // C3648  
   // try the following line instead  
   // virtual void f() = I::f{}  
};  
```
