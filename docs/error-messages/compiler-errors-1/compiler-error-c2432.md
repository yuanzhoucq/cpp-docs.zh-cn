---
title: "编译器错误 C2432 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2432"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2432"
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2432
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在“identifier”中非法引用 16 位数据  
  
 将 16 位寄存器用作索引或基寄存器。  编译器不支持引用 16 位数据。编译 32 位代码时，无法将 16 位寄存器用作索引或基寄存器。  
  
 下面的示例生成 C2432：  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```