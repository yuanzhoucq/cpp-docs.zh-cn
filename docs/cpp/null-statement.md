---
title: "Null 语句 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "表达式 [C++], null"
  - "null 语句"
  - "null 值, 表达式"
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Null 语句
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“null 语句”是缺少 *expression* 的表达式语句。  当语言的语法调用语句而不是表达式计算时，它很有用。    它包括分号。  
  
 Null 语句通常用作迭代语句中的占位符或用作在复合语句或函数的末尾放置标签的语句。  
  
 以下代码片段说明如何将一个字符串复制到另一个字符串，并包含 null 语句：  
  
```  
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## 请参阅  
 [表达式语句](../cpp/expression-statement.md)