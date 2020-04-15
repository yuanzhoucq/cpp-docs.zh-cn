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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: dddf1d669f77805df8e00f506b6427603ac8fd9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343840"
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

*C*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果参数满足测试条件，**则 isleadbyte**返回一个非零值;如果参数满足测试条件，则返回 0。" 在"C"区域设置和单字节字符集 （SBCS） 区域设置中，**正代字节**始终返回 0。

## <a name="remarks"></a>备注

**如果 isleadbyte**宏的参数是多字节字符的第一个字节，则该宏将返回非零值。 对于从 -1 **（EOF**） 到**UCHAR_MAX** （0xFF） 的任何整数参数（包括 0xFF），**正数生成**有意义的结果。

**isleadbyte**的预期参数类型是**int;** 如果传递了签名字符，编译器可以通过符号扩展将其转换为整数，从而产生不可预知的结果。

具有 **_l**后缀的函数版本相同，只不过它使用传入区域设置，而不是当前区域设置，使其与区域设置相关的行为。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|始终返回 false|**_isleadbyte**|始终返回 false|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
