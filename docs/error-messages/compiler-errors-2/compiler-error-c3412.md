---
title: "编译器错误 C3412 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3412"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3412"
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3412
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“template”: 不能在当前范围内专用化模板  
  
 模板无法在类范围被专用化，只能在全局或命名空间范围被专用化。  
  
## 示例  
 下面的示例生成 C3412。  
  
```  
// C3412.cpp  
template <class T>  
struct S {  
   template <>  
   struct S<int> {};   // C3412 in a class  
};  
```  
  
## 示例  
 下面的示例演示一个可能的解决方案。  
  
```  
// C3412b.cpp  
// compile with: /c  
template <class T>  
struct S {};  
  
template <>  
struct S<int> {};  
```