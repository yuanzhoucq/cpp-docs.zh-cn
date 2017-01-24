---
title: "编译器错误 C3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3482"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3482"
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3482
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“this”只能在非静态成员函数中用作 lambda 捕获  
  
 不能将 `this` 传递至在静态方法或全局函数中声明的 lambda 表达式的捕获列表中。  
  
### 更正此错误  
  
-   将封闭函数转换为非静态方法，或  
  
-   从 lambda 表达式的捕获列表中删除 `this` 指针。  
  
## 示例  
 以下示例生成 C3482：  
  
```  
// C3482.cpp // compile with: /c class C { public: static void staticMethod() { [this] {}(); // C3482 } };  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)