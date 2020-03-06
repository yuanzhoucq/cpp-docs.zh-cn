---
title: SimpleEvent 类
description: C++ BUILD Insights SDK SimpleEvent 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c30f81236138328322d8c870d4ad69d9988b49a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334588"
---
# <a name="simpleevent-class"></a>SimpleEvent 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`SimpleEvent` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它可匹配任何简单事件。 请参阅[事件表](../event-table.md)以查看可由 `SimpleEvent` 类匹配的所有事件。

## <a name="syntax"></a>语法

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Members

除了其[事件](event.md)基类中的继承成员以外，`SimpleEvent` 类包含以下成员：

### <a name="constructors"></a>构造函数

[SimpleEvent](#simple-event)

## <a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
任何简单事件。

::: moniker-end
