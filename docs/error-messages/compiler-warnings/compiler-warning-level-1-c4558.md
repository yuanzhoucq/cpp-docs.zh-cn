---
title: "编译器警告（等级 1）C4558 | Microsoft Docs"
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
  - "C4558"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4558"
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4558
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

操作数“value”的值超出“lowerbound \- upperbound”的范围  
  
 传递到汇编语言指令的值超出了为参数指定的范围。  该值将被截断。  
  
 下面的示例生成 C4558：  
  
```  
// C4558.cpp  
// compile with: /W1  
// processor: x86  
void asm_test() {  
   __asm pinsrw   mm1, eax, 8;   // C4558  
}  
  
int main() {  
}  
```