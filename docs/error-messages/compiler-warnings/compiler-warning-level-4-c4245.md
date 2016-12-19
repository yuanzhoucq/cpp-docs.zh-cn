---
title: "编译器警告（等级 4）C4245 | Microsoft Docs"
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
  - "C4245"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4245"
ms.assetid: 85083d53-9cc2-4d12-b58c-6dad28f15cbe
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4245
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“conversion”: 从“type1”转换到“type2”，有符号\/无符号不匹配  
  
 您尝试将带负值的有符号 **const** 转换为 `unsigned`。  
  
 下面的示例生成 C4245：  
  
```  
// C4245.cpp  
// compile with: /W4 /c  
const int i = -1;  
unsigned int j = i; // C4245  
  
const int k = 1;  
unsigned int l = k; // okay  
  
int m = -1;  
unsigned int n = m; // okay  
  
void Test(size_t i) {}  
  
int main() {  
   Test( -19 );   // C4245  
}  
```