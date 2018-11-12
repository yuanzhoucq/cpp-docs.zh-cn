---
title: _inp、_inpw、_inpd
ms.date: 11/04/2016
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: 56587455b1b5246be361afc131786d85dbc9a1a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469847"
---
# <a name="inp-inpw-inpd"></a>_inp、_inpw、_inpd

从某个端口输入一个字节 (`_inp`)、一个字 (`_inpw`) 或一个双字 (`_inpd`)。

> [!IMPORTANT]
>  这些函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供这些函数。

> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
I/O 端口号。

## <a name="return-value"></a>返回值

这些函数返回从 `port`中读取的字节、字或双字。 无错误返回。

## <a name="remarks"></a>备注

`_inp`、 `_inpw`和 `_inpd` 函数分别从指定的输入端口读取一个字节、一个字和一个双字。 输入值可以是 0 - 65,535 范围内的任何无符号短整数。

由于这些函数可直接从 I/O 端口读取数据，因此无法用于用户代码。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

有关更多兼容性信息，请参阅 [兼容性](../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[控制台和端口 I/O](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp、_outpw、_outpd](../c-runtime-library/outp-outpw-outpd.md)