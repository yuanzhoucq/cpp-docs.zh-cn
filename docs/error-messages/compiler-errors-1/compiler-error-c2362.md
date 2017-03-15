---
title: "编译器错误 C2362 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2362"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2362"
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2362
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“goto label”跳过了“identifier”的初始化  
  
 当使用 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 编译时，跳转到该标签会无法初始化此标识符。  
  
 无法跳过带有初始值设定项的声明，除非该声明包含在未进入的块内，或者已经初始化过该变量。  
  
 下面的示例生成 C2326：  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 可能的解决方案：  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```