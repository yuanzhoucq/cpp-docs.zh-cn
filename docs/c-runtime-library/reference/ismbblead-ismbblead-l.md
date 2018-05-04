---
title: _ismbblead、_ismbblead_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbblead_l
- _ismbblead
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
dev_langs:
- C++
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2d85459f4addf0688acb5a82b0108ec6133b749
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ismbblead-ismbbleadl"></a>_ismbblead、_ismbblead_l

测试字符，以确定它是否是多字节字符的前导字节。

## <a name="syntax"></a>语法

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果返回非零值整数*c*是多字节字符的第一个字节。

## <a name="remarks"></a>备注

多字节字符由前导字节后跟尾随字节构成。 通过在给定字符集中的特定范围来辨别前导字节。 例如，在代码页 932 唯一，前导字节范围为 0x81-0x9F 和 0xE0-0xFC。

**_ismbblead**对区域设置相关行为使用当前区域设置。 **_ismbblead_l**具有完全相同，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|始终返回 false|**_ismbblead**|始终返回 false|

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbblead_l**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|

\* 适用于测试条件的清单常量。

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
