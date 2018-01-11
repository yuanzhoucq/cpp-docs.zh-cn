---
title: "编译器错误 C3670 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3670
dev_langs: C++
helpviewer_keywords: C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 209868fff8b5bf99bf8c77e67b3a58697a1387d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3670"></a>编译器错误 C3670
重写： 不能重写无法访问基类方法 method  
  
 替代仅会在其访问级别使其可派生类型中的函数上发生。 有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下面的示例生成 C3670:  
  
```  
// C3670.cpp  
// compile with: /clr /c  
public ref class C {  
// Uncomment the following line to resolve.  
// public:  
   virtual void g() { }  
};  
  
public ref class D : public C {  
public:  
   virtual void f() new sealed = C::g {};   // C3670  
};  
```