---
title: "_isctype、iswctype、_isctype_l、_iswctype_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isctype_l"
  - "iswctype"
  - "_iswctype_l"
  - "_isctype"
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
  - "iswctype"
  - "_isctype"
  - "_isctype_l"
  - "_iswctype"
  - "isctype"
  - "iswctype_l"
  - "isctype_l"
  - "_iswctype_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isctype 函数"
  - "_isctype_l 函数"
  - "_iswctype 函数"
  - "_iswctype_l 函数"
  - "isctype 函数"
  - "isctype_l 函数"
  - "iswctype 函数"
  - "iswctype_l 函数"
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _isctype、iswctype、_isctype_l、_iswctype_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

测试 `desc` 参数指定的属性 `c`。  `desc`的每个有效值都具有等效的宽字符类的实例。  
  
## 语法  
  
```  
int _isctype(  
   int c,  
   _ctype_t desc  
);  
int _isctype_l(  
   int c,  
   _ctype_t desc,  
   _locale_t locale  
);  
int iswctype(  
   wint_t c,  
   wctype_t desc   
);  
int _iswctype_l(  
   wint_t c,  
   wctype_t desc,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `desc`  
 要测试的属性。  使用 ctype 或 [wctype](../../c-runtime-library/reference/wctype.md)通常需要检索。  
  
 `locale`  
 使用的区域设置用于任何区域设置相关测试。  
  
## 返回值  
 如果 `c`在当前区域设置中具有 `desc` 指定的属性，`_isctype` 和 `iswctype` 返回一个非零值，若没有则返回0。  这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c`不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`_isctype`和`_isctype_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`n/a`|`_isctype`|`n/a`|`_iswctype`|  
|`n/a`|`_isctype_l`|`n/a`|`_iswctype_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_isctype`|\<ctype.h\>|  
|`iswctype`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isctype_l`|\<ctype.h\>|  
|`_iswctype_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)