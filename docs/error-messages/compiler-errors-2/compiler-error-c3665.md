---
title: "编译器错误 C3665 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3665
dev_langs:
- C++
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cf969622909c45a12b4f01c10782ed6a571def05
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3665"></a>编译器错误 C3665
析构函数： 重写说明符 keyword 不允许对析构函数/终结器  
  
 使用析构函数或终结器上不允许的关键字。  
  
 例如，无法在析构函数或终结器上请求新的槽。  有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)和[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 下面的示例生成 C3665:  
  
```  
// C3665.cpp  
// compile with: /clr  
public ref struct R {  
   virtual ~R() { }  
   virtual void a() { }  
};  
  
public ref struct S : R {  
   virtual ~S() new {}   // C3665  
   virtual void a() new {}   // OK  
};  
```
