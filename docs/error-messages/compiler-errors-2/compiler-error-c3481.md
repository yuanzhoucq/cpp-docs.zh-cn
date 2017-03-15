---
title: "编译器错误 C3481 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3481"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3481"
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3481
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：未找到 lambda 捕获变量  
  
 编译器未找到传递给 lambda 表达式捕获列表的变量的定义。  
  
### 更正此错误  
  
-   从 lambda 表达式的捕获列表中删除该变量。  
  
## 示例  
 下面的示例由于未定义变量 `n` 而生成 C3481：  
  
```  
// C3481.cpp int main() { [n] {}(); // C3481 }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)