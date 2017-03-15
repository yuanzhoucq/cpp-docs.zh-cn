---
title: "isalpha、iswalpha、_isalpha_l、_iswalpha_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswalpha"
  - "_iswalpha_l"
  - "isalpha"
  - "_isalpha_l"
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
  - "_istalpha"
  - "_ismbcalpha_l"
  - "isalpha"
  - "_isalpha_l"
  - "iswalpha"
  - "_istalpha_l"
  - "_iswalpha_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isalpha_l 函数"
  - "_ismbcalpha 函数"
  - "_ismbcalpha_l 函数"
  - "_istalpha 函数"
  - "_istalpha_l 函数"
  - "_iswalpha_l 函数"
  - "isalpha 函数"
  - "istalpha 函数"
  - "iswalpha 函数"
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# isalpha、iswalpha、_isalpha_l、_iswalpha_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示字母字符。  
  
## 语法  
  
```  
int isalpha(   
   int c   
);  
int iswalpha(   
   wint_t c   
);  
int _isalpha_l(   
   int c,  
   _locale_t locale   
);  
int _iswalpha_l(   
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 使用区域设置而不是当前区域设置。  
  
## 返回值  
 如果 `c` 是字母字符的特定表示，则每个实例返回非零。  如果 `c` 在范围A\-Z或a\-z 中，`isalpha` 返回一个非零值。  仅当`iswupper` 或 `iswlower` 是非零的宽字符时，`iswalpha` 返回一个非零值 ；即为现实定义的任何宽字符`iswcntrl`、`iswdigit`、`iswpunct`或 `iswspace` 都不是非零。  如果 `c` 不满足测试条件，则每个实例都返回 0。  
  
 这些带有 `_l` 后缀的函数使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c`不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`isalpha`和`_isalpha_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istalpha`|`isalpha`|`_ismbcalpha`|`iswalpha`|  
|`_istalpha_l`|`_isalpha_l`|`_ismbcalpha_l`|`_iswalpha_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isalpha`|\<ctype.h\>|  
|`iswalpha`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isalpha_l`|\<ctype.h\>|  
|`_iswalpha_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsLetter](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)