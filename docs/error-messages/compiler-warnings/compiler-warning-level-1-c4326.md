---
title: "编译器警告（等级 1）C4326 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4326"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4326"
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4326
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”的返回类型应为“type1”而非“type2”  
  
 函数返回了 ***type1*** 以外的类型。  例如，使用 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 时，main 没有返回 `int`。  
  
 下面的示例生成 C4326：  
  
```  
// C4326.cpp  
// compile with: /Za /W1  
char main()  
{   // C4326 try int main  
}  
```