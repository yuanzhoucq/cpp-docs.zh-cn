---
title: 引发软件异常
ms.date: 11/04/2016
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
ms.openlocfilehash: 7c58ae2e2b6635345a162d11d2b75a9865d37751
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246409"
---
# <a name="raising-software-exceptions"></a>引发软件异常

系统不会将某些最常见的程序错误源标记为异常。 例如，如果你尝试分配内存块，但没有足够的内存，则运行时或 API 函数不会引发异常，但会返回一个错误代码。

However, you can treat any condition as an exception by detecting that condition in your code and then reporting it by calling the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function. 通过按此方式标记错误，您可以将结构化异常处理的优点引入任何类型的运行时错误中。

对错误使用结构化异常处理：

- 为事件定义你自己的异常代码。

- Call `RaiseException` when you detect a problem.

- 使用异常处理筛选器来测试您定义的异常代码。

The \<winerror.h> file shows the format for exception codes. 若要确保不定义与现有异常代码发生冲突的代码，请将第三个最高有效位设置为 1。 应设置四个最高有效位，如下表所示。

|Bits|建议的二进制设置|描述|
|----------|--------------------------------|-----------------|
|31-30|11|这两个位描述代码的基本状态：11 = 错误，00 = 成功，01 = 信息性，10 = 警告。|
|29|1|客户端位。 为用户定义的代码将其设置为 1。|
|28|0|保留位。 （将其设置为 0。）|

虽然“错误”设置适用于大多数异常，但如果需要，您可将前两个位设置为 11 二进制之外的设置。 请务必记住设置 29 和 28 位，如上表所示。

The resulting error code should therefore have the highest four bits set to hexadecimal E. For example, the following definitions define exception codes that do not conflict with any Windows exception codes. （但是，你可能需要检查第三方 DLL 使用了哪些代码。）

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

在定义异常代码后，可以使用它来引发异常。 For example, the following code raises the `STATUS_INSUFFICIENT_MEM` exception in response to a memory allocation problem:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

如果只需引发异常，则可以将最后三个参数设置为 0。 最后三个参数对于传递附加信息和设置阻止处理程序继续执行的标记很有用。 See the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function in the Windows SDK for more information.

在异常处理筛选器中，您随后可以测试已定义的代码。 例如:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>请参阅

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Structured exception handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)