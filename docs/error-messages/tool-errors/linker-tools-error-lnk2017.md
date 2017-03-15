---
title: "链接器工具错误 LNK2017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2017"
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK2017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

没有 \/LARGEADDRESSAWARE:NO，“symbol”到“segment”的重定位无效  
  
 您尝试生成具有 32 位地址的 64 位图像。  为此，必须：  
  
-   使用固定加载地址。  
  
-   将图像限制为 3 GB。  
  
-   指定 [\/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md)。