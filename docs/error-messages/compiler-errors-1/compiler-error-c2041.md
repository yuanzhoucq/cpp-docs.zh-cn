---
title: "编译器错误 C2041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2041"
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法的数字“character”\(用于基“number”\)  
  
 指定的字符不是基（如八进制或十六进制）的有效数字。  
  
 下面的示例生成 C2041：  
  
```  
// C2041.cpp  
int i = 081;   // C2041  8 is not a base 8 digit  
```  
  
 可能的解决方案：  
  
```  
// C2041b.cpp  
// compile with: /c  
int j = 071;  
```