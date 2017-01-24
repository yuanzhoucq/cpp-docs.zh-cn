---
title: "___lc_collate_cp_func | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "___lc_collate_cp_func"
apilocation: 
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___lc_collate_cp_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_collate_cp_func"
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ___lc_collate_cp_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内部 CRT 函数。  检索线程的当前排序规则代码页。  
  
## 语法  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## 返回值  
 线程的当前排序规则代码页。  
  
## 备注  
 `___lc_collate_cp_func` 是一个内部 CRT 函数，其他 CRT 函数可将其用于从 CRT 数据的线程本地存储中获取当前排序规则代码页。  也可通过使用 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md) 函数提供此信息。  
  
 内部 CRT 函数特定于实现且会根据每个发行版本发生更改。  不建议在代码中使用它们。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`___lc_collate_cp_func`|crt\\src\\setlocal.h|  
  
## 请参阅  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)