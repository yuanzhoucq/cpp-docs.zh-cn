---
title: "非原型函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 非原型函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于不是完全原型的函数，调用方会将整数值作为整型传递，而将浮点值作为双精度数传递。  仅对于浮点值，被调用方希望使用整数寄存器中的值时，整数寄存器和浮点寄存器都将包含浮点值。  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)