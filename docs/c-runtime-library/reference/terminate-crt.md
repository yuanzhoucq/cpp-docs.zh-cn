---
title: terminate (CRT)
ms.date: 11/04/2016
apiname:
- terminate
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
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1f655d328b4d97a2989ad49005ed8a9f44fd9d79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438632"
---
# <a name="terminate-crt"></a>terminate (CRT)

调用[中止](abort.md)或指定使用的函数**set_terminate**。

## <a name="syntax"></a>语法

```C
void terminate( void );
```

## <a name="remarks"></a>备注

**终止**函数与 c + + 异常处理一起使用，并在以下情况下调用：

- 无法为引发的 C++ 异常找到匹配的 catch 处理程序。

- 在堆栈展开过程中，析构函数引发了异常。

- 在引发异常后，堆栈已损坏。

**终止**调用[中止](abort.md)默认情况下。 您可以更改此默认设置编写你自己的终止函数并调用**set_terminate**与作为其参数函数的名称。 **终止**调用的最后一个函数的参数被当作**set_terminate**。 有关详细信息，请参阅 [未经处理的 C++ 异常](../../cpp/unhandled-cpp-exceptions.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**terminate**|\<eh.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
