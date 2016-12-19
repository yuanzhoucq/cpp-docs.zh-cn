---
title: "链接器工具警告 LNK4092 | Microsoft Docs"
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
  - "LNK4092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4092"
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

共享的可写节“section”包含重定位；映像可能不能正确运行  
  
 只要您有共享节，链接器就发出此警告以提醒您潜在的严重问题。  
  
 在多个进程之间共享数据的一种方法是将节标记为“共享”。但是将节标记为共享会导致问题。  例如，您的 DLL 在共享数据节中包含类似下面的声明：  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 链接器无法解析 `pvar`，因为其值取决于 DLL 在内存中的加载位置，因此它在 DLL 中放入一个重定位记录。  当 DLL 加载到内存中时，`var` 的地址可被解析，并分配 `pvar`。  如果另一个进程加载同一个 DLL 但无法在相同的地址加载它，则 `var` 地址的重定位将为第二个进程更新，并且第一个进程的地址空间将指向错误的地址。