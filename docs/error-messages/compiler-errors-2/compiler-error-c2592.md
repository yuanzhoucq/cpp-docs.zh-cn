---
title: "编译器错误 C2592 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2592"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2592"
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2592
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：“base\_class\_2” 继承自“base\_class\_1”，无法重新指定  
  
 你仅可指定不是继承自其他基类的基类。  在此情况下，`class` 的规范中仅需要 `base_class_1`，因为 `base_class_1` 已继承 `base_class_2`。