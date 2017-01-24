---
title: "程序终止中的 return 语句 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据类型 [C++], 函数返回类型"
  - "函数返回类型, return 语句"
  - "return 关键字 [C++], 语法"
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 程序终止中的 return 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 **main** 发出 `return` 语句在功能上等效于调用 **exit** 函数。  请看下面的示例：  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 上面的示例中的 **exit** 和 `return` 语句的功能相同。  但是，C\+\+ 需要具有 `void` 之外的返回类型的函数返回一个值。  `return` 语句允许您从 **main** 中返回一个值。  
  
## 请参阅  
 [程序终止](../cpp/program-termination.md)