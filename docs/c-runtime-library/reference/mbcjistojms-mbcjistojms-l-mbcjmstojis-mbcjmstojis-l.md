---
title: "_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
dev_langs:
- C++
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
caps.latest.revision: 20
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 514e00148ec34a14a7b229d5b7e226d8be66636d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l
在日本行业标准 (JIS) 和日本 Microsoft (JMS) 字符之间转换。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _mbcjistojms(  
   unsigned int c   
);  
unsigned int _mbcjistojms_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbcjmstojis(  
   unsigned int c   
);  
unsigned int _mbcjmstojis_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要转换的字符。  
  
 `local`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 在日文区域设置中，这些函数将返回经转换的字符或者在转换不可用时返回 0。 在非日文区域设置中，这些函数将返回传入的字符。  
  
## <a name="remarks"></a>备注  
 `_mbcjistojms` 函数将日本行业标准 (JIS) 字符转换为 Microsoft 日文汉字（转义 JIS）字符。 仅当主管和结尾字节在范围内 0x21-0x7E，转换的字符。 如果前导字节或结尾字节超出此范围，则将 `errno` 设置为 `EILSEQ`。 有关此代码及其他错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `_mbcjmstojis`函数将 Shift JIS 字符转换为 JIS 字符。 仅当处于范围内 0x81-0x9F 或 0xE0-0xFC 前导字节和结尾字节处于范围内 0x40-0x7E 或 0x80-0xFC，转换的字符。 请注意该范围内的一些码位未分配字符，因此无法进行转换。  
  
 值 `c` 应为 16 位值，其中，较高的 8 位表示要转换的字符的前导字节，较低的 8 位表示结尾字节。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 在早期版本，`_mbcjistojms`和`_mbcjmstojis`调用`jistojms`和`jmstojis`分别。 `_mbcjistojms``_mbcjistojms_l`，`_mbcjmstojis`和`_mbcjmstojis_l`应改为使用。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbcjistojms`|\<mbstring.h>|  
|`_mbcjistojms_l`|\<mbstring.h>|  
|`_mbcjmstojis`|\<mbstring.h>|  
|`_mbcjmstojis_l`|\<mbstring.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [_ismbb 例程](../../c-runtime-library/ismbb-routines.md)
