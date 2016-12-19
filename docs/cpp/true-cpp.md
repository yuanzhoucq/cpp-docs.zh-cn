---
title: "true (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "true_cpp"
  - "true"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "true 关键字 [C++]"
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# true (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
        bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## 备注  
 此关键字是类型 [bool](../cpp/bool-cpp.md) 的变量或条件表达式（条件表达式现在是值为 true 的 Boolean 表达式）的两个值之一。  如果 `i` 的类型为 `bool`，则 `i = true;` 语句会将 **true** 赋给 `i`。  
  
## 示例  
  
```  
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
  **1**  
**0**   
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)