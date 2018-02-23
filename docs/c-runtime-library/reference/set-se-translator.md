---
title: "_set_se_translator | Microsoft 文档"
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b5eec59acfe65189368a9b0555c3065b7159aae
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2018
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

*seTransFunction*  
指向您编写的 C 结构化异常转换器函数的指针。

## <a name="return-value"></a>返回值

返回指向由 `_set_se_translator` 注册的上一个转换器函数的指针，以便稍后能还原上一个函数。 如果已设置上一个函数，可以使用返回值还原默认行为;此值可为**nullptr**。

## <a name="remarks"></a>备注

`_set_se_translator` 函数提供一种将 Win32 异常（C 结构化异常）作为 C++ 类型异常处理的方法。 若要使每个 C 异常均由 C++ `catch` 处理程序处理，请先定义一个可以使用或从中派生的 C 异常包装器类，以将特定的类类型归于 C 异常。 若要使用此类，请安装自定义 C 异常转换器函数，该函数在每次引发 C 异常时由内部异常处理机制调用。 在转换器函数内，您可以引发可由匹配的 C++ `catch` 处理程序捕获的任意类型异常。

在使用 `_set_se_translator` 时，必须使用 [/EHa](../../build/reference/eh-exception-handling-model.md)。

若要指定自定义转换函数，调用`_set_se_translator`使用作为其自变量的转换函数的名称。 对于具有 `try` 块的堆栈上的每个函数调用，将调用编写的转换器函数一次。 没有默认的转换器函数。

转换器函数只能是引发 C++ 类型的异常。 如果它执行了除引发异常之外的任何操作（例如，对日志文件进行写入操作），您的程序可能不会按预期方式运行，因为调用转换器函数的次数是与平台相关的。

在多线程环境中，单独为每个线程维护转换器函数。 每个新线程都需要安装它自己的转换器函数。 因此，每个线程都负责处理它自己的转换。 `_set_se_translator` 特定于一个线程；另一个 DLL 可安装不同的转换函数。

*SeTransFunction*你编写的函数必须是本机编译的函数 （不使用 /clr 进行编译）。 它必须将一个无符号整数和一个指向 Win32 `_EXCEPTION_POINTERS` 结构的指针用作参数。 这些参数是通过调用 Win32 API `GetExceptionCode` 和 `GetExceptionInformation` 函数所返回的值。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

对于 `_set_se_translator`，在动态链接到 CRT 时会有影响；进程中的另一个 DLL 可能调用 `_set_se_translator` 并将您的处理程序替换为它自己的处理程序。

在从托管代码（使用 /clr 编译的）或混合的本机和托管代码中使用 `_set_se_translator` 时，请注意转换器仅影响本机代码中生成的异常。 托管代码中生成的任何托管异常（例如，在引发 `System::Exception` 时）都不会通过转换器函数进行传送。 使用 Win32 函数 `RaiseException` 的托管代码中引发的异常或由系统异常（如被零除异常）引发的异常将通过转换器传送。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_set_se_translator`|\<eh.h>|

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

虽然 `_set_se_translator` 提供的功能在托管代码中不可用，但只要使用 `/clr` 指示本机代码，就可以在本机代码中使用此映射，即使本机代码正在 `#pragma unmanaged` 开关下编译也是如此。 如果要映射的托管代码中引发了结构化的异常，必须标记生成和处理异常的代码`#pragma unmanaged`。 以下代码演示了可能的用途。 有关详细信息，请参阅 [Pragma 指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

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

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)  
[set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)  
[set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)  
[terminate](../../c-runtime-library/reference/terminate-crt.md)  
[unexpected](../../c-runtime-library/reference/unexpected-crt.md)  
