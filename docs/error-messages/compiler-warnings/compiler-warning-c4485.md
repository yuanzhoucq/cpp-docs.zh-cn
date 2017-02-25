---
title: "编译器警告 C4485 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4485"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4485"
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告 C4485
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“override\_function”: 匹配 ref 基类方法“base\_class\_function”，但没有标记为“new”或“override”；假定为“new”\(和“virtual”\)  
  
 访问器重写（无论是否具有 `virtual` 关键字）基类访问器函数，而 `override` 或 `new` 说明符并非重写函数签名的一部分。  添加 `new` 或 `override` 说明符可解决此警告。  
  
 有关更多信息，请参见 [override](../../windows/override-cpp-component-extensions.md) 和 [新的 \(在 vtable 的新槽\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。  
  
 C4485 始终作为错误发出。  使用 [警告](../../preprocessor/warning.md) 杂注可取消 C4485。  
  
## 示例  
 下面的示例生成 C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```