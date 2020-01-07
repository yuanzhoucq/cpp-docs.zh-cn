---
title: j0、j1、jn
ms.date: 12/16/2019
api_name:
- jn
- j0
- j1
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
- jn
- j1
- j0
helpviewer_keywords:
- jn function
- j1 function
- j0 function
ms.assetid: ec8a9512-aacb-423c-a845-fc8927e6e21d
ms.openlocfilehash: a3dc02c1e85a57be119899a962d284d923cb42d8
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299229"
---
# <a name="j0-j1-jn"></a>j0、j1、jn

Microsoft 实现的 POSIX 函数名称 `j0`、`j1`和 `jn` 是[_j0、_j1 和 _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md)函数的不推荐使用的别名。 默认情况下，它们生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它们不遵循特定于实现的名称的标准 C 规则。 但仍支持这些函数。

建议改为使用[_j0、_j1 和 _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) 。 或者，你可以继续使用这些函数名，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
