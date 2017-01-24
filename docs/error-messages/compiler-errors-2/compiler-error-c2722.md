---
title: "编译器错误 C2722 | Microsoft Docs"
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
  - "C2722"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2722"
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2722
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“::operator”: 后面的运算符命令非法；使用“operator operator”  
  
 `operator` 语句重定义 `::new` 或 `::delete`。  `new` 和 `delete` 运算符是全局运算符，所以范围解析运算符 \(`::`\) 无意义。  移除 `::` 运算符。