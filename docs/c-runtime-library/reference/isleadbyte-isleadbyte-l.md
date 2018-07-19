---
title: isleadbyte、_isleadbyte_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _isleadbyte_l
- isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs:
- C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 682cdde6983c5e590920c43418e510b9c275b34e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401013"
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte、_isleadbyte_l

确定一个字符是否为多字节字符的前导字节。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

**isleadbyte**如果自变量满足测试条件或 0，如果它不返回非零值。 在"C"区域设置和单字节字符集 (SBCS) 区域设置中， **isleadbyte**始终返回 0。

## <a name="remarks"></a>备注

**Isleadbyte**宏返回非零值，如果该参数是多字节字符的第一个字节。 **isleadbyte**生成有意义的结果的任何整数自变量在-1 (**EOF**) 到**UCHAR_MAX** (0xFF) （含)。

预期自变量类型**isleadbyte**是**int**; 如果传递了带符号的字符，编译器可能将其转换为整数通过符号扩展，从而生成不可预知的结果。

使用此函数的版本 **_l**后缀是相同，但它使用传递区域设置而不是当前区域设置其区域设置相关的行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|始终返回 false|**_isleadbyte**|始终返回 false|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
