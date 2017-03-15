---
title: "编译器警告（等级 3）C4018 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4018"
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 3）C4018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“expression”: 有符号\/无符号不匹配  
  
 比较有符号数字和无符号数字要求编译器将有符号值转换为无符号值。  
  
 在测试有符号和无符号类型时，如果强制转换两个类型之一，则可能修复此警告。  
  
 下面的示例生成 C4018：  
  
```  
// C4018.cpp  
// compile with: /W3  
int main() {  
   unsigned int uc = 0;  
   int c = 0;  
   unsigned int c2 = 0;  
  
   if (uc < c) uc = 0;   // C4018  
  
   // OK  
   if (uc == c2) uc = 0;  
}  
```