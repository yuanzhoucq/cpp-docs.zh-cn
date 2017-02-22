---
title: "编译器错误 C2516 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2516"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2516"
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2516
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”: 是非法基类  
  
 该类是从由 `typedef` 语句定义的类型名派生的。  
  
 下面的示例生成 C2516：  
  
```  
// C2516.cpp  
typedef unsigned long ulong;  
class C : public ulong {}; // C2516  
```