---
title: "_set_printf_count_output | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_printf_count_output
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
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
caps.latest.revision: 8
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
ms.sourcegitcommit: aadbf7d2c6fece48ab29c1b818995464a790c38b
ms.openlocfilehash: 11f0dbe2a4bb67992dd307aea62f79ca8f6b5f73
ms.contentlocale: zh-cn
ms.lasthandoff: 03/07/2017

---
# <a name="setprintfcountoutput"></a>_set_printf_count_output
启用或禁用 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 系列函数中的 `%n` 格式支持。  
  
## <a name="syntax"></a>语法  
  
```  
int _set_printf_count_output(  
   int enable  
);  
```  
  
#### <a name="parameters"></a>参数  
 `enable`  
 如果启用 `%n` 支持，则为非零值；如果禁用 `%n` 支持，则为 0。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 调用此函数之前的 `%n` 支持状态：如果启用 `%n` 支持，则为非零值；如果禁用它，则为 0。  
  
## <a name="remarks"></a>备注  
 出于安全考虑，默认情况下，在 `%n` 和其所有变量中禁用对 `printf` 格式说明符的支持。 如果在 `printf` 格式规范中遇到 `%n`，则默认行为是调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 调用`_set_printf_count_output`使用非零自变量将导致`printf`-系列函数解释`%n`中所述[格式规范语法︰ printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_set_printf_count_output`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```C  
// crt_set_printf_count_output.c  
#include <stdio.h>  
  
int main()  
{  
   int e;  
   int i;  
   e = _set_printf_count_output( 1 );  
   printf( "%%n support was %sabled.\n",  
        e ? "en" : "dis" );  
   printf( "%%n support is now %sabled.\n",  
        _get_printf_count_output() ? "en" : "dis" );  
   printf( "12345%n6789\n", &i ); // %n format should set i to 5  
   printf( "i = %d\n", i );  
}  
```  
  
```Output  
%n support was disabled.  
%n support is now enabled.  
123456789  
i = 5  
```  
  
## <a name="see-also"></a>另请参阅  
 [_get_printf_count_output](../../c-runtime-library/reference/get-printf-count-output.md)
