---
title: "编译器警告（等级 1）C4804 | Microsoft Docs"
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
  - "C4804"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4804"
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4804
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operation”: 在操作中使用类型“bool”不安全  
  
 当您在意外情况下使用了 `bool` 变量或值时出现此警告。  例如，如果您使用负一元运算符 \(**\-**\) 或求补运算符 \(`~`\)，则生成 C4804。  编译器将计算表达式。  
  
## 示例  
 下面的示例生成 C4804：  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```