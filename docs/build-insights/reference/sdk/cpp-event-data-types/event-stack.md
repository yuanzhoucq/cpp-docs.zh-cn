---
title: EventStack 类
description: C++ BUILD Insights SDK EventStack 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334894"
---
# <a name="eventstack-class"></a>EventStack 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`EventStack` 类是[事件](event.md)对象的集合。 从C++生成见解 SDK 接收的所有事件都以 `EventStack` 对象的形式提供。 此堆栈中的最后一项是当前正在处理的事件。 最后一个条目之前的条目是当前事件的父层次结构。 有关生成见解中C++使用的事件模型的详细信息，请参阅[事件表](../event-table.md)。

## <a name="syntax"></a>语法

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

[EventStack](#event-stack)

### <a name="functions"></a>函数

[Back](#back)
[运算符 []](#subscript-operator)
[大小](#size)

## <a name="back"></a>返回

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>返回值

表示堆栈中最后一项的[RawEvent](raw-event.md)对象。 事件堆栈中的最后一项是触发的事件。

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>参数

*数据*\
从中生成 `EventStack` 的原始数据。

### <a name="remarks"></a>备注

通常不需要自己构造 `EventStack` 的对象。 当在分析或 relogging 会话过程C++中处理事件时，生成见解 SDK 会提供这些事件。

## <a name="subscript-operator"></a>运算符 []

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>参数

*索引*\
要在事件堆栈中访问的元素的索引。

### <a name="return-value"></a>返回值

一个[RawEvent](raw-event.md)对象，该对象表示存储在事件堆栈中的*索引*所指示的位置上的事件。

## <a name="size"></a>规格

```cpp
size_t Size() const;
```

### <a name="return-value"></a>返回值

事件堆栈的大小。

::: moniker-end
