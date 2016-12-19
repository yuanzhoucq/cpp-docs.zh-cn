---
title: "编译器错误 C2129 | Microsoft Docs"
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
  - "C2129"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2129"
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2129
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

静态函数“function”已声明但未定义  
  
 对从未定义的 `static` 函数进行了前向引用。  
  
 必须在文件范围内定义 `static` 函数。  如果函数是在其他文件中定义的，则必须将其声明为 `extern`。