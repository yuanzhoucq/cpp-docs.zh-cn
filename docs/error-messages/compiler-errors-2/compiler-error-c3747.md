---
title: "编译器错误 C3747 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3747"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3747"
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3747
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

缺少默认模板参数: 参数 param  
  
 在参数列表中，具有默认值的泛型参数或模板参数后面不能是没有默认值的参数。  
  
 下面的示例生成 C3747：  
  
```  
// C3747.cpp  
template <class T1 = int, class T2>   // C3747  
struct MyStruct {};  
```  
  
 可能的解决方案：  
  
```  
// C3747b.cpp  
// compile with: /c  
template <class T1, class T2 = int>  
struct MyStruct {};  
```