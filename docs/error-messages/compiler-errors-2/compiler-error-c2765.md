---
title: "编译器错误 C2765 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2765"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2765"
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2765
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数模板的显式专用化不能具有任何默认参数  
  
 不允许在函数模板的显式专用化上使用默认参数。  有关更多信息，请参见[函数模板的显式专用化](../../cpp/explicit-specialization-of-function-templates.md)。  
  
 下面的示例生成 C2765：  
  
```  
// C2765.cpp  
template<class T> void f(T t) {};  
  
template<> void f<char>(char c = 'a') {}   // C2765  
// try the following line instead  
// template<> void f<char>(char c) {}  
```