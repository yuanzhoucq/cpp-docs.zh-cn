---
title: _countof 宏
ms.date: 03/22/2018
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 3debd63da7d218e29f31847034c69d89b4691643
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942691"
---
# <a name="_countof-macro"></a>_countof 宏

计算静态分配的数组中的元素数目。

## <a name="syntax"></a>语法

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>参数

*array*<br/>
数组的名称。

## <a name="return-value"></a>返回值

数组中的元素数，表示为**size_t**。

## <a name="remarks"></a>备注

**_countof**实现为类似于函数的预处理器宏。 如果C++传递的是指针而不是静态声明的数组，则该版本具有要在编译时检测的额外的模板机械。

确保*数组*实际上是数组，而不是指针。 在 C 中，如果*数组*是指针， **_countof**将生成错误的结果。 在C++中，如果*array*为指针，则 **_countof**无法编译。  作为参数传递给*decays 到指针*的函数的数组，这意味着在函数内，不能使用 **_countof**来确定数组的范围。

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
