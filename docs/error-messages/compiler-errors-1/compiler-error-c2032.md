---
title: "编译器错误 C2032 | Microsoft Docs"
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
  - "C2032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2032"
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 函数不能是结构\/联合“structorunion”的成员  
  
 该结构或联合中的一个成员函数在 C\+\+ 中允许使用而在 C 中不允许使用。  若要解决该错误，请编译为 C\+\+ 程序或移除该成员函数。  
  
 下面的示例生成 C2032：  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 可能的解决方案：  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```