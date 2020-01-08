---
title: strlwr、wcslwr
ms.date: 12/16/2019
api_name:
- strlwr
- wcslwr
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
- wcslwr
- strlwr
helpviewer_keywords:
- strlwr function
- wcslwr function
ms.assetid: b9274824-4365-4674-b656-823c89653656
ms.openlocfilehash: ff730d6bea6619c50fefb407a7a69c50e1a06af0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301075"
---
# <a name="strlwr-wcslwr"></a>strlwr、wcslwr

特定于 Microsoft 的函数名称 `strlwr` 和 `wcslwr` 是[_strlwr 和 _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)函数的不推荐使用的别名。 默认情况下，它们生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它们不遵循特定于实现的名称的标准 C 规则。 但仍支持这些函数。

建议改用[_strlwr 或 _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)或安全增强型[_strlwr_s 和 _wcslwr_s](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)函数。 或者，你可以继续使用这些函数名，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
