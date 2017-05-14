---
title: "_mbbtype、_mbbtype_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
caps.latest.revision: 18
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
ms.openlocfilehash: e7b9c7aed7205e6cac428a0f627525f9484afc5a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="mbbtype-mbbtypel"></a>_mbbtype、_mbbtype_l
基于上一个字节返回字节类型。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _mbbtype(  
   unsigned char c,  
   int type   
);  
int _mbbtype_l(  
   unsigned char c,  
   int type,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的字符。  
  
 `type`  
 要测试的字节类型。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `_mbbtype` 返回字符串中字节的类型。 此判定与上下文相关，由提供控制测试条件的 `type` 的值指定。 `type` 是字符串中上一个字节的类型。 下表中的清单常量在 Mbctype.h 中定义。  
  
|`type` 的值|`_mbbtype` 测试|返回值|`c`|  
|---------------------|--------------------------|------------------|---------|  
|1 以外的任何值|有效的单字节或前导字节|`_MBC_SINGLE` (0)|单字节 (0x20-0x7E、 0xA1-0xDF)|  
|1 以外的任何值|有效的单字节或前导字节|`_MBC_LEAD` (1)|多字节字符的前导字节 (0x81-0x9F、 0xE0-0xFC)|  
|1 以外的任何值|有效的单字节或前导字节|`_MBC_ILLEGAL`<br /><br /> ( -1)|无效的字符 (任何以外的值 0x20-0x7E、 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|  
|1|有效的结尾字节|`_MBC_TRAIL` (2)|多字节字符的结尾字节 (0x40-0x7E、 0x80-0xFC)|  
|1|有效的结尾字节|`_MBC_ILLEGAL`<br /><br /> ( -1)|无效的字符 (任何以外的值 0x20-0x7E、 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|  
  
## <a name="remarks"></a>备注  
 `_mbbtype` 函数确定多字节字符中字节的类型。 如果 `type` 的值为 1 以外的任何值，则 `_mbbtype` 测试多字节字符的单字节或前导字节是否有效。 如果 `type` 的值为 1，则 `_mbbtype` 测试多字节字符的结尾字节是否有效。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置的影响；有关详细信息，请参阅 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 此函数的 `_mbbtype` 版本对与区域设置相关的行为使用当前区域设置，`_mbbtype_l` 版本基本相同，但它使用传入的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在早期版本中，`_mbbtype` 被命名为 `chkctype`。 对于新代码，请改为使用 `_mbbtype`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_mbbtype`|\<mbstring.h>|\<mbctype.h>*|  
|`_mbbtype_l`|\<mbstring.h>|\<mbctype.h>*|  
  
 \*用作返回值的清单常量的定义。  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)
