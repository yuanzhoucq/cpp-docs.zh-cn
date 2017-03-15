---
title: "_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbctolower_l"
  - "_mbctoupper_l"
  - "_mbctoupper"
  - "_mbctolower"
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
  - "mbctoupper_l"
  - "mbctolower_l"
  - "_mbctolower"
  - "_mbctolower_l"
  - "_mbctoupper"
  - "mbctoupper"
  - "mbctolower"
  - "_mbctoupper_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbctolower 函数"
  - "_mbctolower_l 函数"
  - "_mbctoupper 函数"
  - "_mbctoupper_l 函数"
  - "_totlower 函数"
  - "_totupper 函数"
  - "mbctolower 函数"
  - "mbctolower_l 函数"
  - "mbctoupper 函数"
  - "mbctoupper_l 函数"
  - "totlower 函数"
  - "totupper 函数"
ms.assetid: 787fab71-3224-4ed7-bc93-4dcd8023fc54
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

测试并转换多字节字符用例。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
unsigned int _mbctolower(  
   unsigned int c   
);  
unsigned int _mbctolower_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctoupper(  
   unsigned int c   
);  
unsigned int _mbctoupper_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 转换多字节字符。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些函数中的每一个尽可能返回转换的字符`c`。  否则，它将返回未修改的字符 `c`。  
  
## 备注  
 函数可测试一个字符 `c`，如果可能应用以下转换之一。  
  
|例程|转换|  
|--------|--------|  
|`_mbctolower,_mbctolower_l`|将大写字符转为小写字符。|  
|`_mbctoupper,_mbctoupper_l`|将小写字符转为大写字符。|  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数版本使用为该区域设置相关行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用区域设置参数通过。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在早期版本中，`_mbctolower` 调用`jtolower`，并且，`_mbctoupper` 调用 `jtoupper`。  对于新代码，请使用新名称。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_t`|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbctolower,_mbctolower_l`|\<mbstring.h\>|  
|`_mbctoupper,_mbctoupper_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_mbbtombc、\_mbbtombc\_l](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [\_mbctombb、\_mbctombb\_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)