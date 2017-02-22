---
title: "_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbcjistojms"
  - "_mbcjmstojis"
  - "_mbcjistojms_l"
  - "_mbcjmstojis_l"
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
  - "mbcjistojms"
  - "_mbcjistojms"
  - "_mbcjistojms_l"
  - "_mbcjmstojis_l"
  - "_mbcjmstojis"
  - "mbcjmstojis_l"
  - "mbcjistojms_l"
  - "mbcjmstojis"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbcjistojms 函数"
  - "_mbcjistojms_l 函数"
  - "_mbcjmstojis 函数"
  - "_mbcjmstojis_l 函数"
  - "mbcjistojms 函数"
  - "mbcjistojms_l 函数"
  - "mbcjmstojis 函数"
  - "mbcjmstojis_l 函数"
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在Japan Industry Standard \(JIS\) 和Japan Microsoft \(JMS\) 字符之间转换。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
unsigned int _mbcjistojms(  
   unsigned int c   
);  
unsigned int _mbcjistojms_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbcjmstojis(  
   unsigned int c   
);  
unsigned int _mbcjmstojis_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要转换的字符。  
  
 `local`  
 要使用的区域设置。  
  
## 返回值  
 在日语区域设置中，如果转换是不可能的，这些函数返回一个转换的字符或返回 0。  在是非日语区域设置中，这些函数返回传递的字符。  
  
## 备注  
 `_mbcjistojms` 函数将Japan Industry Standard \(JIS\) 字符转换为Microsoft Kanji \(Shift JIS\) 字符。  只有当主管和试用字节范围在 0x21 – 0x7E，字符才转换。  如果主管或试用字节是此范围外，`errno` 设置为 `EILSEQ`。  有关此更改和其他错误代码的详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `_mbcjmstojis` 函数将 Shift JIS 字符转换为 JIS 字符。  只有当前导字节范围在 0x81 – 0x9F 或 0xE0 – 0xFC，并且尾字节范围在 0x40 – 0x7E 或 0x80 – 0xFC，字符才转换。  请注意在该范围内某些码位没有字符分配，所以未能转换。  
  
 该值 `c` 应有16位值，它的高 8 位字符表示要转换的前导字节，而低 8 位表示末尾字节。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在早期版本中，`_mbcjistojms` 和 `_mbcjmstojis` 分别调用`jistojms` 和 `jmstojis`。  应改用 `_mbcjistojms`,`_mbcjistojms_l`,`_mbcjmstojis` 和 `_mbcjmstojis_l` 。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbcjistojms`|\<mbstring.h\>|  
|`_mbcjistojms_l`|\<mbstring.h\>|  
|`_mbcjmstojis`|\<mbstring.h\>|  
|`_mbcjmstojis_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)