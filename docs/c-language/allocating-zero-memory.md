---
title: "分配零内存 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存分配, 零内存"
  - "零内存"
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 分配零内存
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.10.3** 请求的大小为零时，`calloc`、`malloc` 或 `realloc` 函数的行为  
  
 `calloc`、`malloc` 和 `realloc` 函数接受零作为参数。  不分配实际内存，但会返回有效的指针，并且之后可通过 realloc 修改内存块。  
  
## 请参阅  
 [库函数](../c-language/library-functions.md)