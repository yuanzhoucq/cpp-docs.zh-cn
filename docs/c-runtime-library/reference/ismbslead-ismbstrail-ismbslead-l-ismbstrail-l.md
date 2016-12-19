---
title: "_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbstrail"
  - "_ismbslead_l"
  - "_ismbslead"
  - "_ismbstrail_l"
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
  - "_ismbslead"
  - "ismbs"
  - "ismbslead_l"
  - "_ismbs"
  - "ismbstrail_l"
  - "ismbslead"
  - "_ismbstrail"
  - "_ismbstrail_l"
  - "ismbstrail"
  - "_ismbslead_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbslead 函数"
  - "_ismbslead_l 函数"
  - "_ismbstrail 函数"
  - "_ismbstrail_l 函数"
  - "ismbslead 函数"
  - "ismbslead_l 函数"
  - "ismbstrail 函数"
  - "ismbstrail_l 函数"
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对多字节字符串前导字节和结尾字节执行上下文相关测试，并确定给定子字符串指针指向前导字节还是结尾字节。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _ismbslead(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbstrail(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbslead_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
int _ismbstrail_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 指向字符串开头或之前已知的前导字节的指针。  
  
 `current`  
 指向要测试的字符串中位置的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果字符是前导字节，则 `_ismbslead` 将返回 \-1；如果字符为结尾字节，则 `_ismbstrail` 将返回 \-1。  如果输入字符串有效，但不是前导字节也不是结尾字节，则这些函数将返回零。  如果任一参数为 `NULL`，则将调用无效的参数处理程序，正如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## 备注  
 `_ismbslead` 和 `_ismbstrail` 慢于 `_ismbblead` 和 `_ismbbtrail` 版本，因为前二者会将字符串文本考虑进去。  
  
 前缀为 `_l` 的函数的版本相同，但其依赖区域设置的行为除外，它们可使用已传入的区域设置代替当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_ismbslead`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbstrail`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbslead_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbstrail_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
  
 \* 适用于测试条件的清单常数。  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [\_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)