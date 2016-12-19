---
title: "false (C++) | Microsoft Docs"
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
  - "false_cpp"
  - "false"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "false 关键字 [C++]"
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# false (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

关键字是类型 [bool](../cpp/bool-cpp.md) 的变量或条件表达式（条件表达式现为 **true** Boolean 表达式）的两个值之一。  例如，如果 `i` 是类型 `bool` 的变量，则 `i = false;` 语句将 **false** 分配给 `i`。  
  
## 示例  
  
```  
// bool_false.cpp  
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