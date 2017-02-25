---
title: "编译器错误 C2800 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2800"
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法重载“operator operator”  
  
 无法重载下列运算符：类成员访问 \(`.`\)、指向成员的指针 \(`.*`\)、范围解析 \(`::`\)、条件表达式 \(`? :`\) 和 `sizeof`。  
  
 下面的示例生成 C2800：  
  
```  
// C2800.cpp  
// compile with: /c  
class C {  
   operator:: ();   // C2800  
};  
```