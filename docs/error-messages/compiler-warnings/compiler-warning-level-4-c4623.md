---
title: "编译器警告（等级 4）C4623 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4623"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4623"
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4623
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“`derived class`”：默认构造函数已被隐式定义为已删除，因为基类默认构造函数不可访问或已被删除  
  
 基类中的构造函数不可访问，且没有为派生类生成构造函数。  任何在堆栈上创建此类型对象的尝试都将导致编译器错误。  
  
 默认情况下，此警告处于关闭状态。  请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)了解详细信息。  
  
## 示例  
 下面的示例生成 C4623。  
  
```  
// C4623.cpp  
// compile with: /W4  
#pragma warning(default : 4623)  
class B {  
   B();  
};  
  
class C {  
public:  
   C();  
};  
  
class D : public B {};   // C4623 - to fix, make B's constructor public  
class E : public C {};   // OK - class C constructor is public  
  
int main() {  
   // D d;  will cause an error  
}  
```