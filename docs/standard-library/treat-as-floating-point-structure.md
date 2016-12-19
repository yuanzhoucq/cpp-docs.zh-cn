---
title: "treat_as_floating_point 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::treat_as_floating_point"
dev_langs: 
  - "C++"
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
caps.latest.revision: 13
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# treat_as_floating_point 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 `Rep` 是否可以被视为一个浮点类型。  
  
## 语法  
  
```  
template<class Rep>  
struct treat_as_floating_point : is_floating_point<Rep>;  
```  
  
## 备注  
 `Rep` 可视为一个浮点类型，只有当专业化 `treat_as_floating_point<Rep>` 来自 [true\_type](../Topic/true_type%20Typedef.md).  模板类可用于一个用户定义的类型专用化。  
  
## 要求  
 **Header:** chrono  
  
 **Namespace:** std::chrono  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)