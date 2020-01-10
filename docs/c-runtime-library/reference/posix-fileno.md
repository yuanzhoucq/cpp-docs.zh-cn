---
title: fileno
ms.date: 12/16/2019
api_name:
- fileno
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
- fileno
helpviewer_keywords:
- fileno function
ms.assetid: 8f33e1e0-0dc8-4311-b690-ec6e577a64b5
ms.openlocfilehash: 798334e4139209be50c665d112f502f60909ed0f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301166"
---
# <a name="fileno"></a>fileno

Microsoft 实现的 POSIX 函数名称 `fileno` 是[_fileno](fileno.md)函数的不推荐使用的别名。 默认情况下，它会生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它不遵循特定于实现的名称的标准 C 规则。 但是，该函数仍受支持。

建议改用[_fileno](fileno.md) 。 或者，你可以继续使用此函数名称，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
