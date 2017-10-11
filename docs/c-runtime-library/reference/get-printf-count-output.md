---
title: "_get_printf_count_output | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 4373fc075e46110cbcef411b283b8566bf74508c
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="getprintfcountoutput"></a>_get_printf_count_output
指示 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 系列函数是否支持 `%n` 格式。  
  
## <a name="syntax"></a>语法  
  
```  
int _get_printf_count_output();  
```  
  
## <a name="return-value"></a>返回值  
 如果支持 `%n`，则为非零值。如果不支持 `%n`，则为 0。  
  
## <a name="remarks"></a>备注  
 如果不支持 `%n`（默认设置），则在任何 `printf` 函数的格式字符串中遇到 `%n` 时，都将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果`%n`启用支持 (请参阅[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)) 然后`%n`中所述的表现[格式规范语法： printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_get_printf_count_output`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md) 示例。  
  
## <a name="see-also"></a>另请参阅  
[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)  

