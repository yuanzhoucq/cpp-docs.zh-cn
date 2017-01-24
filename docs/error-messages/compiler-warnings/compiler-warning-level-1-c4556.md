---
title: "编译器警告（等级 1）C4556 | Microsoft Docs"
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
  - "xml"
  - "C4556"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4556"
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4556
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内部即时参数“value”的值超出“lowerbound \- upperbound”的范围  
  
 内部项匹配硬件指令。  硬件指令具有固定数目的用来对常数进行编码的位。  如果 ***value*** 超出范围，它将不会正确编码。  编译器截断多余位。  
  
 下面的示例生成 C4556：  
  
```  
// C4556.cpp  
// compile with: /W1  
// processor: x86 IPF  
#include <xmmintrin.h>  
void test()  
{  
   __m64 m;  
   _m_pextrw(m, 5);   // C4556  
}  
int main()  
{  
}  
```