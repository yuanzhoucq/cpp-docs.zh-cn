---
title: "编译器错误 C2400 | Microsoft Docs"
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
  - "C2400"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2400"
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2400
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“context”中的内联汇编语法错误；找到“token”  
  
 该标记在指定的上下文中导致语法错误。  
  
 下面的示例生成 C2400：  
  
```  
// C2400.cpp  
// processor: x86  
int main() {  
   __asm {  
      heh ax,bx;   // C2400, heh is not a valid x86 instruction  
      mov ax,bx;   // OK  
   }  
}  
```