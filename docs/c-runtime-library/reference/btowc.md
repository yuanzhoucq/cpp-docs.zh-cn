---
title: "btowc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- btowc
dev_langs:
- C++
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 71af03a57886b150d6543e3aa11bfb0e05896890
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="btowc"></a>btowc
确定整数是否表示初始位移状态中的有效单字节字符。  
  
## <a name="syntax"></a>语法  
  
```  
wint_t btowc(  
   int c  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数。  
  
## <a name="return-value"></a>返回值  
 如果整数表示初始位移状态中的有效单字节字符，则将返回字符的宽字符表示形式。 如果整数是 EOF 或不是初始位移状态中的有效单字节字符，则返回 WEOF。 此函数的输出将受当前 `LC_TYPE` 区域设置的影响。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`btowc`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另请参阅  
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)
