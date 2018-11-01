---
title: vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l
ms.date: 11/04/2016
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: 6654588754bbd8a8d6f6ac4c5dcd8361e932a5e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480556"
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l

使用指向参数列表的指针写入格式化的输出。 这些版本的 [vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
输出的存储位置

*sizeOfBuffer*<br/>
大小*缓冲区*用于输出，如的字符数。

*count*<br/>
要写入的字符最大数量（不包括终止 null 或 [_TRUNCATE](../../c-runtime-library/truncate.md)）。

*format*<br/>
格式规范。

*argptr*<br/>
指向参数列表的指针。

*locale*<br/>
要使用的区域设置。

有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>返回值

**vsnprintf_s**， **_vsnprintf_s**并 **_vsnwprintf_s**返回写入的字符，不包括终止 null，则为负值，如果发生输出错误数。 **vsnprintf_s**等同于 **_vsnprintf_s**。 **vsnprintf_s**包含 ANSI 标准的符合性。 **_vnsprintf**保留用于向后兼容。

如果所需存储数据和终止 null 的存储超出*sizeOfBuffer*，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)，除非*计数*是[_TRUNCATE](../../c-runtime-library/truncate.md)，在这种情况下尽可能多的字符串一样将中容纳不下*缓冲区*写入并返回-1。 如果将无效参数处理程序后继续执行，这些函数将设置*缓冲区*为空字符串，设置**errno**到**ERANGE**，并返回-1。

如果*缓冲区*或*格式*是**NULL**指针，或者如果*计数*小于或等于 0，将调用无效参数处理程序。 如果允许继续执行，这些函数将设置**errno**到**EINVAL**并返回-1。

### <a name="error-conditions"></a>错误条件

|**条件**|返回|**errno**|
|-----------------|------------|-------------|
|*缓冲区*是**NULL**|-1|**EINVAL**|
|*格式*是**NULL**|-1|**EINVAL**|
|*计数*< = 0|-1|**EINVAL**|
|*sizeOfBuffer*太小 (和*计数*！ = **_TRUNCATE**)|-1 (和*缓冲区*设置为空字符串)|**ERANGE**|

## <a name="remarks"></a>备注

每个函数采用一个指向参数列表，然后格式化和最多写入*计数*指向的内存的给定数据的字符*缓冲区*并追加终止 null。

如果*计数*是[_TRUNCATE](../../c-runtime-library/truncate.md)，则这些函数编写尽可能多的字符串将能放入*缓冲区*保留终止 null 空间时。 如果整个字符串 （具有终止 null) 适合*缓冲区*，则这些函数将返回写入 （不包括终止 null） 的字符数; 否则，这些函数将返回-1 指示该截断出现。

使用这些函数的版本 **_l**后缀完全相同，只不过它们使用传递中而不是当前线程区域设置的区域设置参数。

> [!IMPORTANT]
> 确保 format 不是用户定义的字符串。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

> [!NOTE]
> 若要确保终止 null 的空间，请确保*计数*严格小于缓冲区长度或使用 **_TRUNCATE**。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**， **_vsnprintf_s_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**， **_vsnwprintf_s_l**|\<stdio.h> 或 \<wchar.h> 和 \<stdarg.h>|\<varargs.h>*|

\* 仅对 UNIX V 兼容性是必需的。

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函数](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
