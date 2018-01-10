---
title: "_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbcpunct_l
- _ismbcblank
- _ismbcprint
- _ismbcgraph_l
- _ismbcblank_l
- _ismbcpunct
- _ismbcprint_l
- _ismbcspace_l
- _ismbcspace
- _ismbcgraph
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ismbcspace
- _ismbcgraph
- _ismbcpunct
- ismbcspace_l
- ismbcgraph
- _ismbcgraph_l
- _ismbcprint
- _ismbcspace_l
- ismbcprint
- ismbcgraph_l
- ismbcspace
- ismbcpunct
dev_langs: C++
helpviewer_keywords:
- ismbcspace_l function
- _ismbcprint_l function
- ismbcspace function
- ismbcpunct function
- _ismbcspace_l function
- _ismbcprint function
- ismbcprint function
- _ismbcgraph function
- ismbcgraph_l function
- _ismbcpunct_l function
- ismbcpunct_l function
- ismbcprint_l function
- _ismbcpunct function
- ismbcgraph function
- _ismbcgraph_l function
- _ismbcspace function
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e06106db699ba98d3821cdf09bbe668f745f73fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ismbcgraph-ismbcgraphl-ismbcprint-ismbcprintl-ismbcpunct-ismbcpunctl-ismbcblank-ismbcblankl-ismbcspace-ismbcspacel"></a>_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l
确定字符是图形字符、显示字符、标点字符还是空格字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _ismbcgraph(  
   unsigned int c   
);  
int _ismbcgraph_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcprint(  
   unsigned int c   
);  
int _ismbcprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcpunct(  
   unsigned int c  
);  
int _ismbcpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcblank(  
   unsigned int c   
);  
int _ismbcblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcspace(  
   unsigned int c   
);  
int _ismbcspace_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要确定的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时返回 0。 如果 `c`<= 255 且存在相应的 `_ismbb` 例程（例如，`_ismbcalnum` 对应于 `_ismbbalnum`），则结果是相应的 `_ismbb` 例程的返回值。  
  
 这些函数的版本相同，只不过后缀为 `_l` 的函数将已传入的区域设置而不是当前区域设置用于其与区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="remarks"></a>备注  
 其中每个函数都针对给定的条件测试给定的多字节字符。  
  
|例程所返回的值|测试条件|代码页 932 示例|  
|-------------|--------------------|---------------------------|  
|`_ismbcgraph`|图形|当且仅当 `c` 是除空格 () 之外的任何 ASCII 或片假名可打印字符的单字节表示形式时返回非零值。|  
|`_ismbcprint`|可打印|当且仅当 `c` 是包括空格 () 的任何 ASCII 或片假名可打印字符的单字节表示形式时返回非零值。|  
|`_ismbcpunct`|标点|当且仅当 `c` 是任何 ASCII 或片假名标点字符的单字节表示形式时返回非零值。|  
|`_ismbcblank`|空格或水平制表符|当且仅当 `c` 是空格字符或水平制表符 `c`=0x20 或 `c`=0x09 时返回非零值。|  
|`_ismbcspace`|空格|当且仅当 `c` 是空白字符 `c`=0x20 或 0x09<=`c`<=0x0D 时返回非零值。|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_ismbcgraph`|\<mbstring.h>|  
|`_ismbcgraph_l`|\<mbstring.h>|  
|`_ismbcprint`|\<mbstring.h>|  
|`_ismbcprint_l`|\<mbstring.h>|  
|`_ismbcpunct`|\<mbstring.h>|  
|`_ismbcpunct_l`|\<mbstring.h>|  
|`_ismbcblank`|\<mbstring.h>|  
|`_ismbcblank_l`|\<mbstring.h>|  
|`_ismbcspace`|\<mbstring.h>|  
|`_ismbcspace_l`|\<mbstring.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb 例程](../../c-runtime-library/ismbb-routines.md)