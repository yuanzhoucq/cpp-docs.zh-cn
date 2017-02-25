---
title: "编译器警告（等级 1）C4311 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4311"
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 编译器警告（等级 1）C4311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”: 从“type”到“type”的指针截断  
  
 此警告检测 64 位指针截断问题。  例如，如果为 64 位体系结构编译代码，则当指针被分配给 `int`（32 位）时，指针（64 位）的值将被截断。  相关信息请参阅[使用指针的规则](http://msdn.microsoft.com/library/windows/desktop/aa384242)。  
  
 有关警告 C4311 的常见原因的其他信息，请参阅[常见编译器错误](http://msdn.microsoft.com/library/windows/desktop/aa384160)。  
  
 为 64 位目标编译后，下列代码示例会生成 C4311，然后演示如何修复此问题：  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```