---
title: stricmp、wcsicmp
ms.date: 12/16/2019
api_name:
- stricmp
- wcsicmp
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
- stricmp
- wcsicmp
helpviewer_keywords:
- stricmp function
- wcsicmp function
ms.assetid: 2e3c6703-2635-4961-a253-e2c4c5029ed8
ms.openlocfilehash: d47249a3b41c76bf87ece8ed2e8a0fbbfc05ff09
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300503"
---
# <a name="stricmp-wcsicmp"></a>stricmp、wcsicmp

特定于 Microsoft 的函数名称 `stricmp` 和 `wcsicmp` 是[_stricmp 和 _wcsicmp](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)函数的不推荐使用的别名。 默认情况下，它们生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它们不遵循特定于实现的名称的标准 C 规则。 但仍支持这些函数。

建议改用[_stricmp 或 _wcsicmp](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md) 。 或者，你可以继续使用这些函数名，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
