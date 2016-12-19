---
title: "编译器错误 C2054 | Microsoft Docs"
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
  - "C2054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2054"
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在“identifier”之后应输入“\(”  
  
 该函数标识符用在需要尾部括号的上下文中。  
  
 导致该错误的可能原因是省略了复杂初始化上的等号 \(\=\)。  
  
 下面的示例生成 C2054：  
  
```  
// C2054.c  
int array1[] { 1, 2, 3 };   // C2054, missing =  
```  
  
 可能的解决方案：  
  
```  
// C2054b.c  
int main() {  
   int array2[] = { 1, 2, 3 };  
}  
```