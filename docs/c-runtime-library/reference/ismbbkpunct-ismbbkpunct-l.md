---
title: "_ismbbkpunct、_ismbbkpunct_l | Microsoft Docs"
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
  - "_ismbbkpunct_l"
  - "_ismbbkpunct"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ismbbkpunct_l"
  - "_ismbbkpunct_l"
  - "ismbbkpunct"
  - "_ismbbkpunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbbkpunct_l 函数"
  - "ismbbkpunct_l 函数"
  - "ismbbkpunct 函数"
  - "_ismbbkpunct 函数"
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbkpunct、_ismbbkpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检查多字节字符是否为标点字符。  
  
## 语法  
  
```  
int _ismbbkpunct(  
   unsigned int c   
);  
int _ismbbkpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果整数 `c` 为非 ASCII 标点符号，则 `_ismbbkpunct` 返回非零整数；如果它不为非 ASCII 标点符号，则返回 0。 例如，仅在代码页 932 中，`_ismbbkpunct` 测试片假名标点。`_ismbbkpunct` 对与区域设置相关的所有字符设置使用当前区域设置。`_ismbbkpunct_l` 是相同的，但它使用传入的区域设置。 有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbbkpunct`|\<mbctype.h\>|  
|`_ismbbkpunct_l`|\<mbctype.h\>|  
  
 有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)