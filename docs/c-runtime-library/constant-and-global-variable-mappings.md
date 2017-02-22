---
title: "常量和全局变量映射 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_tenviron"
  - "_TEOF"
  - "_tfinddata_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tenviron 函数"
  - "_TEOF 类型"
  - "_tfinddata_t 函数"
  - "一般文本映射"
  - "tenviron 函数"
  - "TEOF 类型"
  - "tfinddatat 函数"
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 常量和全局变量映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些一般文本、常数全局变量和标准类型d\=定义在 TCHAR.H 中并由常数 `_UNICODE` 或 `_MBCS` 在程序中定义。  
  
### 一般文本常数和全局变量映射  
  
|一般文本 \- 对象名称|SBCS \(\_UNICODE, \_MBCS 未定义\)|已定义 \_MBCS|已定义 \_UNICODE|  
|------------------|------------------------------------|----------------|-------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## 请参阅  
 [一般文本映射](../c-runtime-library/generic-text-mappings.md)   
 [数据类型映射](../c-runtime-library/data-type-mappings.md)   
 [例程映射](../c-runtime-library/routine-mappings.md)   
 [简单一般文本项目](../c-runtime-library/a-sample-generic-text-program.md)   
 [使用一般文本映射](../c-runtime-library/using-generic-text-mappings.md)