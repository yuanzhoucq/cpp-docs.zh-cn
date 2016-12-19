---
title: "编译器错误 C3490 | Microsoft Docs"
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
  - "C3490"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3490"
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3490
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法修改 var，因为正在通过 const 对象对其进行访问  
  
 在 `const` 方法中声明的 lambda 表达式不能修改不可变成员数据。  
  
### 更正此错误  
  
-   从方法声明删除 `const` 修饰符。  
  
## 示例  
 下面的示例生成 C3490，因为它修改 `const` 方法中的成员变量 `_i`：  
  
```  
// C3490a.cpp // compile with: /c class C { void f() const  { auto x = [=]() { _i = 20; }; // C3490 } int _i; };  
```  
  
## 示例  
 下面的示例通过从方法声明删除 `const` 修饰符解决了错误 C3490：  
  
```  
// C3490b.cpp // compile with: /c class C { void f() { auto x = [=]() { _i = 20; }; } int _i; };  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)