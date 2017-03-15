---
title: "isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_iswxdigit_l"
  - "iswxdigit"
  - "isxdigit"
  - "_isxdigit_l"
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
  - "iswxdigit"
  - "isxdigit"
  - "_istxdigit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_istxdigit 函数"
  - "_iswxdigit_l 函数"
  - "_isxdigit_l 函数"
  - "十六进制字符"
  - "istxdigit 函数"
  - "iswxdigit 函数"
  - "iswxdigit_l 函数"
  - "isxdigit 函数"
  - "isxdigit_l 函数"
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示一个十六进制数字的字符。  
  
## 语法  
  
```  
int isxdigit(  
   int c   
);  
int iswxdigit(  
   wint_t c   
);  
int _isxdigit_l(  
   int c,  
   _locale_t locale  
);  
int _iswxdigit_l(  
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
 如果 `c` 是十六进制数字字符的特定表示，则每个实例返回非零。  如果 `c` 是十六进制数字 \(A\-F，a\-f 或 0 – 9\)，`isxdigit` 返回一个非零值。  如果 `c` 是对应于十六进制数字字符的宽字符,`iswxdigit` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回0。  
  
 对于“C”区域设置，`iswxdigit` 函数不支持 Unicode 全角十六进制字符。  
  
 这些带有 `_l` 后缀的函数的版本使用传递的区域设置，而不是与区域设置行为相关的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `isxdigit` 和 `_isxdigit_l` 的行为是未定义的，如果 `c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF）.  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istxdigit`|`isxdigit`|`isxdigit`|`iswxdigit`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isxdigit`|\<ctype.h\>|  
|`iswxdigit`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isxdigit_l`|\<ctype.h\>|  
|`_iswxdigit_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsNumber](https://msdn.microsoft.com/en-us/library/system.char.isnumber.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)