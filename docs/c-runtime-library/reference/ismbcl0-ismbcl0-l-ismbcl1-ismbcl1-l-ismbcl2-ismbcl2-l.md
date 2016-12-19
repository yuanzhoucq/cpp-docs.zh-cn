---
title: "_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l | Microsoft Docs"
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
  - "_ismbcl2"
  - "_ismbcl1"
  - "_ismbcl0"
  - "_ismbcl2_l"
  - "_ismbcl1_l"
  - "_ismbcl0_l"
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
  - "ismbcl0"
  - "_ismbcl1_l"
  - "_ismbcl0"
  - "ismbcl1"
  - "ismbcl0_l"
  - "_ismbcl2_l"
  - "ismbcl2"
  - "ismbcl1_l"
  - "_ismbcl1"
  - "_ismbcl0_l"
  - "_ismbcl2"
  - "ismbcl2_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcl0 函数"
  - "_ismbcl0_l 函数"
  - "_ismbcl1 函数"
  - "_ismbcl1_l 函数"
  - "_ismbcl2 函数"
  - "_ismbcl2_l 函数"
  - "ismbcl0 函数"
  - "ismbcl0_l 函数"
  - "ismbcl1 函数"
  - "ismbcl1_l 函数"
  - "ismbcl2 函数"
  - "ismbcl2_l 函数"
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Code Page 932 Specific functions**，使用当前区域设置或指定的 LC\_CTYPE 转换状态类别。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _ismbcl0(  
   unsigned int c   
);  
int _ismbcl0_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcl1(  
   unsigned int c   
);  
int _ismbcl1_l(  
   unsigned int c ,  
   _locale_t locale  
);  
int _ismbcl2(  
   unsigned int c   
);  
int _ismbcl2_l(  
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
 其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。  如果`c` \<\= 255，且存在相应的 `_ismbb` 实例 \(例如，`_ismbcalnum` 对应于 `_ismbbalnum`\)，则结果是相应的 `_ismbb` 实例的返回值。  
  
## 备注  
 其中每个函数都针对给定的条件测试给定的多字节字符。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
|例程|测试条件 \(代码页 932 只\)|  
|--------|------------------------|  
|`_ismbcl0`|JIS 非日本汉字：0x8140\=\<`c`\<\=0x889E。|  
|`_ismbcl0_l`|JIS 非日本汉字：0x8140\=\<`c`\<\=0x889E。|  
|`_ismbcl1`|JIS 级别 1:0x889F\=\<`c`\<\=0x9872。|  
|`_ismbcl1_l`|JIS 级别 1:0x889F\=\<`c`\<\=0x9872。|  
|`_ismbcl2`|JIS 级别 2:0x989F\=\<`c`\<\=0xEAA4。|  
|`_ismbcl2_l`|JIS 级别 2:0x989F\=\<`c`\<\=0xEAA4。|  
  
 函数检查满足上述测试条件的指定值 `c`，但是，不检查`c` 是有效的多字节字符。  如果低字节在范围 0x00 – 0x3F、0x7F 或 0xFD – 0xFF，这些函数返回一个非零值，指示满足测试条件的字符。  使用 [\_ismbbtrail](../../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 测试多字节字符是否已定义。  
  
 **尾代码页 932 特定**  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbcl0`|\<mbstring.h\>|  
|`_ismbcl0_l`|\<mbstring.h\>|  
|`_ismbcl1`|\<mbstring.h\>|  
|`_ismbcl1_l`|\<mbstring.h\>|  
|`_ismbcl2`|\<mbstring.h\>|  
|`_ismbcl2_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [\_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)