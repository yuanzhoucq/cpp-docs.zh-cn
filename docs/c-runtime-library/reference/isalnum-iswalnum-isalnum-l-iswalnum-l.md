---
title: "isalnum、iswalnum、_isalnum_l、_iswalnum_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_iswalnum_l"
  - "_isalnum_l"
  - "iswalnum"
  - "isalnum"
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
  - "_istalnum_l"
  - "_iswalnum_l"
  - "iswalnum"
  - "_isalnum_l"
  - "isalnum"
  - "_istalnum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isalnum_l 函数"
  - "_ismbcalnum_l 函数"
  - "_istalnum 函数"
  - "_istalnum_l 函数"
  - "_iswalnum_l 函数"
  - "isalnum 函数"
  - "istalnum 函数"
  - "iswalnum 函数"
ms.assetid: 0dc51306-ade8-4944-af27-e4176fc89093
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# isalnum、iswalnum、_isalnum_l、_iswalnum_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定一个整数是否表示一个字母字符。  
  
## 语法  
  
```  
int isalnum(   
   int c   
);  
int iswalnum(   
   wint_t c   
);  
int _isalnum_l(   
   int c,  
   _locale_t locale  
);  
int _iswalnum_l(   
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
 如果 `c` 是字母字符的特定表示，则每个实例返回非零值。  `isalnum` 返回一个非零值，如果 `isalpha` 或 `isdigit` 为 `c`不为零，如果 `c` 在范围内，A\-Z、a\-z 或 0 – 9。  如果 `iswalpha` 或 `iswdigit` 为 `c`，是非零`iswalnum` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回0。  
  
 这些带有 `_l` 后缀的函数使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`isalnum`和`_isalnum_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istalnum`|`isalnum`|[\_ismbcalnum](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswalnum`|  
|`_istalnum_l`|`_isalnum_l`|`_ismbcalnum_l`|`_iswalnum_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isalnum`|\<ctype.h\>|  
|`iswalnum`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isalnum_l`|\<ctype.h\>|  
|`_iswalnum_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsLetterOrDigit](https://msdn.microsoft.com/en-us/library/system.char.isletterordigit.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)