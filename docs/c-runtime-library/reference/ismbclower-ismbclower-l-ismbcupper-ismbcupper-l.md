---
title: "_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- _ismbcupper
- _ismbclower
dev_langs:
- C++
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865c2280ab395b5c8172ee978da16a2bcc26f7b9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l
检查多字节字符是大写还是小写。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int _ismbclower(  
   unsigned int c   
);  
int _ismbclower_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcupper(  
   unsigned int c   
);  
int _ismbcupper_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果 `c`<= 255 且存在相应的 `_ismbb` 例程（例如，`_ismbcalnum` 对应于 `_ismbbalnum`），则结果是相应的 `_ismbb` 例程的返回值。  
  
## <a name="remarks"></a>备注  
 其中每个函数都针对给定的条件测试给定的多字节字符。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
|例程|测试条件|代码页 932 示例|  
|-------------|--------------------|---------------------------|  
|`_ismbclower`|小写字母|当且仅当 `c` 是 ASCII 小写英文字母 0x61<=`c`<=0x7A 的单字节表示形式时返回非零值。|  
|`_ismbclower_l`|小写字母|当且仅当 `c` 是 ASCII 小写英文字母 0x61<=`c`<=0x7A 的单字节表示形式时返回非零值。|  
|`_ismbcupper`|大写字母|当且仅当 `c` 是 ASCII 大写英文字母 0x41<=`c`<=0x5A 的单字节表示形式时返回非零值。|  
|`_ismbcupper_l`|大写字母|当且仅当 `c` 是 ASCII 大写英文字母 0x41<=`c`<=0x5A 的单字节表示形式时返回非零值。|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_ismbclower`|\<mbstring.h>|  
|`_ismbclower_l`|\<mbstring.h>|  
|`_ismbcupper`|\<mbstring.h>|  
|`_ismbcupper_l`|\<mbstring.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb 例程](../../c-runtime-library/ismbb-routines.md)