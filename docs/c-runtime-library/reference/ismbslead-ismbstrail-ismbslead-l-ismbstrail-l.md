---
title: "_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
dev_langs:
- C++
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
caps.latest.revision: 22
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
ms.openlocfilehash: 5c74c39a90896f9c04bfc945b420238795b11b74
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="ismbslead-ismbstrail-ismbsleadl-ismbstraill"></a>_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l
对多字节字符串前导字节和结尾字节执行上下文相关测试，并确定给定子字符串指针指向前导字节还是结尾字节。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _ismbslead(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbstrail(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbslead_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
int _ismbstrail_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 指向字符串开头或之前已知的前导字节的指针。  
  
 `current`  
 指向要测试的字符串中位置的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `_ismbslead`如果字符是前导字节，则返回-1 和`_ismbstrail`如果字符是一个尾字节返回-1。 如果输入字符串有效，但不是前导字节也不是结尾字节，则这些函数将返回零。 如果任一参数为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_ismbslead` 和 `_ismbstrail` 慢于 `_ismbblead` 和 `_ismbbtrail` 版本，因为前二者会将字符串文本考虑进去。  
  
 前缀为 `_l` 的函数的版本相同，但其依赖区域设置的行为除外，它们可使用已传入的区域设置代替当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_ismbslead`|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|  
|`_ismbstrail`|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|  
|`_ismbslead_l`|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|  
|`_ismbstrail_l`|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|  
  
 \* 适用于测试条件的清单常量。  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb 例程](../../c-runtime-library/ismbb-routines.md)
