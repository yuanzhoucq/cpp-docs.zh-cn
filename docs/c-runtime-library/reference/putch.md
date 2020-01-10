---
title: putch
ms.date: 12/16/2019
api_name:
- putch
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
- putch
helpviewer_keywords:
- putch function
ms.assetid: 81e733e5-770e-4c7a-b7e4-8e66da109f92
ms.openlocfilehash: 60efe440814a415da0cc51fa1b822bc1fd1f51f0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300789"
---
# <a name="putch"></a>putch

特定于 Microsoft 的函数名称 `putch` 是[_putch](putch-putwch.md)函数的不推荐使用的别名。 默认情况下，它会生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它不遵循特定于实现的名称的标准 C 规则。 但是，该函数仍受支持。

建议改用[_putch](putch-putwch.md) 。 或者，你可以继续使用此函数名称，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。
