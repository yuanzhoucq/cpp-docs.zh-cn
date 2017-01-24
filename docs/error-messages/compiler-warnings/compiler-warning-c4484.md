---
title: "编译器警告 C4484 | Microsoft Docs"
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
  - "C4484"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4484"
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4484
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“override\_function”: 匹配 ref 基类方法“base\_class\_function”，但没有标记为“virtual”、“new”或“override”；假定为“new”\(而不是“virtual”\)  
  
 使用 **\/clr** 编译时，编译器不隐式重写基类函数，这意味着函数将在 vtable 中获得一个新槽。  要解除此警告，请显式指定函数是否可重写。  
  
 有关详细信息，请参阅：  
  
-   [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [新的 \(在 vtable 的新槽\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 C4484 始终作为错误发出。  使用 [警告](../../preprocessor/warning.md) 杂注取消显示 C4484。  
  
## 示例  
 下面的示例生成 C4484。  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```