---
title: "_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbcalpha"
  - "_ismbcalnum"
  - "_ismbcdigit"
  - "_ismbcalnum_l"
  - "_ismbcdigit_l"
  - "_ismbcalpha_l"
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
  - "_ismbcdigit"
  - "ismbcalnum_l"
  - "_ismbcdigit_l"
  - "_ismbcalpha"
  - "ismbcalnum"
  - "ismbcdigit"
  - "ismbcalpha"
  - "_ismbcalnum_l"
  - "_ismbcalnum"
  - "ismbcdigit_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcalnum 函数"
  - "_ismbcalnum_l 函数"
  - "_ismbcalpha 函数"
  - "_ismbcalpha_l 函数"
  - "_ismbcdigit 函数"
  - "_ismbcdigit_l 函数"
  - "ismbcalnum 函数"
  - "ismbcalnum_l 函数"
  - "ismbcalpha 函数"
  - "ismbcalpha_l 函数"
  - "ismbcdigit 函数"
  - "ismbcdigit_l 函数"
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选定多字节字符是字母数字字符，希腊字母或数字字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _ismbcalnum  
(  
   unsigned int c   
);  
int _ismbcalnum_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcalpha  
(  
   unsigned int c   
);  
int _ismbcalpha_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcdigit  
(  
   unsigned int c   
);  
int _ismbcdigit_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。  如果`c`\<\= 255，且存在相应的 `_ismbb`实例 \(例如，`_ismbcalnum`对应于`_ismbbalnum`\)，则结果是相应的`_ismbb`实例的返回值。  
  
## 备注  
 其中每个实例都针对给定的条件测试给定的多字节字符。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
|例程|测试条件|代码页 932 示例|  
|--------|----------|----------------|  
|`_ismbcalnum,_ismbcalnum_l`|字母数字|返回非零，则因此只有当 `c` 是 ASCII 字母英语的单字节表示：为 `_ismbcdigit` 和 `_ismbcalpha` 参见示例。|  
|`_ismbcalpha,_ismbcalpha_l`|Alphabetic|返回非零，则，因此，只有当 `c` 是 ASCII 字母英语的单字节表示：0x41\<\=`c`\<\=0x5A or 0x61\<\=`c`\<\=0x7A; 片假名或字母: 0xA6\<\=`c`\<\=0xDF。|  
|`_ismbcdigit,_ismbcdigit`|Digit|返回非零，且只有 `c` 是 ASCII 数字的单字节表示：0x30\=\<`c`\<\=0x39。|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbcalnum,_ismbcalnum_l`|\<mbstring.h\>|  
|`_ismbcalpha,_ismbcalpha_l`|\<mbstring.h\>|  
|`_ismbcdigit,_ismbcdigit_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
  
-   [System::Char::IsLetter](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)  
  
-   [System::Char::IsDigit](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)  
  
-   对于 `_ismbcalnum`：不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [\_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)