---
title: "编译器警告（等级 1）C4048 | Microsoft Docs"
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
  - "C4048"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4048"
ms.assetid: 8429f513-4732-40f1-8e56-4c224e723bcb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4048
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

声明的数组下标不同 :“identifier1”和“identifier2”  
  
 表达式涉及指向不同大小的数组的指针。  使用指针时不进行转换。  
  
 如果显式将数组强制转换为相同或等效的类型，则可能修复此警告。