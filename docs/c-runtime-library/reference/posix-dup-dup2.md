---
title: dup、dup2
ms.date: 12/16/2019
api_name:
- dup2
- dup
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
- dup
- dup2
helpviewer_keywords:
- dup function
- dup2 function
ms.assetid: c7572170-47ff-4e0d-b9c3-10f0ab0ba40a
ms.openlocfilehash: ea6fe475b4a5e3cce5e9d05d89bd351361c2a4de
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301205"
---
# <a name="dup-dup2"></a>dup、dup2

Microsoft 实现的 POSIX 函数名称 `dup` 和 `dup2` 是[_dup](dup-dup2.md)和[_dup2](dup-dup2.md)函数的不推荐使用的别名。 默认情况下，它们生成[编译器警告（等级3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名称已弃用，因为它们不遵循特定于实现的名称的标准 C 规则。 但仍支持这些函数。

建议改用[_dup](dup-dup2.md)和[_dup2](dup-dup2.md) 。 或者，你可以继续使用这些函数名，并禁用警告。 有关详细信息，请参阅[关闭警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函数名称](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
