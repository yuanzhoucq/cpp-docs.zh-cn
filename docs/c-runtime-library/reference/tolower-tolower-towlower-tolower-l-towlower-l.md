---
title: "tolower、_tolower、towlower、_tolower_l、_towlower_l | Microsoft Docs"
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
  - "_tolower_l"
  - "towlower"
  - "tolower"
  - "_tolower"
  - "_towlower_l"
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
  - "_totlower"
  - "tolower"
  - "_tolower"
  - "towlower"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tolower 函数"
  - "_tolower_l 函数"
  - "_totlower 函数"
  - "_towlower_l 函数"
  - "大小写, 转换"
  - "字符, 转换"
  - "lowercase, 转换为"
  - "字符串转换, 大小写"
  - "字符串转换, 为不同的字符"
  - "tolower 函数"
  - "tolower_l 函数"
  - "totlower 函数"
  - "towlower 函数"
  - "towlower_l 函数"
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tolower、_tolower、towlower、_tolower_l、_towlower_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符都转换为小写。  
  
## 语法  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### 参数  
 \[in\] `c`  
 要转换的字符。  
  
 \[in\] `locale`  
 为区域特定转换使用区域设置。  
  
## 返回值  
 如果转换可行的，这些例程中的每个 `c` 将转换为小写字符，然后返回结果。  没有保留任何返回值以指示错误。  
  
## 备注  
 如果可能和相关，每个这些例程中转换一个特定大写字母转换为小写字母。  `towlower` 的用例转换特定于区域设置。  在用例中仅与当前区域设置相关的字符被更改。  没有 `_l` 后缀的函数使用当前设置的区域设置。  这些函数的版本有 `_l` 后缀将区域设置作为参数并使用它们来代替当前设置的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 为了使 `_tolower` 可以提供预期结果，[\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 和 [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) 必须同时返回非零。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l` 和 `_towlower_l` 没有区域设置依赖项，且不应该直接调用。  它们提供`_totlower_l`的内部使用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`tolower`|\<ctype.h\>|  
|`_tolower`|\<ctype.h\>|  
|`towlower`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 参见 [指向函数](../../c-runtime-library/to-functions.md)的示例。  
  
## .NET Framework 等效项  
 [System::Char::ToLower](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [to 函数](../../c-runtime-library/to-functions.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)