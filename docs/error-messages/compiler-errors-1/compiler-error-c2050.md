---
title: "编译器错误 C2050 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2050"
ms.assetid: 66aaed7d-00db-4ce1-a9d6-4447c1cf07ce
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

switch 表达式不是整型  
  
 `switch` 表达式计算结果为一个非整数值。  若要解决该错误，请在 switch 语句中只使用整数值。  
  
 下面的示例生成 C2050：  
  
```  
// C2050.cpp  
int main() {  
   int a = 1;  
   switch ("a") {   // C2050  
      case 1:  
         a = 0;  
      default:  
         a = 2;  
   }  
}  
```  
  
 可能的解决方案：  
  
```  
// C2050b.cpp  
int main() {  
   int a = 1;  
   switch (a) {  
      case 1:  
         a = 0;  
      default:  
         a = 2;  
   }  
}  
```