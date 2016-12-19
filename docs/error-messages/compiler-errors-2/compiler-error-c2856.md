---
title: "编译器错误 C2856 | Microsoft Docs"
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
  - "C2856"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2856"
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2856
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma hdrstop 不能在 \#if 块内  
  
 `hdrstop` 杂注不能放在条件编译块体中。  
  
 请将 `#pragma hdrstop` 语句移至 `#if/#endif` 块不包含的区域。