---
title: "isupper、_isupper_l、iswupper、_iswupper_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "isupper"
  - "iswupper"
  - "_iswupper_l"
  - "_isupper_l"
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
  - "isupper"
  - "_istupper"
  - "iswupper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_istupper 函数"
  - "_isupper_l 函数"
  - "_iswupper_l 函数"
  - "istupper 函数"
  - "isupper 函数"
  - "isupper_l 函数"
  - "iswupper 函数"
  - "iswupper_l 函数"
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# isupper、_isupper_l、iswupper、_iswupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示大写字母。  
  
## 语法  
  
```  
int isupper(  
   int c   
);  
int _isupper_l (  
   int c,  
   _locale_t locale  
);  
int iswupper(  
   wint_t c   
);  
int _iwsupper_l(  
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
 如果 `c` 是大写字母的特定表示，其中每个实例返回非零。  如果 `c` 是一个大写字母 \(A\-Z\)，`isupper` 返回一个非零值。  如果 `c` 是对应于一个大写字母的宽字符，或者，如果 `c` 是宽字符的现实定义集，其中`iswcntrl`、`iswdigit`、`iswpunct`或 `iswspace` 都是非零，则`iswupper` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回 0。  
  
 这些带有 `_l` 后缀的函数的版本使用传递的区域设置，而不是与区域设置行为相关的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c`不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`isupper` 和 `_isupper_l` 的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istupper`|`isupper`|[\_ismbcupper](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswupper`|  
|`_istupper_l`|`_isupper_l`|[\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_iswupper_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isupper`|\<ctype.h\>|  
|`_isupper_l`|\<ctype.h\>|  
|`iswupper`|\<ctype.h\> 或 \<wchar.h\>|  
|`_iswupper_l`|\<ctype.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsUpper](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)