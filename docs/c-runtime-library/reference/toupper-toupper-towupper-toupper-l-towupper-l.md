---
title: "toupper、_toupper、towupper、_toupper_l、_towupper_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_toupper_l"
  - "towupper"
  - "toupper"
  - "_towupper_l"
  - "_toupper"
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
  - "towupper"
  - "_toupper"
  - "_totupper"
  - "toupper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_totupper 函数"
  - "_toupper 函数"
  - "_toupper_l 函数"
  - "_towupper_l 函数"
  - "大小写, 转换"
  - "字符, 转换"
  - "字符串转换, 大小写"
  - "字符串转换, 为不同的字符"
  - "totupper 函数"
  - "toupper 函数"
  - "toupper_l 函数"
  - "towupper 函数"
  - "towupper_l 函数"
  - "大写, 将字符串转换为"
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# toupper、_toupper、towupper、_toupper_l、_towupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

要转换为大写的字符。  
  
## 语法  
  
```  
int toupper(  
   int c   
);  
int _toupper(  
   int c   
);  
int towupper(  
   wint_t c   
);  
int _toupper_l(  
   int c ,  
   _locale_t locale  
);  
int _towupper_l(  
   wint_t c ,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要转换的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些例程每个转换 `c`复制，如果可能，然后返回结果。  
  
 如果 `c` 是 `iswlower` 是非零的宽字符，并使 `iswupper` 不为零，`towupper` 返回相应的宽字符对应的宽字符；否则，`towupper` 返回未更改的 `c`。  
  
 没有保留任何返回值以指示错误。  
  
 为了使 `toupper` 可以提供预期结果、[\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 和 [isupper](../../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md) 必须同时非零返回。  
  
## 备注  
 如果可能且合适，每个这些例程中转换一个特定小字母转换为大写字母。  `towupper` 的用例转换特定于区域设置。  在用例中仅与当前区域设置相关的字符被更改。  没有 `_l`  后缀的函数使用当前设置的区域设置。  这些函数的版本有 `_l`  后缀将区域设置作为参数并使用它们来代替当前设置的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 为了使 `toupper` 可以提供预期结果、[\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 和 [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) 必须同时非零返回。  
  
 [数据转换例程](../../c-runtime-library/data-conversion.md)  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE  & 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|--------------------------------|----------------|-------------------|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`_toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
> [!NOTE]
>  `_toupper_l` 和 `_towupper_l` 没有区域设置依赖项，且不应该直接调用。  它们提供`_totupper_l`的内部使用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`toupper`|\<ctype.h\>|  
|`_toupper`|\<ctype.h\>|  
|`towupper`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 参见 [指向函数](../../c-runtime-library/to-functions.md)的示例。  
  
## .NET Framework 等效项  
 [System::Char::ToUpper](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)  
  
## 请参阅  
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [to 函数](../../c-runtime-library/to-functions.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)