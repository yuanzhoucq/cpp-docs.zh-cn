---
title: _strdec、_wcsdec、_mbsdec、_mbsdec_l
ms.date: 11/04/2016
apiname:
- _wcsdec
- _strdec
- _mbsdec
- _mbsdec_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strdec
- mbsdec_l
- strdec
- _mbsdec
- _mbsdec_l
- mbsdec
- wcsdec
- _wcsdec
helpviewer_keywords:
- mbsdec_l function
- mbsdec function
- tcsdec function
- _tcsdec function
- _strdec function
- _wcsdec function
- _mbsdec_l function
- strdec function
- wcsdec function
- _mbsdec function
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
ms.openlocfilehash: a937f8fcd18dd62bb7c63cf60c250cf7986b69b7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500910"
---
# <a name="_strdec-_wcsdec-_mbsdec-_mbsdec_l"></a>_strdec、_wcsdec、_mbsdec、_mbsdec_l

比字符串指针退后一个字符。

> [!IMPORTANT]
> **mbsdec**和**mbsdec_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
unsigned char *_strdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned wchar_t *_wcsdec(
   const unsigned wchar_t *start,
   const unsigned wchar_t *current
);
unsigned char *_mbsdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned char *_mbsdec_l(
   const unsigned char *start,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*start*<br/>
指向源字符串中任意字符 (或 **_mbsdec**和 **_mbsdec_l**的第一个字节) 的指针;*开始*必须在源字符串中的*当前*之前。

*current*<br/>
指向源字符串中任意字符 (或 **_mbsdec**和 **_mbsdec_l**的第一个字节) 的指针;*当前*必须在源字符串中的*开始时间*之后。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsdec**、 **_mbsdec_l**、 **_strdec**和 **_wcsdec**都将返回一个指向紧跟在*当前*前面的字符的指针;如果*start*的值大于或等于*当前*的值, 则 **_mbsdec**返回**NULL** 。 **_tcsdec**映射到其中一个函数, 并且其返回值取决于映射。

## <a name="remarks"></a>备注

**_Mbsdec**和 **_mbsdec_l**函数返回一个指针, 该指针指向在包含*start*的字符串中紧跟在*当前*之前的多字节字符的第一个字节。

输出值受区域设置的**LC_CTYPE**类别设置的影响;有关详细信息, 请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。  **_mbsdec**根据当前使用的区域设置识别多字节字符序列, 而 **_mbsdec_l**则相同, 只不过它使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*start*或*current*为**NULL**, 则将调用无效参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则此函数将返回**EINVAL** , 并将**Errno**设置为**EINVAL**。

> [!IMPORTANT]
> 这些函数可能容易受到的缓冲区溢出的威胁。 缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsdec**|**_strdec**|**_mbsdec**|**_wcsdec**|

**_strdec**和 **_wcsdec**是 **_mbsdec**和 **_mbsdec_l**的单字节字符和宽字符版本。 仅为此映射提供了 **_strdec**和 **_wcsdec** , 否则不应使用它。

有关详细信息，请参阅[使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md)和[一般文本映射](../../c-runtime-library/generic-text-mappings.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_mbsdec**|\<mbstring.h>|\<mbctype.h>|
|**_mbsdec_l**|\<mbstring.h>|\<mbctype.h>|
|**_strdec**|\<tchar.h>||
|**_wcsdec**|\<tchar.h>||

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

下面的示例演示如何使用 **_tcsdec**。

```cpp
// crt_tcsdec.cpp
// Compile by using: cl /EHsc crt_tcsdec.cpp
#include <iostream>
#include <tchar.h>
using namespace std;

int main()
{
   const TCHAR *str = _T("12345");
   cout << "str: " << str << endl;

   const TCHAR *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   TCHAR *answer;
   answer = _tcsdec( str, str2 );
   cout << "answer: " << answer << endl;

   return (0);
}
```

下面的示例演示如何使用 **_mbsdec**。

```cpp
// crt_mbsdec.cpp
// Compile by using: cl /EHsc crt_mbsdec.c
#include <iostream>
#include <mbstring.h>
using namespace std;

int main()
{
   char *str = "12345";
   cout << "str: " << str << endl;

   char *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   unsigned char *answer;
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));

   cout << "answer: " << answer << endl;

   return (0);
}
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strinc、_wcsinc、_mbsinc、_mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc、_wcsninc、_mbsninc、_mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
