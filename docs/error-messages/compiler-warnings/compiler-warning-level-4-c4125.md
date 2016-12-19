---
title: "编译器警告（等级 4）C4125 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4125"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4125"
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4125
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

十进制数字终止八进制转义序列  
  
 编译器未用十进制数求八进制数，并假定十进制数字是一个字符。  
  
## 示例  
  
```  
// C4125a.cpp // compile with: /W4 char array1[] = "\709"; // C4125 int main() { }  
```  
  
 如果数字 9 作为一个字符，请如下更正示例：  
  
```  
// C4125b.cpp // compile with: /W4 char array[] = "\0709";  // C4125 String containing "89" int main() { }  
```