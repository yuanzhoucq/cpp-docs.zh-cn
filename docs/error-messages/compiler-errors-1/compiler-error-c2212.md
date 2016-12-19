---
title: "编译器错误 C2212 | Microsoft Docs"
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
  - "C2212"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2212"
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2212
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: \_\_based 不可用于指向函数的指针  
  
 指向函数的指针无法声明为 `__based`。  如果需要基于代码的数据，请使用 `__declspec` 关键字或 `data_seg` 杂注。