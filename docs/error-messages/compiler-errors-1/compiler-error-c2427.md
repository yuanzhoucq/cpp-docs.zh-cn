---
title: "编译器错误 C2427 | Microsoft Docs"
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
  - "C2427"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2427"
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2427
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 无法在此范围中定义类  
  
 尝试定义嵌套类，但该嵌套类是基类的成员，而非大多数包含类。  
  
 下面的示例生成 C2427：  
  
```  
// C2427.cpp  
// compile with: /c  
template <class T>   
struct S {  
   struct Inner;   
};   
  
struct Y : S<int> {};   
  
struct Y::Inner {};   // C2427  
  
// OK  
template<typename T>  
struct S<T>::Inner {};  
```