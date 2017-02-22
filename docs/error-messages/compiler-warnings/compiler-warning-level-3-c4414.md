---
title: "编译器警告（等级 3）C4414 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4414"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4414"
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 3）C4414
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 短跳转到转换为附近的函数  
  
 短跳转根据指令生成分支到有限范围内的地址的精简的指令。  该指令包括表示该跳转与目标地址（即函数定义）之间的距离的短偏移量。  在链接期间，函数可被移到链接时优化或取决于将导致函数移出可从短偏移量访问的范围的链接时优化。  编译器必须为该跳转生成特殊记录，这要求 jmp 指令是 NEAR 或 FAR。  编译器进行了此转换。  
  
 例如，以下代码生成 C4414：  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```