---
title: "链接器工具错误 LNK2023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2023"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2023"
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK2023
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

错误的 dll 或入口点 \<dll or entry point\>  
  
 链接器正在加载错误的 msobj90.dll 版本。  确保路径中的 link.exe 和 msobj90.dll 的版本相同。  
  
 可能未提供 msobj90.dll 的依赖项。  msobj90.dll 的依赖项列表是：  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 请检查您的计算机，确定 msobj90.dll 的任何其他副本是否已过期。