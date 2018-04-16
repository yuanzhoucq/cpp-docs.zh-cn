---
title: "toascii、__toascii | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
dev_langs:
- C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf4c29934d22d3f20d79650faa406f217ffdd4c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="toascii-toascii"></a>toascii、__toascii

通过截断将字符转换为 7 位 ASCII。

## <a name="syntax"></a>语法

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>参数

*c*  
要转换的字符。

## <a name="return-value"></a>返回值

`__toascii` 将的值转换*c*到 7 位 ASCII 范围，并返回结果。 没有保留任何返回值以指示错误。

## <a name="remarks"></a>备注

`__toascii` 例程通过将指定字符截断为低顺序 7 位来将其转换为 ASCII 字符。 未应用其他转换。

除非定义了预处理器宏 _CTYPE_DISABLE_MACROS，否则将 `__toascii` 例程定义为宏。 为了向后兼容，`toascii`定义为宏时，才[&#95; &#95;STDC &#95; &#95;](../../preprocessor/predefined-macros.md)未定义或定义为 0; 否则它是不确定。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`toascii`, `__toascii`|C：\<ctype.h><br /><br /> C++：\<cctype> 或 \<ctype.h>|

`toascii` 宏是 POSIX 扩展名，`__toascii` 是 POSIX 扩展的 Microsoft 专用实现。 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)   
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
[to 函数](../../c-runtime-library/to-functions.md)