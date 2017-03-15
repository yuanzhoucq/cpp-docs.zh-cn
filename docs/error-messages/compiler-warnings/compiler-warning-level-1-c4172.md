---
title: "编译器警告（等级 1）C4172 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4172"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4172"
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4172
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回局部变量或临时变量的地址  
  
 函数返回局部变量或临时对象的地址。  当函数返回时会破坏局部变量和临时对象，所以返回的地址无效。  
  
 重新设计该函数以使其不返回局部对象的地址。  
  
 下面的示例生成 C4172：  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```