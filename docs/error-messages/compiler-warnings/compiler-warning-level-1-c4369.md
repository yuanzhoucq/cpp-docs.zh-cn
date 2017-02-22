---
title: "编译器警告（等级 1）C4369 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4369"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4369"
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4369
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“enumerator”: 枚举数的值“value”不能表示为“type”，值是“new\_value”  
  
 枚举数的计算结果大于指定的基础类型的最大值。这会导致溢出，并且编译器将枚举数的值包装到该类型的最小可能值。  
  
## 示例  
 下面的示例生成 C4369。  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```