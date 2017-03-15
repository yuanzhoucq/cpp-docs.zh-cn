---
title: "编译器警告（等级 1）C4042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4042"
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 有坏的存储类  
  
 在此上下文中，指定的存储类不能与该标识符一起使用。  编译器改用默认的存储类：  
  
-   `extern`（如果 *identifier* 是函数）。  
  
-   **auto**（如果 *identifier* 是形参或局部变量）。  
  
-   无存储类（如果 *identifier* 是全局变量）。  
  
 当在参数声明中指定 **register** 之外的存储类时便会出现此警告。  
  
 下面的示例生成 C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```