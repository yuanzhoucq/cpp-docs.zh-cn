---
title: "编译器错误 C2110 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2110"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2110"
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2110
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\+L”：不能添加两个指针  
  
 尝试使用加号 \(`+`\) 运算符添加两个指针值。  
  
 以下示例生成 C2110：  
  
```  
// C2110.cpp int main() { int a = 0; int *pa; int *pb; a = pa + pb;   // C2110 }  
```