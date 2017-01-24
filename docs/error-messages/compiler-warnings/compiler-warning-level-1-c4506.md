---
title: "编译器警告（等级 1）C4506 | Microsoft Docs"
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
  - "C4506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4506"
ms.assetid: aa682869-65d1-4dad-ba32-198f10b44f91
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内联函数“function”没有定义  
  
 声明了给定函数并将其标记为了内联，但没有定义它。  
  
 编译器没有内联该函数。  
  
 请确保用 `extern` 关键字声明要内联的外部函数。