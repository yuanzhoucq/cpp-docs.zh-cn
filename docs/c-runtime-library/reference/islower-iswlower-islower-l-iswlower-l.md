---
title: "islower、iswlower、_islower_l、_iswlower_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswlower"
  - "_islower_l"
  - "islower"
  - "_iswlower_l"
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
  - "_istlower"
  - "islower"
  - "_ismbclower_l"
  - "_liswlower_l"
  - "_istlower_l"
  - "_iswlower_l"
  - "_islower _l"
  - "_islower_l"
  - "iswlower"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_islower _l 函数"
  - "_islower_l 函数"
  - "_ismbclower_l 函数"
  - "_istlower 函数"
  - "_istlower_l 函数"
  - "_iswlower_l 函数"
  - "_liswlower_l 函数"
  - "islower 函数"
  - "istlower 函数"
  - "iswlower 函数"
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# islower、iswlower、_islower_l、_iswlower_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示小写字母。  
  
## 语法  
  
```  
int islower(  
   int c   
);  
int iswlower(  
   wint_t c   
);  
int islower_l(  
   int c,  
   _locale_t locale  
);  
int _iswlower_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `c` 是小写字母的特定表示，则每个实例返回非零值。  如果 `c` 是一个小写字母 \(a\-z\)，`islower` 返回一个非零值，。  如果 `c` 是对应于一个小写字母的宽字符，或者，如果 `c` 是宽字符的现实定义集，其中`iswcntrl`、`iswdigit`、`iswpunct`或 `iswspace` 都是非零，则`iswlower` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回 0。  
  
 这些带有 `_l` 后缀的函数的版本使用传递的区域设置，而不是与区域设置行为相关的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c`不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），则`islower`和`_islower_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istlower`|`islower`|[\_ismbclower](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswlower`|  
|`_istlower_l`|`_islower _l`|[\_ismbclower\_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_liswlower_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`islower`|\<ctype.h\>|  
|`iswlower`|\<ctype.h\> 或 \<wchar.h\>|  
|`_islower_l`|\<ctype.h\>|  
|`_swlower_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsLower](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)