---
title: 事件堆栈类
description: C++生成见解 SDK 事件堆栈类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324979"
---
# <a name="eventstack-class"></a>事件堆栈类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

类`EventStack`是[事件](event.md)对象的集合。 从C++生成见解 SDK 接收的所有事件都以`EventStack`对象的形式出现。 此堆栈中的最后一个条目是当前正在处理的事件。 最后一个条目之前的条目是当前事件的父层次结构。 有关生成见解C++中使用的事件模型的详细信息，请参阅[事件表](../event-table.md)。

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

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

[事件堆栈](#event-stack)

### <a name="functions"></a>函数

[背面](#back)
[运算符 *](#subscript-operator)
[大小](#size)

## <a name="back"></a><a name="back"></a>返回

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>返回值

表示堆栈中最后一个条目的[RawEvent](raw-event.md)对象。 事件堆栈中的最后一个条目是触发的事件。

## <a name="eventstack"></a><a name="event-stack"></a>事件堆栈

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>参数

*数据*\
生成 的原始`EventStack`数据。

### <a name="remarks"></a>备注

您通常不需要自己构造`EventStack`对象。 当分析或重新记录会话期间处理事件时，C++生成见解 SDK 会为您提供它们。

## <a name="operator"></a><a name="subscript-operator"></a>运算符*

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>参数

*指数*\
要在事件堆栈中访问的元素的索引。

### <a name="return-value"></a>返回值

一个[RawEvent](raw-event.md)对象，表示存储在事件堆栈中*索引*指示的位置的事件。

## <a name="size"></a><a name="size"></a> 大小

```cpp
size_t Size() const;
```

### <a name="return-value"></a>返回值

事件堆栈的大小。

::: moniker-end
