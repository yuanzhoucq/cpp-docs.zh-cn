---
title: "编译器错误 C3200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3200"
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“template”: 模板参数“parameter”的模板变量无效，应输入类模板  
  
 您向类模板传递的参数无效。  类模板期望将模板用作参数。  在下面的示例中，调用 `Y<int, int> aY` 将生成 C3200。  第一个参数应为模板，例如 `Y<X, int> aY`。  
  
```  
// C3200.cpp  
template<typename T>  
class X  
{  
};  
  
template<template<typename U> class T1, typename T2>  
class Y  
{  
};  
  
int main()  
{  
   Y<int, int> y;   // C3200  
}  
```