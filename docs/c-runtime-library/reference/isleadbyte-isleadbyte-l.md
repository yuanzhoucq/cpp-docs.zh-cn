---
title: isleadbyte、_isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: 1d2202bd1ca59ee42287c398da429df132e24fcb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234076"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte、_isleadbyte_l

确定一个字符是否为多字节字符的前导字节。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>参数

*ansi-c*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果参数满足测试条件，则**isleadbyte**将返回一个非零值，否则返回0。 在 "C" 区域设置和单字节字符集（SBCS）区域设置中， **isleadbyte**始终返回0。

## <a name="remarks"></a>备注

如果**isleadbyte**宏的参数是多字节字符的第一个字节，则它返回非零值。 **isleadbyte**为从-1 （**EOF**）到**UCHAR_MAX** （0xff）（含）的任何整数参数生成有意义的结果。

**Isleadbyte**的预期参数类型是 **`int`** ; 如果传递了带符号的字符，编译器可能会通过符号扩展将其转换为整数，从而产生不可预知的结果。

带有 **_l**后缀的此函数的版本是相同的，只不过它使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|始终返回 false|**_isleadbyte**|始终返回 false|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
