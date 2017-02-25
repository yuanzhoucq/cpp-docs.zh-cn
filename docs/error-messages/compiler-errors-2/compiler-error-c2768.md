---
title: "编译器错误 C2768 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2768"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2768"
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2768
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 非法使用显式模板参数  
  
 编译器无法确定函数定义应是函数模板的显式专用化还是函数定义应用于新函数。  
  
 此错误作为编译器一致性增强功能的一部分在 Visual Studio .NET 2003 中引入。  
  
 下面的示例生成 C2768：  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```