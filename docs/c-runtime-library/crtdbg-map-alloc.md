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
ms.openlocfilehash: a6b6ca5d3e6fdc1bac43d082b0d7df5a87830050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453428"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

在应用程序的调试版本中定义 **_CRTDBG_MAP_ALLOC** 标志时，堆函数的基础版本将直接映射到其调试版本。 该标志在 Crtdbg.h 中用于执行映射。 此标志仅当已在应用程序中定义 [_DEBUG](../c-runtime-library/debug.md) 标志时才可用。

有关使用堆函数的调试版本和基础版本的更多信息，请参阅[使用调试版本与基础版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="see-also"></a>请参阅

[控制标志](../c-runtime-library/control-flags.md)