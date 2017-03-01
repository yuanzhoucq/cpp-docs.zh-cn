---
title: "_mbctombb、_mbctombb_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
dev_langs:
- C++
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d1831c28a8aab99478fb362d46db352674a360df
ms.lasthandoff: 02/24/2017

---
# <a name="mbctombb-mbctombbl"></a>_mbctombb、_mbctombb_l
将双字节的多字节字符转换为相应的单字节的多字节字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _mbctombb(  
   unsigned int c   
);  
unsigned int _mbctombb_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要转换的多字节字符。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果成功，`_mbctombb` 和 `_mbctombb_l` 将返回与 `c` 对应的单字节字符；否则会返回 `c`。  
  
## <a name="remarks"></a>备注  
 `_mbctombb` 和 `_mbctombb_l` 函数将给定的多字节字符转换为对应的单字节的多字节字符。 要转换的字符必须对应 0x20 – 0x7E 或 0xA1 – 0xDF 范围内的单字节字符。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 此不带 `_l` 后缀的版本将对与区域设置相关的行为使用当前设置；而带有 `_l` 后缀的版本也执行相同的操作，只不过它改用传入的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在早期版本中，`_mbctombb` 称为 `zentohan`。 请改用 _`mbctombb`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbctombb`|\<mbstring.h>|  
|`_mbctombb_l`|\<mbstring.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [_mbbtombc、_mbbtombc_l](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)
