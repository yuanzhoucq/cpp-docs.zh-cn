---
title: "编译器警告（等级 1）C4731 | Microsoft Docs"
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
  - "C4731"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4731"
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4731
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“pointer”: 帧指针寄存器“register”被内联程序集代码修改  
  
 修改了帧指针寄存器。  必须保存和还原内联程序集块中的寄存器或帧变量（局部变量或参数，视所修改的寄存器而定），否则代码可能不能正常工作。  
  
 下面的示例生成 C4731：  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP 是帧指针（FPO 是不允许的），它正在被修改。  当随后引用 `p` 时，则相对于 `EBP` 来引用它。  但 `EBP` 已被代码覆盖，所以程序将不能正常工作，甚至可能出现故障。