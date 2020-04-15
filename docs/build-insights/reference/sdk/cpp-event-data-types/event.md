---
title: 事件类
description: C++生成见解 SDK 事件类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324968"
---
# <a name="event-class"></a>事件类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`Event`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配任何事件。

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

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

[事件](#entity)

### <a name="functions"></a>函数

[数据](#data)
[事件 Id](#event-id)\
[事件实例 Id](#event-instance-id)\
[事件名称](#event-name)\
[事件宽名称](#event-wide-name)\
[进程 Id](#process-id)\
[处理器索引](#processor-index)\
[线程 Id](#thread-id)\
[滴答频率](#tick-frequency)\
[时间戳](#timestamp)

## <a name="event"></a><a name="entity"></a> 事件

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
任何事件。

## <a name="data"></a><a name="data"></a>数据

```cpp
const void* Data() const;
```

### <a name="return-value"></a>返回值

指向此事件中包含的额外数据的指针。 有关如何解释此字段的详细信息，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="eventid"></a><a name="event-id"></a>事件 Id

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>返回值

标识事件类型的数字。 有关事件标识符的列表，请参阅[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>事件实例 Id

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>返回值

唯一标识跟踪内事件的数字。 多次分析或重新记录同一跟踪时，此值不会更改。 使用此值可识别多个分析或重新记录通过同一跟踪中的同一事件。

## <a name="eventname"></a><a name="event-name"></a>事件名称

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>返回值

包含[事件 Id](#event-id)标识的事件类型名称的 ANSI 字符串。

## <a name="eventwidename"></a><a name="event-wide-name"></a>事件宽名称

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>返回值

包含[EventId](#event-id)标识的事件名称的宽字符串。

## <a name="processid"></a><a name="process-id"></a>进程 Id

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>返回值

事件发生的进程的标识符。

## <a name="processorindex"></a><a name="processor-index"></a>处理器索引

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>返回值

事件发生的逻辑处理器的零基索引。

## <a name="threadid"></a><a name="thread-id"></a>线程 Id

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>返回值

发生事件的线程的标识符。

## <a name="tickfrequency"></a><a name="tick-frequency"></a>滴答频率

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>返回值

评估以此事件的刻度为单位的持续时间时，每秒使用的刻度数。

## <a name="timestamp"></a><a name="timestamp"></a>时间 戳

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>返回值

如果事件是活动，则此函数将返回在活动启动时捕获的刻度值。 对于简单事件，此函数返回事件发生时捕获的刻度值。

::: moniker-end
