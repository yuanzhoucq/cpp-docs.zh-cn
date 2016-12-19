---
title: "编译器错误 C3196 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3196"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3196"
ms.assetid: d9c38a13-191d-472d-aa2b-f61a6459d16c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3196
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“keyword”: 使用了多次  
  
 某关键字被使用了多次。  
  
 下面的示例生成 C3196：  
  
```  
// C3196.cpp  
// compile with: /clr  
ref struct R abstract abstract {};   // C3196  
ref struct S abstract {};   // OK  
```