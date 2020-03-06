---
title: TopDown 类
description: C++ BUILD Insights SDK TopDown 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2d4ef1f2f824bca9ab8e45f8fb030727e6e4007b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334504"
---
# <a name="topdown-class"></a>TopDown 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TopDown` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[TOP_DOWN](../event-table.md#top-down)事件。

## <a name="syntax"></a>语法

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`TopDown` 类包含以下成员：

### <a name="constructors"></a>构造函数

[TopDown](#top-down)

## <a name="top-down"></a>TopDown

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[TOP_DOWN](../event-table.md#top-down)事件。

::: moniker-end
