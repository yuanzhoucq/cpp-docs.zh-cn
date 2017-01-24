---
title: "_ismbbpunct、_ismbbpunct_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbpunct"
  - "_ismbbpunct_l"
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
  - "ismbbpunct"
  - "ismbbpunct_l"
  - "_ismbbpunct_l"
  - "_ismbbpunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ismbbpunct 函数"
  - "_ismbbpunct 函数"
  - "ismbbpunct_l 函数"
  - "_ismbbpunct_l 函数"
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbpunct、_ismbbpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定特定字符是否为标点字符。  
  
## 语法  
  
```  
int _ismbbpunct(  
   unsigned int c   
);  
int _ismbbpunct_l(  
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
 如果整数 `_ismbbpunct` 是非 ASCII 标点符号，则 `c` 将返回非零值。`_ismbbpunct` 对与区域设置相关的所有字符设置使用当前区域设置。`_ismbbpunct_l` 是相同的，但它使用传入的区域设置。 有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbbpunct`|\<mbctype.h\>|  
|`_ismbbpunct_l`|\<mbctype.h\>|  
  
 有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)