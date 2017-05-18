---
title: "_STATIC_ASSERT 宏 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- _STATIC_ASSERT
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 265796cdebbed1c0a067c44bbe6b71077be44a2b
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="staticassert-macro"></a>_STATIC_ASSERT 宏
在编译时计算表达式，如果结果为 `FALSE`，则将生成错误。  
  
## <a name="syntax"></a>语法  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### <a name="parameters"></a>参数  
 `booleanExpression`  
 计算结果为零 (`TRUE`) 或不为零 (`FALSE`) 的表达式（包括指针）。  
  
## <a name="remarks"></a>备注  
 此宏类似于 [_ASSERT 和 _ASSERTE macros](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)，但会在编译时而不是运行时计算 `booleanExpression`。 如果将 `booleanExpression` 计算为 `FALSE` (0)，则会生成[编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)。  
  
## <a name="example"></a>示例  
 在此示例中，我们将检查 `sizeof` 的 `int` 是否大于或等于 2 字节以及 `sizeof` 的 `long` 是否为 1 字节。 该程序将不会进行编译，并会生成[编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)，因为 `long` 大于 1 字节。  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## <a name="requirements"></a>要求  
  
|宏|必需的标头|  
|-----------|---------------------|  
|`_STATIC_ASSERT`|\<crtdbg.h>|  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)
