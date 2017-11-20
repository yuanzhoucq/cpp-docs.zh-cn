---
title: "_mbbtombc、_mbbtombc_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbbtombc_l
- _mbbtombc
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
dev_langs: C++
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba3dc3100469e207fcfa2e653a9f1a771cfe0d1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mbbtombc-mbbtombcl"></a>_mbbtombc、_mbbtombc_l
将单字节的多字节字符转换为相应的双字节的多字节字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _mbbtombc(  
   unsigned int c   
);  
unsigned int _mbbtombc_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要转换的单字节字符。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `_mbbtombc` 成功转换 `c`，则它将返回一个多字节字符；否则返回 `c`。  
  
## <a name="remarks"></a>备注  
 `_mbbtombc` 函数将一个给定的单字节的多字节字符转换为一个对应的双字节的多字节字符。 字符必须在范围 0x20-0x7E 或 0xA1-0xDF 要转换。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置的影响；有关详细信息，请参阅 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 此函数的各个版本均相同，只不过 `_mbbtombc` 对与区域设置相关的行为使用当前区域设置，而 `_mbbtombc_l` 使用传入的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在早期版本中，`_mbbtombc` 被命名为 `hantozen`。 对于新代码，请使用 `_mbbtombc`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbbtombc`|\<mbstring.h>|  
|`_mbbtombc_l`|\<mbstring.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [_mbctombb、_mbctombb_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)