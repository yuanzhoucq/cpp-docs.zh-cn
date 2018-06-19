---
title: vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 738a69ad0acd1af3b400b56f0f759414b9e28578
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451597"
---
# <a name="vsnprintf-vsnprintf-vsnprintfl-vsnwprintf-vsnwprintfl"></a>vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l

使用指向参数列表的指针写入格式化的输出。 提供这些函数的更多安全版本；请参阅 [vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)。

## <a name="syntax"></a>语法

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
输出的存储位置

*count*<br/>
要写入的最大字符数。

*format*<br/>
格式规范。

*argptr*<br/>
指向参数列表的指针。

*locale*<br/>
要使用的区域设置。

有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>返回值

**Vsnprintf**函数将返回写入的字符数，不包括终止 null 字符。 如果缓冲区大小指定*计数*足够大，无法包含由指定的输出*格式*和*argptr*的返回值**vsnprintf** ，则会写入，如果不包括 null 字符的字符数*计数*足够大。 如果返回的值大于*计数*-1，输出已被截断。 返回值 -1 指示发生编码错误。

同时 **_vsnprintf**和 **_vsnwprintf**函数将返回写入要写入的字符数是否小于或等于的字符数*计数*; 如果数字格式要写入的字符大于*计数*，则这些函数返回-1，指示输出已被截断。

不论是否写入终止 null，所有这些函数的返回值都不会将其包含在内。 当*计数*为零，返回的值编写函数，不的字符数包括任何终止 null。 可以将此结果用于为字符串和终止 null 分配足够的缓冲区空间，然后再次调用可填充缓冲区的函数。

如果*格式*是**NULL**，或者如果*缓冲区*是**NULL**和*计数*不等于零，这些函数中所述将调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回-1 并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

其中每个函数采用指向自变量列表，然后将格式化数据，并最多写入*计数*指向的内存的字符*缓冲区*。 **Vsnprintf**函数始终会写入一个 null 终止符，即使它截断输出。 使用时 **_vsnprintf**和 **_vsnwprintf**，缓冲区才将 null 终止仅当有空间末尾 (即，如果要写入的字符数小于*计数*).

> [!IMPORTANT]
> 若要防止某些类型的安全风险，确保*格式*不是用户定义的字符串。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

> [!NOTE]
> 若要确保在调用时没有终止 null 的空间 **_vsnprintf**， **_vsnprintf_l**， **_vsnwprintf**和 **_vsnwprintf_l**，请确保*计数*严格小于缓冲区长度并将缓冲区初始化为 null 在调用函数之前。
>
> 因为**vsnprintf**始终会写入终止 null*计数*参数可能等于缓冲区的大小。

从 Visual Studio 2015 和 Windows 10 中的 UCRT 开始**vsnprintf**不再等同于 **_vsnprintf**。 **Vsnprintf**函数遵循 C99 标准;**_vnsprintf**保留用于替换旧的 Visual Studio 代码向后兼容。

使用这些函数的版本 **_l**后缀是相同，只不过它们使用传递而不是当前线程区域设置的区域设置参数。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**， **_vsnprintf**， **_vsnprintf_l**|\<stdio.h>|\<stdio.h> 或 \<cstdio>|
|**_vsnwprintf**， **_vsnwprintf_l**|\<stdio.h> 或 \<wchar.h>|\<stdio.h>、\<wchar.h>、\<cstdio> 或 \<cwchar>|

**_Vsnprintf**， **_vsnprintf_l**， **_vsnwprintf**和 **_vsnwprintf_l**函数是 Microsoft 特定。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

如果使用 vsnprintf 以及窄字符串参数代替，结果会发生更改。 *计数*参数可以是整个大小的缓冲区，并且返回值是将如果已写入的字符数*计数*是否足够大：

## <a name="example"></a>示例

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函数](../../c-runtime-library/vprintf-functions.md)<br/>
[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
