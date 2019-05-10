---
title: _CRTDBG_MAP_ALLOC
ms.date: 11/04/2016
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
ms.openlocfilehash: 8bcb0f5ea26218b74034eb0a41199a1104ba944d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739779"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

在应用程序的调试版本中定义 **_CRTDBG_MAP_ALLOC** 标志时，堆函数的基础版本将直接映射到其调试版本。 该标志在 Crtdbg.h 中用于执行映射。 此标志仅当已在应用程序中定义 [_DEBUG](../c-runtime-library/debug.md) 标志时才可用。

有关使用堆函数的调试版本和基础版本的更多信息，请参阅[使用调试版本与基础版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="see-also"></a>请参阅

[控制标志](../c-runtime-library/control-flags.md)
