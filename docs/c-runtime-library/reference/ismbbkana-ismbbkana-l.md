---
title: "_ismbbkana、_ismbbkana_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbkana_l
- _ismbbkana
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
- _ismbbkana_l
- ismbbkana_l
- ismbbkana
- _ismbbkana
dev_langs:
- C++
helpviewer_keywords:
- _ismbbkana_l function
- _ismbbkana function
- ismbbkana function
- ismbbkana_l function
ms.assetid: 64d4eb4a-205a-40ef-be35-ff9d77fabbaf
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3473da1104d9bc4578fbeb9d29bbbca3ddc9e0dc
ms.lasthandoff: 02/24/2017

---
# <a name="ismbbkana-ismbbkanal"></a>_ismbbkana、_ismbbkana_l
测试片假名符号，并且专门用于代码页 932。  
  
## <a name="syntax"></a>语法  
  
```  
int _ismbbkana(  
   unsigned int c   
);  
int _ismbbkana_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果整数 `_ismbbkana` 为片假名符号，则 `c` 返回一个非零值，否则返回 0。 `_ismbbkana` 对区域设置相关的字符信息使用当前区域设置。 `_ismbbkana_l` 也是一样，只不过它使用传入的区域设置对象。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_ismbbkana`|\<mbctype.h>|  
|`_ismbbkana_l`|\<mbctype.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [_ismbb 例程](../../c-runtime-library/ismbb-routines.md)
