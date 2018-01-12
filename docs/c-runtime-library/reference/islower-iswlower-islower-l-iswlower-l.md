---
title: "islower、iswlower、_islower_l、_iswlower_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iswlower
- _islower_l
- islower
- _iswlower_l
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
- _istlower
- islower
- _ismbclower_l
- _liswlower_l
- _istlower_l
- _iswlower_l
- _islower _l
- _islower_l
- iswlower
dev_langs: C++
helpviewer_keywords:
- _islower _l function
- _ismbclower_l function
- islower function
- _iswlower_l function
- _liswlower_l function
- _istlower_l function
- istlower function
- _istlower function
- iswlower function
- _islower_l function
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6aa6f584db325694b081f367f8b78146776764ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="islower-iswlower-islowerl-iswlowerl"></a>islower、iswlower、_islower_l、_iswlower_l
确定整数是否表示小写字符。  
  
## <a name="syntax"></a>语法  
  
```  
int islower(  
   int c   
);  
int iswlower(  
   wint_t c   
);  
int islower_l(  
   int c,  
   _locale_t locale  
);  
int _iswlower_l(  
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
 如果 `c` 是小写字符的特定表示形式，则每个例程将返回非零值。 `islower`返回一个非零值，如果`c`是小写字符 (a-z)。 如果 `c` 是对应于一个小写字母的宽字符，或者如果 `c` 是实现定义的宽字符集之一，且对于该宽字符，`iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 均不是非零值，则 `iswlower` 返回一个非零值。 如果 `c` 不满足测试条件，则这些例程都返回 0。  
  
 这些后缀为 `_l` 的函数版本将传入的区域设置而不是当前区域设置用于其区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `islower` 不是 EOF 或在范围 0 到 0xFF 内（包含 0 和 0xFF），则 `_islower_l` 和 `c` 的行为没有定义。 当使用调试 CRT 库并且 `c` 不是这些值中的一个时，函数将引发断言。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istlower`|`islower`|[_ismbclower](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswlower`|  
|`_istlower_l`|`_islower _l`|[_ismbclower_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_liswlower_l`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`islower`|\<ctype.h 1>|  
|`iswlower`|\<ctype.h 1> 或 \<wchar.h 1>|  
|`_islower_l`|\<ctype.h>|  
|`_swlower_l`|\<ctype.h 1> 或 \<wchar.h 1>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)