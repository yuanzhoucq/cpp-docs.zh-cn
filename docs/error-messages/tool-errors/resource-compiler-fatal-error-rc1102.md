---
title: "资源编译器错误 RC1102 | Microsoft Docs"
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
  - "RC1102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1102"
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC1102
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内部错误 : RCPP 的参数太多  
  
 传递到资源编译器预处理器的参数太多。  通过在源中进行定义，减少用“定义符号”\(\/d\) 选项定义的符号数。  若使用“包括搜索路径”选项 \(\/i\) 指定太多的包含文件搜索路径，也会导致该错误。