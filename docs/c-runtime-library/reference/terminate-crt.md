---
title: terminate (CRT)
ms.date: 4/2/2020
api_name:
- terminate
- _o_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1ec4e27096dd6b5fea089e21c95022542d7adc82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912226"
---
# <a name="terminate-crt"></a>terminate (CRT)

调用[abort](abort.md)或使用**set_terminate**指定的函数。

## <a name="syntax"></a>语法

```C
void terminate( void );
```

## <a name="remarks"></a>备注

**Terminate**函数与 c + + 异常处理一起使用，并在以下情况下调用：

- 无法为引发的 C++ 异常找到匹配的 catch 处理程序。

- 在堆栈展开过程中，析构函数引发了异常。

- 在引发异常后，堆栈已损坏。

默认情况下，**终止**调用[中止](abort.md)。 可以通过以下方式更改此默认设置：编写自己的终止函数并调用**set_terminate** ，并将函数名称作为其参数。 **terminate**调用作为**set_terminate**的参数提供的最后一个函数。 有关详细信息，请参阅 [未经处理的 C++ 异常](../../cpp/unhandled-cpp-exceptions.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**终止**|\<eh.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[中止](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[之外](unexpected-crt.md)<br/>
