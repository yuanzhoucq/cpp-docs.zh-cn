---
title: "编译器错误 C2486 | Microsoft Docs"
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
  - "C2486"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2486"
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2486
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

仅在具有“naked”特性的函数中允许“\_\_LOCAL\_SIZE”  
  
 在内联程序集函数中，名称 `__LOCAL_SIZE` 是保留的，供用 [naked](../../cpp/naked-cpp.md) 特性声明的函数使用。  
  
 下面的示例生成 C2486：  
  
```  
// C2486.cpp  
// processor: x86  
void __declspec(naked) f1() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE  
   }  
}  
void f2() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE   // C2486  
   }  
}  
```