---
title: EventGroup 类
description: C++ BUILD Insights SDK EventGroup 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334918"
---
# <a name="eventgroup-class"></a>EventGroup 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`EventGroup` 类模板是所有组捕获类的基类。

## <a name="syntax"></a>语法

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>参数

*TActivity*组中包含的活动类型。

## <a name="members"></a>Members

### <a name="functions"></a>函数

[返回](#back)
[开始](#begin)
[结束](#end)
[前](#front)
[运算符 []](#subscript-operator)
[大小](#size)

## <a name="back"></a>返回

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>返回值

对组中的最后一个活动事件的引用。

## <a name="begin"></a>准备

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>返回值

指向活动事件组开头的迭代器。

## <a name="end"></a>端面

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>返回值

一个迭代器，该迭代器指向活动事件组结尾之后的一个位置。

## <a name="front"></a>主

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>返回值

对组中第一个活动事件的引用。

## <a name="subscript-operator"></a>运算符 []

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>参数

*索引*\
要在活动事件组中访问的元素的索引。

### <a name="return-value"></a>返回值

事件堆栈中的事件，该事件存储在*索引*指示的位置。

## <a name="size"></a>规格

```cpp
size_t Size() const;
```

### <a name="return-value"></a>返回值

事件组的大小。

::: moniker-end
