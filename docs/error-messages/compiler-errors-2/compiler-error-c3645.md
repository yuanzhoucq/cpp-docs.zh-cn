---
title: "编译器错误 C3645 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3645"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3645"
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3645
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: \_\_clrcall 不能用在编译为本机代码的函数上  
  
 函数中存在某些关键字将导致将函数编译到本机。  
  
## 示例  
 下面的示例生成 C3645。  
  
```  
// C3645.cpp  
// compile with: /clr /c  
#pragma unmanaged   
int __clrcall dog() {}   // C3645  
```