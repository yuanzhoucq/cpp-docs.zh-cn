---
title: "表达式计算器错误 CXX0024 | Microsoft Docs"
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
  - "CXX0024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0024"
  - "CXX0024"
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

操作要求左值  
  
 为需要左值的操作指定了计算结果不是左值的表达式。  
  
 左值（因出现在赋值语句左端而得名）是引用内存位置的表达式。  
  
 例如，`buffer[count]` 是一个有效左值，因为它指向特定的内存位置。  逻辑比较 `zed != 0` 不是一个有效左值，因为它的计算结果是 TRUE 或 FALSE 而不是内存地址。  
  
 该错误与 CAN0024 相同。