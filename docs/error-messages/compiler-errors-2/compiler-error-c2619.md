---
title: "编译器错误 C2619 | Microsoft Docs"
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
  - "C2619"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2619"
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2619
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“标识符”：匿名结构或联合中不允许使用静态数据成员  
  
 匿名结构或联合的成员声明为 `static`。  
  
 下面的示例生成 C2619，并演示如何通过删除 static 关键字修复此错误。  
  
```  
// C2619.cpp  
int main() {  
   union { static int j; };  // C2619  
   union { int j; };  // OK  
}  
```