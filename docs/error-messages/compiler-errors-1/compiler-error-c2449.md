---
title: "编译器错误 C2449 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2449"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2449"
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2449
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在文件范围内找到“{”\(是否缺少函数头？\)  
  
 在文件范围内出现左大括号。  
  
 此错误可能是由函数头和函数定义的左大括号之间的分号引起的。  
  
 下面的示例生成 C2499：  
  
```  
// C2449.c  
// compile with: /c  
void __stdcall func(void) {}   // OK  
void __stdcall func(void);  // extra semicolon on this line  
{                         // C2449 detected here  
```