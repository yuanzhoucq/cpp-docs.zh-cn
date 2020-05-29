---
title: EVENT_COLLECTION_DATA结构
description: C++构建见解 SDK EVENT_COLLECTION_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325696"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`EVENT_COLLECTION_DATA`结构描述了[EVENT_DATA](event-data-struct.md)元素的数组。

## <a name="syntax"></a>语法

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `Count` | 数组中的元素`EVENT_DATA`数。 |
| `Elements` | 指向数组中的第`EVENT_DATA`一个元素。 |

::: moniker-end
