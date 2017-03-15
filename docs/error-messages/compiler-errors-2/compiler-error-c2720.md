---
title: "编译器错误 C2720 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2720"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2720"
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2720
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：成员上的“specifier”存储类说明符非法  
  
 存储类无法用于声明外部的类成员。  若要解决此错误，请从类声明外部的成员定义中删除不需要的[存储类说明符](http://msdn.microsoft.com/zh-cn/10b3d22d-cb40-450b-994b-08cf9a211b6c)。  
  
 下例生成了 C2720，并介绍了如何修复此错误：  
  
```  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
  
```