---
title: "编译器错误 C2311 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2311"
ms.assetid: 1aff9bd5-ed0b-4db6-bbc0-01ac89850cf2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“exception”: 在行 number 上被“...”捕获  
  
 用于省略号 \(...\) 的 catch 处理程序必须是用于引发的最后一个处理程序。  
  
 下面的示例生成 C2311：  
  
```  
// C2311.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "ooops!";  
   }  
   catch( ... ) {}  
   catch( int ) {}   // C2311  ellipsis handler not last catch  
}  
```