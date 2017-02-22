---
title: "编译器警告（等级 2）C4056 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4056"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4056"
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 2）C4056
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

浮点常数算术溢出  
  
 浮点常数算术生成的结果超出最大允许值。  
  
 在常数算法期间执行的编译器优化会导致出现此警告。  若关闭优化 \([\/Od](../../build/reference/od-disable-debug.md)\) 时警告消失，则可以安全地忽略此警告。  
  
 下面的示例生成 C4056：  
  
```  
// C4056.cpp  
// compile with: /W2 /LD  
#pragma warning (default : 4056)  
float fp_val = 1.0e300 * 1.0e300;   // C4056  
```