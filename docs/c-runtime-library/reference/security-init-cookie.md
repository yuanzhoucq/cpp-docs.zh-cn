---
title: __security_init_cookie | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __security_init_cookie
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
- security_init_cookie
- __security_init_cookie
dev_langs:
- C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e6bfafa1322d9730923867c86f754153f641460
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="securityinitcookie"></a>__security_init_cookie

初始化全局安全 Cookie。

## <a name="syntax"></a>语法

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>备注

全局安全 Cookie 用于在使用 [/GS（缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md)编译的代码中和使用异常处理的代码中提供缓冲区溢出保护。 进入受到溢出保护的函数时，Cookie 被置于堆栈之上；退出时，会将堆栈上的值与全局 Cookie 进行比较。 它们之间存在任何差异则表示已经发生缓冲区溢出，并导致该程序的立即终止。

通常情况下， **__security_init_cookie**由 CRT 初始化时调用。 如果绕开 CRT 初始化-例如，如果你使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)指定入口点，则必须调用 **__security_init_cookie**自己。 如果 **__security_init_cookie**不调用，全局安全 cookie 将设定为默认值和缓冲区溢出保护将受到威胁。 因为攻击者可以利用此默认 cookie 值来攻克缓冲区溢出检查，我们建议你始终调用 **__security_init_cookie**当定义你自己的入口点。

调用 **__security_init_cookie**必须在任何受到溢出保护之前进行输入函数; 否则将检测到虚假的缓冲区溢出。 有关详细信息，请参阅 [C 运行时错误 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)。

## <a name="example"></a>示例

请参阅 [C 运行时错误 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) 中的示例。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie**是标准的 C 运行库的 Microsoft 扩展。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[编译器安全检查深入介绍](http://go.microsoft.com/fwlink/p/?linkid=7260)<br/>
