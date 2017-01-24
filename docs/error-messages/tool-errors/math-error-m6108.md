---
title: "数学错误 M6108 | Microsoft Docs"
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
  - "M6108"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6108"
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 数学错误 M6108
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

平方根  
  
 平方根运算中操作数为负数。  
  
 程序以退出代码 136 终止。  
  
> [!NOTE]
>  C 运行库中的 `sqrt` 函数和 FORTRAN 内部函数 **SQRT** 不生成该错误。  C `sqrt` 函数在执行操作之前检查参数，如果操作数为负数则返回一个错误值。  FORTRAN **SQRT** 函数生成 DOMAIN 错误 [M6201](../../error-messages/tool-errors/math-error-m6201.md) 而不是该错误。