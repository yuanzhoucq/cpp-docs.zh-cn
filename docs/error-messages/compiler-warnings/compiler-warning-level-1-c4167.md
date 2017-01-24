---
title: "编译器警告（等级 1）C4167 | Microsoft Docs"
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
  - "C4167"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4167"
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4167
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数：仅可用作内部函数  
  
 **\#pragma 函数**尝试强制编译器对必须以内部形式使用的函数使用常规调用。 将忽略杂注。  
  
 若要避免此警告，请删除 **\#pragma 函数**。  
  
## 示例  
  
```  
// C4167.cpp // compile with: /W1 #include <malloc.h> #pragma function(_alloca )   // C4167: _alloca() is intrinsic only int main(){}  
```