---
title: _set_se_translator | Microsoft 文档
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_se_translator
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
- _set_se_translator
- set_se_translator
dev_langs:
- C++
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d4a5c9e86023ea47f23b648cad1a4dffedf905b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="setsetranslator"></a>_set_se_translator

设置用于将转换到 c + + 的 Win32 异常 （C 结构化异常） 的每个线程回调函数类型的异常。

## <a name="syntax"></a>语法

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>参数

*seTransFunction*<br/>
指向您编写的 C 结构化异常转换器函数的指针。

## <a name="return-value"></a>返回值

返回指向上一个转换器函数的注册的 **_set_se_translator**，以便稍后能还原上一个函数。 如果已设置上一个函数，可以使用返回值还原默认行为;此值可为**nullptr**。

## <a name="remarks"></a>备注

**_Set_se_translator**函数提供了一种将 Win32 异常 （C 结构化异常） 处理为 c + + 方法类型的异常。 若要允许每个 C 异常均由 c + +**捕获**处理程序，首先定义 C 异常包装器类，可使用，或从派生以特定类类型归于 C 异常。 若要使用此类，请安装自定义 C 异常转换器函数，该函数在每次引发 C 异常时由内部异常处理机制调用。 在转换器函数，你可以引发可由匹配的 c + + 捕获任何类型化的异常**捕获**处理程序。

必须使用[/EHa](../../build/reference/eh-exception-handling-model.md)时使用 **_set_se_translator**。

若要指定自定义转换函数，调用 **_set_se_translator**使用作为其自变量的转换函数的名称。 你编写的转换器函数具有的堆栈上每个函数调用一次**重**块。 没有默认的转换器函数。

转换器函数只能是引发 C++ 类型的异常。 如果它执行了除引发异常之外的任何操作（例如，对日志文件进行写入操作），您的程序可能不会按预期方式运行，因为调用转换器函数的次数是与平台相关的。

在多线程环境中，单独为每个线程维护转换器函数。 每个新线程都需要安装它自己的转换器函数。 因此，每个线程都负责处理它自己的转换。 **_set_se_translator**特定于一个线程; 另一个 DLL 可安装不同的转换函数。

*SeTransFunction*你编写的函数必须是本机编译的函数 （不使用 /clr 进行编译）。 它必须将一个无符号的整数和一个指针，Win32 **_EXCEPTION_POINTERS**作为自变量的结构。 自变量是对 Win32 API 的调用的返回值**GetExceptionCode**和**GetExceptionInformation**函数。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

有关 **_set_se_translator**，动态链接到 CRT 时会有影响; 进程中的 DLL 可能调用另一个 **_set_se_translator**并将您的处理程序替换为其自身。

使用时 **_set_se_translator**从托管代码 （使用 /clr 编译的代码） 或混合的本机和托管代码，请注意转换器影响仅调试本机代码中生成的异常。 托管代码中生成的任何托管异常（例如，在引发 `System::Exception` 时）都不会通过转换器函数进行传送。 在使用 Win32 函数的托管代码中引发的异常**RaiseException**或由系统异常像除数为零异常将通过转换器传送。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class SE_Exception
{
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func);
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>示例

虽然提供的功能 **_set_se_translator**是在托管代码中不可用，就可以使用此映射在本机代码中，即使该本机代码正在下编译 **/clr**只要使用指示本机代码中切换`#pragma unmanaged`。 如果要映射的托管代码中引发了结构化的异常，必须标记生成和处理异常的代码`#pragma unmanaged`。 以下代码演示了可能的用途。 有关详细信息，请参阅 [Pragma 指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class CMyException{
private:
    unsigned int nSE;
public:
    CMyException() : nSE{ 0 } {}
    CMyException(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw CMyException(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(CMyException e)
    {
        printf("Caught CMyException.\n");
    }
    catch(...)
    {
        printf("Caught unexpected SEH exception.\n");
    }
}
#pragma managed

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught CMyException, error c0000094
```

## <a name="see-also"></a>请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
