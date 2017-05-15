---
title: "isblank、iswblank、_isblank_l、_iswblank_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
dev_langs:
- C++
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6c5f3ebe9921a4b8cc4781cf81239fd63dfa7fd2
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank、iswblank、_isblank_l、_iswblank_l
确定整数是否表示空格字符。  
  
## <a name="syntax"></a>语法  
  
```  
int isblank(  
   int c   
);  
int iswblank(  
   wint_t c   
);  
int _isblank_l(  
   int c,  
   _locale_t locale  
);  
int _iswblank_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `c` 是空格或水平制表符的特定表示方式，或者是用于在文本行中分隔单词的一个特定于区域设置的字符集，则这些例程将返回非零值。 如果 `c` 是空格字符 (0x20) 或水平制表符 (0x09)，则 `isblank` 返回非零值。 `isblank` 函数的测试条件的结果取决于区域设置的 `LC_CTYPE` 类别设置；有关详细信息，请参见 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 `_l` 后缀的函数的版本将当前区域设置用于任何依赖于区域设置的行为；带有 `_l` 后缀的版本与之相同，只不过它们改用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `c` 对应于标准空间的宽字符或水平制表符，则 `iswblank` 返回非零值。  
  
 如果 `isblank` 不是 EOF 或在范围 0 到 0xFF 内（包含 0 和 0xFF），则 `_isblank_l` 和 `c` 的行为没有定义。 当使用调试 CRT 库并且 `c` 不是这些值中的一个时，函数将引发断言。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istblank`|`isblank`|[_ismbcblank](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswblank`|  
|`_istblank_l`|`_isblank_l`|[_ismbcblank_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswblank_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`isblank`|\<ctype.h 1>|  
|`iswblank`|\<ctype.h 1> 或 \<wchar.h 1>|  
|`_isblank_l`|\<ctype.h 1>|  
|`_iswblank_l`|\<ctype.h 1> 或 \<wchar.h 1>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)
