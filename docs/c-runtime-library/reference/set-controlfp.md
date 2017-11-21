---
title: "_set_controlfp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_controlfp
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_controlfp
- _set_controlfp
dev_langs: C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f738b643ac225df45b063839f2f758b2766e5d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="setcontrolfp"></a>_set_controlfp
设置浮点控制字。  
  
## <a name="syntax"></a>语法  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>参数  
 `newControl`  
 新的控制字位值。  
  
 `mask`  
 要设置的新控制字位掩码。  
  
## <a name="return-value"></a>返回值  
 无。  
  
## <a name="remarks"></a>备注  
 `_set_controlfp` 与 `_control87` 类似，但前者仅将浮点控制字设置为 `newControl`。 值中的位表示浮点控制状态。 浮点控制状态允许程序在浮点数学包中更改精度、舍入和无穷模式。 您还可使用 `_set_controlfp` 屏蔽或取消屏蔽浮点异常。 有关详细信息，请参阅 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。  
  
 使用编译时，此函数已弃用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)因为公共语言运行时仅支持默认的浮点精度。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|兼容性|  
|-------------|---------------------|-------------------|  
|`_set_controlfp`|\<float.h>|仅限 x86 处理器|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)