---
title: 并发命名空间运算符
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374384"
---
# <a name="concurrency-namespace-operators"></a>并发命名空间运算符

||||
|-|-|-|
|[操作员！](#operator_neq)|[算子&amp;&amp;](#operator_amp_amp)|[算子&gt;](#operator_gt)|
|[算子&gt;=](#operator_gt_eq)|[算子&lt;](#operator_lt)|[算子&lt;=](#operator_lt_eq)|
|[运算符*](#operator_eq_eq)|[运算符&#124;&#124;](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>操作员&#124;&#124; 操作员

创建将在作为参数提供的任一任务成功完成时成功完成的任务。

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>参数

*返回类型*<br/>
已返回任务的类型。

*lhs*<br/>
要合并到结果任务的第一个任务。

rhs**<br/>
要合并到结果任务的第二个任务。

### <a name="return-value"></a>返回值

当任一输入任务成功完成时，该任务成功完成。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。

### <a name="remarks"></a>备注

如果两个任务均被取消或引发异常，则返回的任务将在已取消状态下完成，并且当您对此任务调用 `get()` 或 `wait()` 时将引发一种异常（在遇到异常的情况下）。

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>操作员&amp;&amp;

创建一个任务，当作为参数提供的两个任务成功完成时，该任务将成功完成。

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>参数

*返回类型*<br/>
已返回任务的类型。

*lhs*<br/>
要合并到结果任务的第一个任务。

rhs**<br/>
要合并到结果任务的第二个任务。

### <a name="return-value"></a>返回值

将在两个输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。

### <a name="remarks"></a>备注

如果其中一个任务被取消或引发异常，则返回的任务将提前完成，处于已取消状态，如果发生异常，则在调用`get()`或`wait()`执行该任务时将引发异常。

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>运算符 = 运算符

测试运算符左侧的 `concurrent_vector` 对象是否等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
存储在并发矢量中的元素的数据类型。

*A1*<br/>
第一`concurrent_vector`个对象的分配器类型。

*A2*<br/>
第二`concurrent_vector`个对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量等于运算符右侧的并发矢量，**则为 true;** 否则**错误**。

### <a name="remarks"></a>备注

如果两个并发矢量具有相同的元素数，并且其各自的元素具有相同的值，则它们相等。 否则，它们不相等。

对于可以修改并发向量`_A`或`_B`的其他方法，此方法并不并发安全。

## <a name="operator-operator"></a><a name="operator_neq"></a>操作员！= 操作员

测试运算符左侧的 `concurrent_vector` 对象是否不等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
存储在并发矢量中的元素的数据类型。

*A1*<br/>
第一`concurrent_vector`个对象的分配器类型。

*A2*<br/>
第二`concurrent_vector`个对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果并发向量不相等，**则为 true;** 如果并发矢量相等，**则为 false。**

### <a name="remarks"></a>备注

如果两个并发矢量具有相同的元素数，并且其各自的元素具有相同的值，则它们相等。 否则，它们不相等。

对于可以修改并发向量`_A`或`_B`的其他方法，此方法并不并发安全。

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>操作员&lt;

测试运算符左侧的 `concurrent_vector` 对象是否小于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
存储在并发矢量中的元素的数据类型。

*A1*<br/>
第一`concurrent_vector`个对象的分配器类型。

*A2*<br/>
第二`concurrent_vector`个对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发矢量小于运算符右侧的并发矢量，**则为 true;** 否则**错误**。

### <a name="remarks"></a>备注

此运算符的行为与`vector``std`命名空间中类的等效运算符相同。

对于可以修改并发向量`_A`或`_B`的其他方法，此方法并不并发安全。

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>运算符&lt;= 运算符

测试运算符左侧的 `concurrent_vector` 对象是否小于或等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
存储在并发矢量中的元素的数据类型。

*A1*<br/>
第一`concurrent_vector`个对象的分配器类型。

*A2*<br/>
第二`concurrent_vector`个对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量小于或等于运算符右侧的并发矢量，**则为 true;** 否则**错误**。

### <a name="remarks"></a>备注

此运算符的行为与`vector``std`命名空间中类的等效运算符相同。

对于可以修改并发向量`_A`或`_B`的其他方法，此方法并不并发安全。

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>操作员&gt;

测试运算符左侧的 `concurrent_vector` 对象是否大于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
存储在并发矢量中的元素的数据类型。

*A1*<br/>
第一`concurrent_vector`个对象的分配器类型。

*A2*<br/>
第二`concurrent_vector`个对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发矢量大于运算符右侧的并发矢量，**则为 true;** 否则**错误**。

### <a name="remarks"></a>备注

此运算符的行为与`vector``std`命名空间中类的等效运算符相同。

对于可以修改并发向量`_A`或`_B`的其他方法，此方法并不并发安全。

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>运算符&gt;= 运算符

测试运算符左侧的 `concurrent_vector` 对象是否大于或等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
存储在并发矢量中的元素的数据类型。

*A1*<br/>
第一`concurrent_vector`个对象的分配器类型。

*A2*<br/>
第二`concurrent_vector`个对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发矢量大于或等于运算符右侧的并发矢量，**则为 true;** 否则**错误**。

### <a name="remarks"></a>备注

此运算符的行为与`vector``std`命名空间中类的等效运算符相同。

对于可以修改并发向量`_A`或`_B`的其他方法，此方法并不并发安全。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
