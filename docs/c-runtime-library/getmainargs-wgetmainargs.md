---
title: __getmainargs、__wgetmainargs
ms.date: 11/04/2016
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 6e2bf21f2ac50d3486af56f9581ff6c8d0e0c309
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523333"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs、__wgetmainargs

调用命令行解析，并通过传递的指针将参数复制到 `main()`。

## <a name="syntax"></a>语法

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char *** _Env,
   int _DoWildCard,
_startupinfo * _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t ***_Env,
   int _DoWildCard,
   _startupinfo * _StartInfo)
```

#### <a name="parameters"></a>参数

`_Argc`<br/>
包含 `argv` 后面的参数数的整数。 `argc` 参数始终大于或等于 1。

`_Argv`<br/>
表示由杂注用户输入的命令行自变量的以 null 结尾的字符串的数组。 按照约定，`argv[0]` 是用于调用程序的命令，argv[1] 是第一个命令行参数，依此类推，直到 argv[argc]（其始终为 NULL）。 第一个命令行参数始终是 `argv[1]`，而最后一个命令行参数是 `argv[argc - 1]`。

`_Env`<br/>
表示用户环境中的变量集的字符串数组。 该数组由 NULL 项终止。

`_DoWildCard`<br/>
一个整数，如果将其设置为 1，则扩展命令行自变量中的通配符；如果设置为 0，则不执行任何操作。

`_StartInfo`<br/>
要传递给 CRT DLL 的其他信息。

## <a name="return-value"></a>返回值

如果成功，则为 0；如果失败，则为负值。

## <a name="remarks"></a>备注

在非宽字符平台上使用 `__getmainargs`，并且在宽字符 (Unicode) 平台上使用 `__wgetmainargs`。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|