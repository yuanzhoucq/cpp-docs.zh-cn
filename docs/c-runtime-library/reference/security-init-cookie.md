---
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 9f7e9924f4a96803749418d777e5ee2020f9df78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948721"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

初始化全局安全 Cookie。

## <a name="syntax"></a>语法

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>备注

全局安全 Cookie 用于在使用 [/GS（缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md)编译的代码中和使用异常处理的代码中提供缓冲区溢出保护。 进入受到溢出保护的函数时，Cookie 被置于堆栈之上；退出时，会将堆栈上的值与全局 Cookie 进行比较。 它们之间存在任何差异则表示已经发生缓冲区溢出，并导致该程序的立即终止。

通常， **__security_init_cookie**在初始化时由 CRT 调用。 如果你跳过 CRT 初始化（例如，如果你使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)来指定入口点），则必须自己调用 **__security_init_cookie** 。 如果未调用 **__security_init_cookie** ，则全局安全 cookie 设置为默认值，缓冲区溢出保护将受到威胁。 由于攻击者可利用此默认 cookie 值来击败缓冲区溢出检查，因此，我们建议您在定义自己的入口点时始终调用 **__security_init_cookie** 。

必须先对 **__security_init_cookie**进行调用，然后才能进入溢出保护的函数。否则，将检测到虚假的缓冲区溢出。 有关详细信息，请参阅 [C 运行时错误 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)。

## <a name="example"></a>示例

请参阅 [C 运行时错误 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) 中的示例。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie**是标准 C 运行库的 Microsoft 扩展。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[Microsoft 安全响应中心](https://www.microsoft.com/msrc?rtc=1)
