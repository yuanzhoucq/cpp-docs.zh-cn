---
title: "_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l | Microsoft Docs"
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
  - "_ismbclower"
  - "_ismbclower_l"
  - "_ismbcupper_l"
  - "_ismbcupper"
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
  - "_ismbcupper"
  - "_ismbclower"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbclower 函数"
  - "_ismbclower_l 函数"
  - "_ismbcupper 函数"
  - "_ismbcupper_l 函数"
  - "ismbclower 函数"
  - "ismbclower_l 函数"
  - "ismbcupper 函数"
  - "ismbcupper_l 函数"
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检查多字节字符是否是小写或大写。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _ismbclower(  
   unsigned int c   
);  
int _ismbclower_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcupper(  
   unsigned int c   
);  
int _ismbcupper_l(  
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
 其中每个函数都针对给定的条件测试给定的多字节字符。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
|例程|测试条件|代码页 932 示例|  
|--------|----------|----------------|  
|`_ismbclower`|小写字母|返回非零，且只有`c` 是 ASCII 字母小写英语的单字节表示：0x61\=\<`c`\<\=0x7A。|  
|`_ismbclower_l`|小写字母|返回非零，且只有`c` 是 ASCII 字母小写英语的单字节表示：0x61\=\<`c`\<\=0x7A。|  
|`_ismbcupper`|大写字母|返回非零，且只有`c` 是 ASCII 字母大写英语的单字节表示：0x41\=\<`c`\<\=0x5A。|  
|`_ismbcupper_l`|大写字母|返回非零，且只有`c` 是 ASCII 字母大写英语的单字节表示：0x41\=\<`c`\<\=0x5A。|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbclower`|\<mbstring.h\>|  
|`_ismbclower_l`|\<mbstring.h\>|  
|`_ismbcupper`|\<mbstring.h\>|  
|`_ismbcupper_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
  
-   [System::Char::IsLower](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)  
  
-   [System::Char::IsUpper](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [\_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)