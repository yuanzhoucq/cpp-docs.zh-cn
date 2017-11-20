---
title: "isalpha、iswalpha、_isalpha_l、_iswalpha_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
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
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
dev_langs: C++
helpviewer_keywords:
- _iswalpha_l function
- _isalpha_l function
- _ismbcalpha_l function
- _istalpha_l function
- _ismbcalpha function
- isalpha function
- iswalpha function
- istalpha function
- _istalpha function
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e93b18a5fc29f74ba9ea9fb990d4a7a0715872b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="isalpha-iswalpha-isalphal-iswalphal"></a>isalpha、iswalpha、_isalpha_l、_iswalpha_l
确定整数是否表示字母字符。  
  
## <a name="syntax"></a>语法  
  
```  
int isalpha(   
   int c   
);  
int iswalpha(   
   wint_t c   
);  
int _isalpha_l(   
   int c,  
   _locale_t locale   
);  
int _iswalpha_l(   
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的非当前区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `c` 是字母字符的特定表示方式，则这些例程都返回非零。 `isalpha`返回一个非零值，如果`c`在 A-Z 或 a-z 范围内。 `iswalpha` 仅为 `iswupper` 或 `iswlower` 是非零值的宽字符返回一个非零值；即对于属于实现定义集之一，且 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 均不是非零值的任何宽字符返回非零值。 如果 `c` 不满足测试条件，则这些例程都返回 0。  
  
 带 `_l` 后缀的函数的版本使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `isalpha` 不是 EOF 或在范围 0 到 0xFF 内（包含 0 和 0xFF），则 `_isalpha_l` 和 `c` 的行为没有定义。 当使用调试 CRT 库并且 `c` 不是这些值中的一个时，函数将引发断言。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istalpha`|`isalpha`|`_ismbcalpha`|`iswalpha`|  
|`_istalpha_l`|`_isalpha_l`|`_ismbcalpha_l`|`_iswalpha_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`isalpha`|\<ctype.h 1>|  
|`iswalpha`|\<ctype.h 1> 或 \<wchar.h 1>|  
|`_isalpha_l`|\<ctype.h 1>|  
|`_iswalpha_l`|\<ctype.h 1> 或 \<wchar.h 1>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)