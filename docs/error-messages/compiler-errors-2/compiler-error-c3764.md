---
title: "编译器错误 C3764 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3764
dev_langs: C++
helpviewer_keywords: C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 60317bb31b5021d4b9b1b6568d77ae92e06880ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3764"></a>编译器错误 C3764
override_function： 不能重写基类方法 base_class_function  
  
 编译器检测到的格式不正确的重写。 例如，基类函数未`virtual`。 有关详细信息，请参阅[重写](../../windows/override-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3764。  
  
```  
// C3764.cpp  
// compile with: /clr /c  
public ref struct A {  
   void g(int);  
   virtual void h(int);  
};  
  
public ref struct B : A {  
   virtual void g(int) override {}   // C3764  
   virtual void h(int) override {}   // OK  
};  
```  
  
## <a name="example"></a>示例  
 C3764 基类方法既显式时也会发生和名为重写。 下面的示例生成 C3764。  
  
```  
// C3764_b.cpp  
// compile with: /clr /c  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : public A {  
   virtual void Test() override {}  
   virtual void Test2() = A::Test {}   // C3764  
};  
```