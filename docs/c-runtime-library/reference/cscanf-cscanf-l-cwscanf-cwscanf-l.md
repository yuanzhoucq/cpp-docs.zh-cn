---
title: _cscanf、_cscanf_l、_cwscanf、_cwscanf_l
ms.date: 11/04/2016
apiname:
- _cscanf_l
- _cscanf
- _cwscanf
- _cwscanf_l
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
- _cwscanf
- cwscanf_l
- tcscanf_l
- _tcscanf_l
- _cscanf
- _cscanf_l
- tcscanf
- cwscanf
- _cwscanf_l
- cscanf_l
- _tcscanf
helpviewer_keywords:
- _cwscanf function
- data [C++], reading from the console
- cscanf_l function
- tcscanf function
- _cscanf_l function
- cwscanf function
- _tcscanf_l function
- _cscanf function
- _tcscanf function
- cwscanf_l function
- tcscanf_l function
- reading data [C++], from the console
- _cwscanf_l function
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
ms.openlocfilehash: 8cb121166ab0103565260538521824d8999425e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335251"
---
# <a name="cscanf-cscanfl-cwscanf-cwscanfl"></a>_cscanf、_cscanf_l、_cwscanf、_cwscanf_l

从控制台读取格式数据。 提供这些函数的更安全版本。请参阅 [_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _cscanf(
   const char *format [,
   argument] ...
);
int _cscanf_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>参数

*format*<br/>
窗体控件字符串。

*argument*<br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

已成功转换和分配的字段数。 返回值不包括已读取但未分配的字段。 返回值是**EOF**尝试读取文件的末尾。 在操作系统命令行级别重定向键盘输入时，会发生这种情况。 返回值为 0 表示没有分配任何字段。

## <a name="remarks"></a>备注

**_Cscanf**函数直接从控制台到给定的位置读取数据*自变量*。 [_Getche](getch-getwch.md) 函数用于读取字符。 每个可选参数必须是指向具有中的类型说明符相对应的类型的变量*格式*。 格式控制字段输入的解释，并且具有相同格式和函数作为*格式*参数[scanf](scanf-scanf-l-wscanf-wscanf-l.md)函数。 虽然 **_cscanf**通常回显输入的字符，不会这样执行操作，如果最后一个调用的是 **_ungetch**。

此函数验证其参数。 如果格式是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回**EOF**。

使用这些函数的版本 **_l**后缀完全相同，只不过它们使用传递中而不是当前线程区域设置的区域设置参数。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf**|**_cscanf**|**_cscanf**|**_cwscanf**|
|**_tcscanf_l**|**_cscanf_l**|**_cscanf_l**|**_cwscanf_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_cscanf**， **_cscanf_l**|\<conio.h>|
|**_cwscanf**， **_cwscanf_l**|\<conio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_cscanf.c
// compile with: /c /W3
/* This program prompts for a string
* and uses _cscanf to read in the response.
* Then _cscanf returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int   result, i[3];

   _cprintf_s( "Enter three integers: ");
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996
   // Note: _cscanf is deprecated; consider using _cscanf_s instead
   _cprintf_s( "\r\nYou entered " );
   while( result-- )
      _cprintf_s( "%i ", i[result] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
Enter three integers: 1 2 3
You entered 3 2 1
```

## <a name="see-also"></a>请参阅

[控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
