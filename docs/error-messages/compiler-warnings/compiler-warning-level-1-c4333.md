---
title: "编译器警告（等级 1）C4333 | Microsoft Docs"
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
  - "C4333"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4333"
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4333
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 右移位数过大，数据将丢失  
  
 右移位操作数过大。所有重要位都被移出，结果将始终为零。  
  
## 示例  
 下面的示例生成 C4333。  
  
```  
// C4333.cpp  
// compile with: /c /W1  
unsigned shift8 (unsigned char c) {  
   return c >> 8;   // C4333  
  
   // try the following line instead  
   // return c >> 4;   // OK  
}  
```