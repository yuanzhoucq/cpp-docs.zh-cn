---
title: "_ismbbtrail、_ismbbtrail_l | Microsoft Docs"
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
  - "_ismbbtrail"
  - "_ismbbtrail_l"
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
  - "_ismbbtrail"
  - "ismbbtrail"
  - "_ismbbtrail_l"
  - "ismbbtrail_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ismbbtrail_l 函数"
  - "_ismbbtrail 函数"
  - "_ismbbtrail_l 函数"
  - "ismbbtrail 函数"
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbtrail、_ismbbtrail_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定一个字节是否为多字节字符的尾随字节。  
  
## 语法  
  
```  
int _ismbbtrail(  
   unsigned int c   
);  
int _ismbbtrail_l(  
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
 如果整数 `_ismbbtrail` 为一个多字节字符的第二个字节，则 `c` 将返回一个非零值。 例如，仅在代码页 932 中，有效范围为 0x40 到 0x7E 以及 0x80 到 0xFC。  
  
## 备注  
 `_ismbbtrail` 对与区域设置相关的行为使用当前区域设置。`_ismbbtrail_l` 具有相同的效果，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_ismbbtrail`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbbtrail_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
  
 \* 适用于测试条件的清单常量。  
  
 有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)