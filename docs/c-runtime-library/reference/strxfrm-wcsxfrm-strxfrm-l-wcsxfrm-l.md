---
title: "strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strxfrm"
  - "_wcsxfrm_l"
  - "_strxfrm_l"
  - "wcsxfrm"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strxfrm"
  - "_tcsxfrm"
  - "wcsxfrm"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strxfrm_l 函数"
  - "_tcsxfrm 函数"
  - "_wcsxfrm_l 函数"
  - "字符串比较 [C++], 转换字符串"
  - "字符串 [C++], 比较区域设置"
  - "strxfrm 函数"
  - "strxfrm_l 函数"
  - "tcsxfrm 函数"
  - "wcsxfrm 函数"
  - "wcsxfrm_l 函数"
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基于特定的区域设置信息转换字符串。  
  
## 语法  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `strDest`  
 目标字符串。  
  
 `strSource`  
 源字符串。  
  
 `count`  
 将字符最大数放置到 `strDest`*.*  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回转换字符串的长度，不计空终止字符。  如果返回值大于或等于 `count`， `strDest` 的内容是无法预计的。  对于一个错误，每个函数将设置为 `errno` 并返回 `INT_MAX`。  对于无效字符，`errno` 设置为 `EILSEQ`。  
  
## 备注  
 `strxfrm` 函数将由 `strSource` 指向的字符串转换成存储在 `strDest`中的新的分页表格。  仅仅是`count` 字符，其中包括空字符，被转换并放置到结果字符串。  使用区域设置的 `LC_COLLATE` 类别设置进行转换。  有关`LC_COLLATE`的详细信息, 请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  `strxfrm` 为其独立区域设置行为使用当前区域设置；`_strxfrm_l` 相同，除了它使用区域设置传递而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 转换之后，使用两个转换字符串对 `strcmp` 的调用使用让产生的结果与应用于两个原始字符串 `strcoll` 的调用是相同的。  与 `strcoll` 和 `stricoll`类似，`strxfrm` 自动处理相应的多字节字符串。  
  
 `wcsxfrm` 是 `strxfrm`的宽字符版本；`wcsxfrm` 的字符串参数是宽指针。  对于`wcsxfrm`，字符串转换之后，使用两个转换字符串对 `wcscmp` 的调用产生的结果与应用于两个原始字符串对`wcscoll` 的调用是相同的。  `wcsxfrm` 和 `strxfrm` 行为相同，否则。  对于区域设置独立行为，`wcsxfrm` 使用当前区域设置；`_wcsxfrm_l` 使用区域设置传递而不是当前区域设置。  
  
 这些函数验证其参数。  如果 `strSource` 为空指针，或 `strDest` 为空指针 \(除非计数为零\)，或者如果 `count` 大于 `INT_MAX`，则调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`INT_MAX`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 在“C”区域设置，在字符集中的字符顺序 \(ASCII 字符集\) 和字典序中的字符顺序是一样的。  但是，在其他区域设置中，字符集的字符顺序可能不同于字典字符顺序。  例如，在某些欧洲区域设置，在字符集中，字符“a”\(值 0x61\) 位于字符 '&\#x00E4;' \(值 0xE4\)之前，但是，在字典序列中，字符“ä”在字符" a ”之前。  
  
 在字符集和字典字符顺序不同的区域设置中，根据当前区域设置的 `LC_COLLATE` 类别设置，在原始字符串上使用 `strxfrm` ，然后在结果字符串上使用 `strcmp` 生成一个字典字符串进行比较。  因此，在上面的区域设置中字典序地比较两个字符串，请在原始字符串上使用 `strxfrm`，然后在结果字符串上使用 `strcmp`。  或者，在原字符串上可以使用 `strcoll` 而不是 `strcmp`。  
  
 `strxfrm` 基本上是以 `LCMAP_SORTKEY` 围绕 [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) 的一个包装类。  
  
 以下表达式的值是需要保持源字符串`strxfrm` 的转换的数组大小：  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 只有在“C”区域设置，`strxfrm` 等效于以下的：  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strxfrm`|\<string.h\>|  
|`wcsxfrm`|\<string.h\> 或 \<wchar.h\>|  
|`_strxfrm_l`|\<string.h\>|  
|`_wcsxfrm_l`|\<string.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)