---
title: EVENT_COLLECTION_DATA 结构
description: C++生成见解 SDK EVENT_COLLECTION_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335242"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_COLLECTION_DATA` 结构描述了[EVENT_DATA](event-data-struct.md)元素的数组。

## <a name="syntax"></a>语法

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Count` | 数组中 `EVENT_DATA` 元素的数目。 |
| `Elements` | 指向数组中第一个 `EVENT_DATA` 元素的指针。 |

::: moniker-end
