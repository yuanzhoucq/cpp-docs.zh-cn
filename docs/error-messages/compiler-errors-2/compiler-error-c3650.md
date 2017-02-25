---
title: "编译器错误 C3650 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3650"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3650"
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3650
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“interface\_method”: 不能用作显式重写，必须是基类的虚拟成员函数  
  
 已尝试对非虚拟成员执行显式重写。  
  
 有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下面的示例生成 C3650：  
  
```  
// C3650.cpp  
// compile with: /clr  
public interface struct I {  
   void a();  
};  
  
public ref class S {  
public:  
   static int f() { return 0; }  
   static int g() { return 0; }  
};  
  
public ref struct T1 : public S, I {  
   virtual int f() new sealed = S::f;   // C3650  
   virtual int g() { return 0; }   // OK does not override S::g  
   virtual void a() new sealed = I::a {}   // OK  
};  
```