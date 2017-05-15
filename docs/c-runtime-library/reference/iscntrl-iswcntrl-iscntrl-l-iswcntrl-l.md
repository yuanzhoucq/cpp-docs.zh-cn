---
title: "iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
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
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
dev_langs:
- C++
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
caps.latest.revision: 19
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: def32829b1be9e5b4076905cd80a475cf589a646
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="iscntrl-iswcntrl-iscntrll-iswcntrll"></a>iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l
确定整数是否表示控制字符。  
  
## <a name="syntax"></a>语法  
  
```  
int iscntrl(   
   int c   
);  
int iswcntrl(   
   wint_t c   
);  
int _iscntrl_l(   
   int c,  
   _locale_t locale  
);  
int _iswcntrl_l(   
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `c` 是控制字符的特定表示形式，则每个例程将返回非零值。 `iscntrl`返回一个非零值，如果`c`是控制字符 (0x00-0x1F 或 0x7F)。 如果 `c` 是一个控制宽字符，则 `iswcntrl` 返回非零值。 如果 `c` 不满足测试条件，则这些例程都返回 0。  
  
 带 `_l` 后缀的函数的版本使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `iscntrl` 不是 EOF 或在范围 0 到 0xFF 内（包含 0 和 0xFF），则 `_iscntrl_l` 和 `c` 的行为没有定义。 当使用调试 CRT 库并且 `c` 不是这些值中的一个时，函数将引发断言。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istcntrl`|`iscntrl`|`iscntrl`|`iswcntrl`|  
|`_istcntrl_l`|`_iscntrl_l`|`_iscntrl_l`|`_iswcntrl_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`iscntrl`|\<ctype.h 1>|  
|`iswcntrl`|\<ctype.h 1> 或 \<wchar.h 1>|  
|`_iscntrl_l`|\<ctype.h 1>|  
|`_iswcntrl_l`|\<ctype.h 1> 或 \<wchar.h 1>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)
