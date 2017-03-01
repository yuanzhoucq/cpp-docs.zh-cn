---
title: "_getmaxstdio | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getmaxstdio
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
- _getmaxstdio
- getmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 458a56eef99582d7b70d04c85169505ddb0ae47c
ms.lasthandoff: 02/24/2017

---
# <a name="getmaxstdio"></a>_getmaxstdio
返回在 I/O 流级别允许同时打开的文件数。  
  
## <a name="syntax"></a>语法  
  
```  
int _getmaxstdio( void );  
```  
  
## <a name="return-value"></a>返回值  
 返回一个表示在 `stdio` 级别当前允许同时打开的文件数。  
  
## <a name="remarks"></a>备注  
 使用 [_setmaxstdio](../../c-runtime-library/reference/setmaxstdio.md) 配置在 `stdio` 级别允许同时打开的文件数。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_getmaxstdio`|\<stdio.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_setmaxstdio.c  
// The program retrieves the maximum number  
// of open files and prints the results  
// to the console.  
  
#include <stdio.h>  
  
int main()  
{  
   printf( "%d\n", _getmaxstdio());  
  
   _setmaxstdio(2048);  
  
   printf( "%d\n", _getmaxstdio());  
}  
```  
  
```Output  
512  
2048  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)
