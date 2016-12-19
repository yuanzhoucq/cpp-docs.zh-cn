---
title: "_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l | Microsoft Docs"
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
  - "_ismbclegal_l"
  - "_ismbclegal"
  - "_ismbcsymbol"
  - "_ismbcsymbol_l"
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
  - "ismbcsymbol_l"
  - "_ismbcsymbol_l"
  - "_ismbcsymbol"
  - "_ismbclegal_l"
  - "_ismbclegal"
  - "ismbclegal_l"
  - "ismbcsymbol"
  - "ismbclegal"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbclegal 函数"
  - "_ismbclegal_l 函数"
  - "_ismbcsymbol 函数"
  - "_ismbcsymbol_l 函数"
  - "_istlegal 函数"
  - "_istlegal_l 函数"
  - "ismbclegal 函数"
  - "ismbclegal_l 函数"
  - "ismbcsymbol 函数"
  - "ismbcsymbol_l 函数"
  - "istlegal 函数"
  - "istlegal_l 函数"
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选定多字节字符是否为某还包括法规或符号字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _ismbclegal(  
   unsigned int c   
);  
int _ismbclegal_l(  
   unsigned int c,   
   _locale_t locale  
);  
int _ismbcsymbol(  
   unsigned int c   
);  
int _ismbcsymbol_l(  
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
|`_ismbclegal`|有效的多字节|返回非零，当且只有当第一个字节 `c` 在范围 0x81– 0x9F 或 0xE0 –0xFC，那么，当第二个字节在范围内 0x40 \- 0x7E 或 0x80 \- 0xFC。|  
|`_ismbcsymbol`|多字节字符|返回非零，当且仅当 0x8141\=\<`c`\<\=0x81AC。|  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istlegal`|始终返回 false|`_ismbclegal`|始终返回 false。|  
|`_istlegal_l`|始终返回 false|`_ismbclegal_l`|始终返回 false。|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbclegal,_ismbclegal_l`|\<mbstring.h\>|  
|`_ismbcsymbol,_ismbcsymbol_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [\_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)