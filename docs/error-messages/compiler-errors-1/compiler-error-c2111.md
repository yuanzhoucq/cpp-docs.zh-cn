---
title: "编译器错误 C2111 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2111"
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2111
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"\+": 指针加法要求整型操作数  
  
 试图使用加号 \(`+`\) 运算符将非整型值添加到指针。  
  
 下面的示例生成 C2111：  
  
```  
// C2111.cpp int main() { int *a = 0, *pa = 0, b = 0; double d = 0.00; a = pa + d;   // C2111 a = pa + b;   // OK }  
```