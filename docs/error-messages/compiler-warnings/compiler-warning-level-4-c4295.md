---
title: "编译器警告（等级 4）C4295 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4295"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4295"
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 4）C4295
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**“**   
 ***数组* ”: 数组太小，无法包括终止空字符**  
  
 已初始化了数组，但数组中的最后一个字符不为空；访问该数组可能会产生意料之外的结果。  
  
 下面的示例生成 C4295：  
  
```  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```