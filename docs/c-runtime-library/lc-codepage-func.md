---
title: "___lc_codepage_func | Microsoft Docs"
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
  - "___lc_codepage_func"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lc_codepage_func"
  - "___lc_codepage_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_codepage_func"
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ___lc_codepage_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内部 CRT 函数。  检索线程的当前代码页。  
  
## 语法  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## 返回值  
 线程的当前代码页。  
  
## 备注  
 `___lc_codepage_func` 是一个内部 CRT 函数，其他 CRT 函数可将其用于从 CRT 数据的线程本地存储中获取当前代码页。  也可通过使用 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md) 函数提供此信息。  
  
 *代码页*是单字节或双字节代码到单独字符的映射。  不同的代码页包含不同的特殊字符，通常会对一种语言或一组语言进行自定义。  有关代码页的详细信息，请参见[代码页](../c-runtime-library/code-pages.md)。  
  
 内部 CRT 函数特定于实现且会根据每个发行版本发生更改。  不建议在代码中使用它们。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`___lc_codepage_func`|crt\\src\\setlocal.h|  
  
## 请参阅  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)