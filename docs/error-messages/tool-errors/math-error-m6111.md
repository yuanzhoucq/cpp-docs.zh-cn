---
title: "数学错误 M6111 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6111"
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 数学错误 M6111
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆栈下溢 \(Stack Underflow\)  
  
 浮点运算在 8087\/287\/387 协处理器或模拟器上导致堆栈下溢。  
  
 该错误通常由调用不返回值的 `long double` 函数而引起。  例如，下列代码编译并运行后生成该错误：  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 程序以退出代码 139 终止。