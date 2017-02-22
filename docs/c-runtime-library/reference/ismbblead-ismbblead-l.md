---
title: "_ismbblead、_ismbblead_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbblead_l"
  - "_ismbblead"
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
  - "ismbblead_l"
  - "istlead"
  - "_ismbblead"
  - "_ismbblead_l"
  - "ismbblead"
  - "_istlead"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ismbblead_l 函数"
  - "ismbblead 函数"
  - "_ismbblead 函数"
  - "istlead 函数"
  - "ismbblead_l 函数"
  - "_istlead 函数"
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _ismbblead、_ismbblead_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

测试字符，以确定它是否是多字节字符的前导字节。  
  
## 语法  
  
```  
int _ismbblead(  
   unsigned int c   
);  
int _ismbblead_l(  
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
 如果整数 `c` 为一个多字节字符的第一个字节，则返回一个非零值。  
  
## 备注  
 多字节字符由前导字节后跟尾随字节构成。 通过在给定字符集中的特定范围来辨别前导字节。 例如，前导字节范围为 0x81 – 0x9F 和 0xE0 – 0xFC（仅在代码页 932 中）。  
  
 `_ismbblead` 对与区域设置相关的行为使用当前区域设置。`_ismbblead_l` 具有相同的效果，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istlead`|始终返回 false|`_ismbblead`|始终返回 false|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_ismbblead`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbblead_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
  
 \* 适用于测试条件的清单常量。  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)