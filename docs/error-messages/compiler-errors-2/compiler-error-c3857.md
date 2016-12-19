---
title: "编译器错误 C3857 | Microsoft Docs"
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
  - "C3857"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3857"
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3857
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 不允许使用多个类型参数列表  
  
 不允许为同一类型指定多个模板或泛型。  
  
 下面的示例生成 C3857：  
  
```  
// C3857.cpp  
template <class T, class TT>  
template <class T2>    // C3857  
struct B {};  
```  
  
 可能的解决方案：  
  
```  
// C3857b.cpp  
// compile with: /c  
template <class T, class TT, class T2>   
struct B {};  
```  
  
 使用以下泛型时也可能发生 C3857 错误：  
  
```  
// C3857c.cpp  
// compile with: /clr  
generic <typename T>  
generic <typename U>  
ref class GC;   // C3857  
```  
  
 可能的解决方案：  
  
```  
// C3857d.cpp  
// compile with: /clr /c  
generic <typename U>  
ref class GC;  
```