---
title: "编译器错误 C2766 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2766"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2766"
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2766
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显式专用化；“specialization”已定义  
  
 不允许使用重复的显式专用化。  有关更多信息，请参见[函数模板的显式专用化](../../cpp/explicit-specialization-of-function-templates.md)。  
  
 下面的示例生成 C2766：  
  
```  
// C2766.cpp  
// compile with: /c  
template<class T>   
struct A {};  
  
template<>   
struct A<int> {};  
  
template<>   
struct A<int> {};   // C2766  
// try the following line instead  
// struct A<char> {};  
```