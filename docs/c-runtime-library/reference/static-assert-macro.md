---
title: _STATIC_ASSERT 宏 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: 3076e2e2a27c4f13222ce5dba8bf66cc46ce20c1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT 宏

计算表达式在编译时，并生成错误，如果结果为**FALSE**。

## <a name="syntax"></a>语法

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>参数

*布尔表达式*计算结果不为零的表达式 （包括指针） (**TRUE**) 或 0 (**FALSE**)。

## <a name="remarks"></a>备注

此宏类似于[_ASSERT 和 _ASSERTE 宏](assert-asserte-assert-expr-macros.md)，只不过*布尔表达式*在而不是在运行时的编译时计算。 如果*布尔表达式*计算结果为**FALSE** (0)，[编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)生成。

## <a name="example"></a>示例

在此示例中，我们检查是否[sizeof](../../c-language/sizeof-operator-c.md) **int**大于或等于 2 字节以及是否[sizeof](../../c-language/sizeof-operator-c.md) **长**为 1 个字节。 程序将不进行编译，并且将生成[编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)因为**长**大于 1 个字节。

```C
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
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)<br/>
