---
title: _lock
ms.date: 11/04/2016
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: c2e57af90bb9b7c6a4ba0e9efdd1dc1dc0bdb985
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606890"
---
# <a name="lock"></a>_lock

获取多线程锁定。

> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。

## <a name="syntax"></a>语法

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>参数

*locknum*<br/>
[in] 要获取的锁定标识符。

## <a name="remarks"></a>备注

如果已获取锁定，则此方法仍获取锁定会导致内部 C 运行时 (CRT) 错误。 如果此方法无法获取锁定，则它将退出并显示错误，同时将错误代码设置为 `_RT_LOCK`。

## <a name="requirements"></a>要求

**源：** mlock.c

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)