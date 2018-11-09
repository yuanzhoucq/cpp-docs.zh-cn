---
title: 控制标志
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 45349099ed5c607468430d2f0a901c6374d88fc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475733"
---
# <a name="control-flags"></a>控制标志

Microsoft C 运行库的调试版本使用下列标志控制堆分配和报告过程。 有关详细信息，请参阅 [CRT 调试方法](/visualstudio/debugger/crt-debugging-techniques)。

|Flag|描述|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|将基堆函数映射到其对应的调试版本|
|[_DEBUG](../c-runtime-library/debug.md)|支持使用运行时函数的调试版本|
|[_CRTDBG_CHECK_CRT_DF](../c-runtime-library/crtdbgflag.md)|控制调试堆管理器如何跟踪分配|

这些标志可以使用 /D 命令行选项或 `#define` 指令定义。 如果标志是使用 `#define` 定义的，则指令必须在标头文件包含例程声明的语句之前显示。

## <a name="see-also"></a>请参阅

[全局变量和标准类型](../c-runtime-library/global-variables-and-standard-types.md)