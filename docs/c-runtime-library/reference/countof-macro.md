---
title: _countof 宏 | Microsoft 文档
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
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
- _countof
- countof
dev_langs:
- C++
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30df64b045e2af6181d343a4eafb962d22eaa05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394738"
---
# <a name="countof-macro"></a>_countof 宏

计算静态分配的数组中元素的数目。

## <a name="syntax"></a>语法

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>参数

*array*<br/>
数组的名称。

## <a name="return-value"></a>返回值

数组，表示为中的元素数**size_t**。

## <a name="remarks"></a>备注

**_countof**作为类似函数的预处理器宏实现。 C + + 版本都具有额外的模板机械以检测在编译时，如果在将指针传递而不是静态声明数组。

确保*数组*实际上是一个数组，不是指针。 在 C 中， **_countof**产生错误的结果，如果*数组*是指针。 C + + 中 **_countof**无法编译如果*数组*是指针。  数组作为参数传递给函数*为指针 decays*，这意味着，在函数中，你无法使用 **_countof**以确定数组的程度。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>示例

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>请参阅

[sizeof 运算符](../../cpp/sizeof-operator.md)<br/>
