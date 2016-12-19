---
title: "编译器警告（等级 1）C4325 | Microsoft Docs"
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
  - "C4325"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4325"
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4325
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**忽略标准节“**   
 ***section* ”的特性**  
  
 您不能更改标准节的特性。  例如：  
  
```  
#pragma section(".sdata", long)  
```  
  
 这会覆盖将 **short** 数据类型与 **long** 数据类型一起使用的 `.sdata` 标准节。  
  
 特性不能被您更改的标准节包括：  
  
-   .data  
  
-   .sdata  
  
-   .bss  
  
-   .sbss  
  
-   .text  
  
-   .const  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 以后可能添加其他的节。  
  
## 请参阅  
 [节](../../preprocessor/section.md)