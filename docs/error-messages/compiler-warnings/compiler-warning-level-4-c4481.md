---
title: "编译器警告（等级 4）C4481 | Microsoft Docs"
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
  - "C4481"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4481"
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4481
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展: 重写说明符“keyword”  
  
 使用了 C\+\+ 标准之外的关键字，例如，也在 \/clr 下有效的重写说明符之一。有关详细信息，请参阅  
  
-   [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## 示例  
 下面的示例生成 C4481。  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```