---
title: spawnvpe
ms.date: 12/16/2019
api_name:
- spawnvpe
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
- spawnvpe
helpviewer_keywords:
- spawnvpe function
ms.assetid: be16bf98-5059-4c33-be00-7524142a017e
ms.openlocfilehash: 7166ddc2f3116ef5d2560486bd69c8525cfbdc42
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300620"
---
# <a name="spawnvpe"></a>spawnvpe

特定于 Microsoft 的函数名称 `spawnvpe` 是[_spawnvpe](spawnvpe-wspawnvpe.md)函数的不推荐使用的别名。 默认情况下，它会生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它不遵循特定于实现的名称的标准 C 规则。 但是，该函数仍受支持。

建议改用[_spawnvpe](spawnvpe-wspawnvpe.md) 。 或者，你可以继续使用此函数名称，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。
