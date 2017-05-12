---
title: "编译器错误 C2611 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2611"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2611"
ms.assetid: 3f2d5253-f24f-4724-83d0-6b2aa6a4e551
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2611
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“token”: 非法的后缀“~”\(应输入标识符\)  
  
 该标记不是标识符。  
  
 下面的示例生成 C2611：  
  
```  
// C2611.cpp  
// compile with: /c  
class C {  
   C::~operator int();   // C2611  
   ~C();   // OK  
};  
```