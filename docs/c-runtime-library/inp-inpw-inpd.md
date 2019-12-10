---
title: sct.inp、_inp、inpw、_inpw、_inpd
description: 描述 Microsoft C 运行时库（CRT）的已过时和已删除的 sct.inp、_inp、inpw、_inpw 和 _inpd 函数。
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
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
ms.openlocfilehash: 48e0e58d2886c5a8bb90a86c81cb785d364666e8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988709"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>sct.inp、_inp、inpw、_inpw、_inpd

输入、端口、字节（`inp`、`_inp`）、字（`inpw`、`_inpw`）或双字（`_inpd`）。

> [!IMPORTANT]
> 这些函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供这些函数。  
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```cpp
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

### <a name="parameters"></a>参数

*端口*\
I/O 端口号。

## <a name="return-value"></a>返回值

这些函数返回从 `port`中读取的字节、字或双字。 无错误返回。

## <a name="remarks"></a>备注

`_inp`、 `_inpw`和 `_inpd` 函数分别从指定的输入端口读取一个字节、一个字和一个双字。 输入值可以是 0 - 65,535 范围内的任何无符号短整数。

由于这些函数可直接从 I/O 端口读取数据，因此无法用于用户代码。

`inp` 和 `inpw` 名称是 `_inp` 和 `_inpw` 函数的旧的、不推荐使用的名称。 有关详细信息，请参阅[POSIX 函数名称](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

## <a name="requirements"></a>需求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

有关兼容性的详细信息，请参阅 [兼容性](../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[控制台和端口 I/O](../c-runtime-library/console-and-port-i-o.md)\
[outp、outpw、_outp、_outpw _outpd](../c-runtime-library/outp-outpw-outpd.md)
