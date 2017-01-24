---
title: "编译器错误 C2616 | Microsoft Docs"
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
  - "C2616"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2616"
ms.assetid: 8d0c02d6-a0b0-4135-b10f-438d67da68c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2616
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“conversion”: 不能隐式地将不是 lvalue 的“type1”转换为不是常数的“type2”  
  
 无法从非左值初始化引用。  
  
 这在 ANSI 兼容 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是一个错误，而在 Microsoft 扩展 \(**\/Ze**\) 下是一个警告。