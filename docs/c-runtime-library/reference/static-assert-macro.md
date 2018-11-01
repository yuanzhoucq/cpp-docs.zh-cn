---
title: _STATIC_ASSERT 宏
ms.date: 11/04/2016
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
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: 5d3aa1d9665b48a0690d8eb62353fc98c5a550f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539537"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT 宏

计算在编译时表达式，并生成错误时的结果是**FALSE**。

## <a name="syntax"></a>语法

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
表达式 （包括指针） 的计算结果不为零 (**，则返回 TRUE**) 或 0 (**FALSE**)。

## <a name="remarks"></a>备注

此宏类似于[_ASSERT 和 _ASSERTE 宏](assert-asserte-assert-expr-macros.md)，只不过*布尔表达式*在而不是在运行时的编译时计算。 如果*布尔表达式*的计算结果为**FALSE** (0)，[编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)生成。

## <a name="example"></a>示例

在此示例中，我们检查是否[sizeof](../../c-language/sizeof-operator-c.md) **int**大于或等于 2 字节和是否[sizeof](../../c-language/sizeof-operator-c.md) **长**是 1 个字节。 程序将不进行编译，它将生成[编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)因为**长**大于 1 个字节。

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
