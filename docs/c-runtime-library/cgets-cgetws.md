---
title: _cgets、_cgetws |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _cgetws
- _cgets
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cgetws
- _cgetws
- _cgets
dev_langs:
- C++
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30ac17204b5fc6df3ce3fe35e5c3acc98260076
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110055"
---
# <a name="cgets-cgetws"></a>_cgets、_cgetws

从控制台获取字符串。 提供这些函数的更多安全版本；请参阅 [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。

> [!IMPORTANT]
>  这些函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供这些函数。 这些函数（_cgets_s 和 _cgetws_s）的安全版本仍然可用。 有关这些备用函数的信息，请参阅 [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。

> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>参数

*buffer*<br/>
数据的存储位置。

## <a name="return-value"></a>返回值

在`_cgets` ， `_cgetws` 和 `buffer[2]`返回指向字符串起始位置的指针。 如果 `buffer` 为 NULL，这些函数则会调用无效的参数处理程序，如[参数验证](../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数则返回 NULL，并将 `errno` 设置为 `EINVAL`。

## <a name="remarks"></a>备注

这些函数从控制台读取字符构成的字符串，并将该字符串及其长度存储在 `buffer`指向的位置。 `buffer` 参数必须是指向字符数组的指针。 数组的第一个元素 `buffer[0]`必须包含要读取的字符串的最大长度（以字符为单位)。 该数组必须包含足够的元素，以保存该字符串、终止 null 字符 ('\0') 和 2 个其他字节。 此函数会读取字符，直至读取回车符 - 换行符 (CR-LF) 组合或指定的字符数。 字符串以开头 `buffer[2]`进行存储。 如果此函数读取 CR-LF，它会存储 null 字符 ('\0')。 然后，此函数会在第二个数组元素 `buffer[1]`中存储字符串的实际长度。

因为处于控制台窗口中时，如果调用 `_cgets` 或 `_cgetws` ，所有编辑键都会处于活动状态，所以按 F3 键可以重复最后一个输入的项。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<conio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>请参阅

[控制台和端口 I/O](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch、_getwch](../c-runtime-library/reference/getch-getwch.md)