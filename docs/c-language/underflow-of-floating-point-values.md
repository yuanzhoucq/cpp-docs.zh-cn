---
title: "浮点值的下溢 | Microsoft Docs"
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
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 浮点值的下溢
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.5.1** 对于下溢范围错误，数学函数是否将整数表达式 `errno` 设置为宏 `ERANGE` 的值  
  
 浮点下溢不会将表达式 `errno` 设置为 `ERANGE`。  当值接近零且最终下溢时，该值将设置为零。  
  
## 请参阅  
 [库函数](../c-language/library-functions.md)