---
title: "isleadbyte、_isleadbyte_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isleadbyte_l
- isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs:
- C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 73078df22931a5533ffe912174d11b384c8de417
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte、_isleadbyte_l
确定一个字符是否为多字节字符的前导字节。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅                  [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int isleadbyte(  
   int c   
);  
int _isleadbyte_l(  
   int c   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数。  
  
## <a name="return-value"></a>返回值  
 如果参数满足测试条件，则 `isleadbyte` 返回一个非零值，否则返回 0。 在“C”区域设置和单字节字符集 (SBCS) 区域设置中， `isleadbyte` 始终返回 0。  
  
## <a name="remarks"></a>备注  
 如果 `isleadbyte` 宏的参数是多字节字符的第一个字节，则它返回非零值。 `isleadbyte`生成有意义的结果的任何整数自变量在-1 (`EOF`) 到`UCHAR_MAX`(0xFF) （含)。  
  
 `isleadbyte` 的预期参数类型是 `int`；如果传递了带符号的字符，编译器可能会通过符号扩展将其转换为整数，从而生成无法预测的结果。  
  
 此函数带 `_l` 后缀的版本是相同的，但该本本会针对其依赖于区域设置的行为使用传入的区域设置而非当前的区域设置。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istleadbyte`|始终返回 false|**_** `isleadbyte`|始终返回 false|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`isleadbyte`|\<ctype.h>|  
|`_isleadbyte_l`|\<ctype.h 1>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [_ismbb 例程](../../c-runtime-library/ismbb-routines.md)
