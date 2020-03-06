---
title: 事件类
description: C++ BUILD Insights SDK 事件类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334888"
---
# <a name="event-class"></a>事件类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Event` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它可匹配任何事件。

## <a name="syntax"></a>语法

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

[Event](#entity)

### <a name="functions"></a>函数

[数据](#data)
[EventId](#event-id)\
[EventInstanceId](#event-instance-id)\
[事件名称](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[时间戳](#timestamp)

## <a name="entity"></a>引发

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
任何事件。

## <a name="data"></a>数据

```cpp
const void* Data() const;
```

### <a name="return-value"></a>返回值

指向此事件中包含的额外数据的指针。 有关如何解释此字段的详细信息，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="event-id"></a>EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>返回值

标识事件类型的数字。 有关事件标识符的列表，请参阅[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>返回值

一个数字，用于唯一标识跟踪内的事件。 多次分析或 relogging 同一跟踪时，此值不会发生更改。 此值用于标识多个分析中的同一事件，或 relogging 在同一跟踪上传递的事件。

## <a name="event-name"></a>名

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>返回值

包含[EventId](#event-id)标识的事件类型名称的 ANSI 字符串。

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>返回值

宽字符串，其中包含[EventId](#event-id)标识的事件的名称。

## <a name="process-id"></a>ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>返回值

发生事件的进程的标识符。

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>返回值

发生事件的逻辑处理器的从零开始的索引。

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>返回值

发生事件的线程的标识符。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>返回值

计算此事件的持续时间时，每秒要使用的计时周期数。

## <a name="timestamp"></a>标志

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>返回值

如果事件是活动，则此函数将返回在活动开始时捕获的滴答值。 对于简单的事件，此函数返回事件发生时捕获的滴答值。

::: moniker-end
