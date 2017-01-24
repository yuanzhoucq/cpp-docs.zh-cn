---
title: "编译器警告（等级 3）C4306 | Microsoft Docs"
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
  - "C4306"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4306"
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4306
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**“**   
 ***identifier* ”：从“**   
 ***type1* ”转换到更大的“**   
 ***type2* ”**  
  
 标识符的类型转换为更大的指针。  新类型中未填充的高位将用零填充。  
  
 此警告可能表明有不必要的转换。  结果指针可能无效。