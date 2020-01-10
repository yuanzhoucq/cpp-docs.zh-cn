---
title: y0、y1、yn
ms.date: 12/16/2019
api_name:
- y1
- yn
- y0
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
- yn
- y1
- y0
helpviewer_keywords:
- y0 function
- y1 function
- yn function
ms.assetid: e14215f3-53d4-4ae8-816e-4c1ec2019316
ms.openlocfilehash: ade2978d9a052b481c8250933257cfa33493860f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301712"
---
# <a name="y0-y1-yn"></a>y0、y1、yn

Microsoft 实现的 POSIX 函数名称 `y0`、`y1`和 `yn` 是[_y0、_y1 和 _yn](bessel-functions-j0-j1-jn-y0-y1-yn.md)函数的不推荐使用的别名。 默认情况下，它们生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它们不遵循特定于实现的名称的标准 C 规则。 但仍支持这些函数。

建议改为使用[_y0、_y1 和 _yn](bessel-functions-j0-j1-jn-y0-y1-yn.md) 。 或者，你可以继续使用这些函数名，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
