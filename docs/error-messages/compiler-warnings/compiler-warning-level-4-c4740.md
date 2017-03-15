---
title: "编译器警告（等级 4）C4740 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4740"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4740"
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4740
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

流入或流出内联 asm 代码取消全局优化  
  
 当跳转到或跳转出 `asm` 块时，为该函数禁用全局优化。  
  
 下面的示例生成 C4740：  
  
```  
// C4740.cpp  
// compile with: /O2 /W4  
// processor: x86  
int main() {  
   __asm jmp tester  
   tester:;  
}  
```