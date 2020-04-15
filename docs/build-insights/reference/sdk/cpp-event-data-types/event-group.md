---
title: 事件组类
description: C++生成见解 SDK 事件组类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324991"
---
# <a name="eventgroup-class"></a>事件组类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

类`EventGroup`模板是所有组捕获类的基类。

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

## <a name="members"></a>成员

### <a name="functions"></a>函数

[后](#back)
[开始](#begin)
[Front](#front)
[Size](#size)[operator[]](#subscript-operator)[end](#end)端前
运算符 * 大小


## <a name="back"></a><a name="back"></a>返回

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>返回值

对组中最后一个活动事件的引用。

## <a name="begin"></a><a name="begin"></a>开始

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>返回值

指向活动事件组开头的迭代器。

## <a name="end"></a><a name="end"></a>结束

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>返回值

迭代器将一个位置指向活动事件组的末尾。

## <a name="front"></a><a name="front"></a>前面

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>返回值

对组中第一个活动事件的引用。

## <a name="operator"></a><a name="subscript-operator"></a>运算符*

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>参数

*指数*\
要在活动事件组中访问的元素的索引。

### <a name="return-value"></a>返回值

存储在*索引*指示的位置的事件堆栈中的事件。

## <a name="size"></a><a name="size"></a> 大小

```cpp
size_t Size() const;
```

### <a name="return-value"></a>返回值

事件组的大小。

::: moniker-end
