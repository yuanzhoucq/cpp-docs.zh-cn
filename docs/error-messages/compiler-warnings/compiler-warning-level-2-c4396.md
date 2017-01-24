---
title: "编译器警告（等级 2）C4396 | Microsoft Docs"
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
  - "C4396"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4396"
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4396
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”：友元声明引用函数模板的专用化时，无法使用内联说明符  
  
 函数模板的专用化不能指定任何[内联](../../misc/inline-inline-forceinline.md)说明符。 编译器发出警告 C4396 并忽略内联说明符。  
  
### 更正此错误  
  
-   从友元函数声明中删除 `inline`、`__inline`，或 `__forceinline` 说明符。  
  
## 示例  
 下面的代码示例演示了一个带有 `inline` 说明符的无效友元函数声明。  
  
```  
// C4396.cpp // compile with: /W2 /c class X; template<class T> void Func(T t, int i); class X { friend inline void Func<char>(char t, int i);  //C4396 // try the following line instead //    friend void Func<char>(char t, int i); int i; };  
```