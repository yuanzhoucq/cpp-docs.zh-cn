---
title: "编译器警告（等级 4）C4389 | Microsoft Docs"
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
  - "c4389"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4389"
ms.assetid: fc0e3a8e-f766-437c-b7f1-e61abb2a8765
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4389
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 有符号\/无符号不匹配  
  
 运算涉及有符号和无符号变量。  这可能导致数据丢失。  
  
 下面的示例生成 C4389：  
  
```  
// C4389.cpp  
// compile with: /W4  
#pragma warning(default: 4389)  
  
int main()  
{  
   int a = 9;  
   unsigned int b = 10;  
   if (a == b)   // C4389  
      return 0;  
   else  
      return 0;  
};  
```