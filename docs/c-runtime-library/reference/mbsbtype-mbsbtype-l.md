---
title: "_mbsbtype、_mbsbtype_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 81223356f5dac86fcc161e1c7fd1bc5eb80dcfbf
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype、_mbsbtype_l
返回字符串中字节的类型。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>参数  
 `mbstr`  
 多字节字符序列的地址。  
  
 `count`  
 字符串头中的字节偏移量。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `_mbsbtype`和`_mbsbtype_l`返回一个整数值，该值指示指定的字节上测试的结果。 下表中的清单常量在 Mbctype.h 中定义。  
  
|返回值|字节类型|  
|------------------|---------------|  
|`_MBC_SINGLE` (0)|单字节字符。 例如，在代码页 932，`_mbsbtype`如果指定的字节在范围内 0x20-0x7E 或 0xA1-0xDF 返回 0。|  
|`_MBC_LEAD` (1)|多字节字符的前导字节。 例如，在代码页 932，`_mbsbtype`返回 1，如果指定的字节在范围内 0x81-0x9F 或 0xE0-0xFC。|  
|`_MBC_TRAIL` (2)|多字节字符的尾随字节。 例如，在代码页 932，`_mbsbtype`返回 2，如果指定的字节在范围内 0x40-0x7E 或 0x80-0xFC。|  
|`_MBC_ILLEGAL` (-1)|在 `mbstr` 中的偏移 `count` 上的字节前发现 `NULL` 字符串、无效字符或 `NULL` 字节。|  
  
## <a name="remarks"></a>备注  
 `_mbsbtype` 函数确定多字节字符字符串中字节的类型。 此函数仅检查 `mbstr` 中的偏移 `count` 上的字节，而忽略指定字节前的无效字符。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 此不带 `_l` 后缀的版本将对与区域设置相关的行为使用当前设置；而带有 `_l` 后缀的版本也执行相同的操作，只不过它改用传入的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果输入字符串为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `_MBC_ILLEGAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_mbsbtype`|\<mbstring.h>|\<mbctype.h>*|  
|`_mbsbtype_l`|\<mbstring.h>|\<mbctype.h>*|  
  
 \*用作返回值的清单常量。  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)
