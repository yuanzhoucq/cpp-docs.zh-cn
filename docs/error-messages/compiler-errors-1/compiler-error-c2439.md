---
title: "编译器错误 C2439 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2439"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2439"
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2439
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 未能初始化成员  
  
 无法初始化类成员、结构成员或联合成员。  
  
### 通过检查以下可能的原因进行修复  
  
1.  尝试初始化间接基类或结构。  
  
2.  尝试初始化类或结构的继承成员。  继承成员必须由类或结构的构造函数进行初始化。