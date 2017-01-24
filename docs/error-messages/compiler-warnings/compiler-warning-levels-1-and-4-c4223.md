---
title: "编译器警告（等级 1 和等级 4）C4223 | Microsoft Docs"
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
  - "C4223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4223"
ms.assetid: 6fc44336-0250-4432-928b-fc5dbe7b7c1c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1 和等级 4）C4223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 将不是 lvalue 的数组转换为指针  
  
 在标准 C 中，不能将非 lvalue 数组转换为指针。  在默认 Microsoft 扩展 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\) 下则可以这样转换。