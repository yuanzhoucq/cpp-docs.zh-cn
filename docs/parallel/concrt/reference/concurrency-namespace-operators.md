---
title: 并发命名空间运算符
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 676e1936af317a6ab19959f8fd09b1de06dfaf69
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883767"
---
# <a name="concurrency-namespace-operators"></a>并发命名空间运算符

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)| |

## <a name="operator_lor"></a>运算符&#124; &#124;运算符

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

### <a name="parameters"></a>parameters

*ReturnType*<br/>
已返回任务的类型。

*lhs*<br/>
要合并到结果任务的第一个任务。

rhs<br/>
要合并到结果任务的第二个任务。

### <a name="return-value"></a>返回值

在任一输入任务成功完成时成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。

### <a name="remarks"></a>备注

如果两个任务均被取消或引发异常，则返回的任务将在已取消状态下完成，并且当您对此任务调用 `get()` 或 `wait()` 时将引发一种异常（在遇到异常的情况下）。

## <a name="operator_amp_amp"></a>运算符&amp;&amp; 运算符

创建一个任务，该任务将在作为参数提供的两个任务成功完成后成功完成。

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

### <a name="parameters"></a>parameters

*ReturnType*<br/>
已返回任务的类型。

*lhs*<br/>
要合并到结果任务的第一个任务。

rhs<br/>
要合并到结果任务的第二个任务。

### <a name="return-value"></a>返回值

将在两个输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。

### <a name="remarks"></a>备注

如果其中一个任务被取消或引发异常，则返回的任务将提前完成，在 "已取消" 状态下，如果对该任务调用 `get()` 或 `wait()`，则会引发异常（如果有）。

## <a name="operator_eq_eq"></a>operator = = 运算符

测试运算符左侧的 `concurrent_vector` 对象是否等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>parameters

*T*<br/>
并发向量中存储的元素的数据类型。

*A1*<br/>
第一个 `concurrent_vector` 对象的分配器类型。

*A2*<br/>
第二个 `concurrent_vector` 对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量等于运算符右侧的并发向量，**则为 true** ; 否则为 true。否则**为 false**。

### <a name="remarks"></a>备注

如果两个并发向量具有相同的元素数，并且它们各自的元素具有相同的值，则这两个向量相等。 否则，它们不相等。

此方法对于可能修改并发向量 `_A` 或 `_B`的其他方法而言，并不是并发安全方法。

## <a name="operator_neq"></a>operator！ = 运算符

测试运算符左侧的 `concurrent_vector` 对象是否不等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>parameters

*T*<br/>
并发向量中存储的元素的数据类型。

*A1*<br/>
第一个 `concurrent_vector` 对象的分配器类型。

*A2*<br/>
第二个 `concurrent_vector` 对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果并发向量不相等，则**为 true** ;如果并发向量相等，则**为 false** 。

### <a name="remarks"></a>备注

如果两个并发向量具有相同的元素数，并且它们各自的元素具有相同的值，则这两个向量相等。 否则，它们不相等。

此方法对于可能修改并发向量 `_A` 或 `_B`的其他方法而言，并不是并发安全方法。

## <a name="operator_lt"></a>运算符&lt; 运算符

测试运算符左侧的 `concurrent_vector` 对象是否小于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>parameters

*T*<br/>
并发向量中存储的元素的数据类型。

*A1*<br/>
第一个 `concurrent_vector` 对象的分配器类型。

*A2*<br/>
第二个 `concurrent_vector` 对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量小于运算符右侧的并发向量，**则为 true** ; 否则为 false。否则**为 false**。

### <a name="remarks"></a>备注

此运算符的行为与 `std` 命名空间中 `vector` 类的等效运算符相同。

此方法对于可能修改并发向量 `_A` 或 `_B`的其他方法而言，并不是并发安全方法。

## <a name="operator_lt_eq"></a>运算符&lt;= 运算符

测试运算符左侧的 `concurrent_vector` 对象是否小于或等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>parameters

*T*<br/>
并发向量中存储的元素的数据类型。

*A1*<br/>
第一个 `concurrent_vector` 对象的分配器类型。

*A2*<br/>
第二个 `concurrent_vector` 对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量小于或等于运算符右侧的并发向量，**则为 true** ; 否则为 false。否则**为 false**。

### <a name="remarks"></a>备注

此运算符的行为与 `std` 命名空间中 `vector` 类的等效运算符相同。

此方法对于可能修改并发向量 `_A` 或 `_B`的其他方法而言，并不是并发安全方法。

## <a name="operator_gt"></a>运算符&gt; 运算符

测试运算符左侧的 `concurrent_vector` 对象是否大于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>parameters

*T*<br/>
并发向量中存储的元素的数据类型。

*A1*<br/>
第一个 `concurrent_vector` 对象的分配器类型。

*A2*<br/>
第二个 `concurrent_vector` 对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量大于运算符右侧的并发向量，**则为 true** ; 否则为 false。否则**为 false**。

### <a name="remarks"></a>备注

此运算符的行为与 `std` 命名空间中 `vector` 类的等效运算符相同。

此方法对于可能修改并发向量 `_A` 或 `_B`的其他方法而言，并不是并发安全方法。

## <a name="operator_gt_eq"></a>运算符&gt;= 运算符

测试运算符左侧的 `concurrent_vector` 对象是否大于或等于右侧的 `concurrent_vector` 对象。

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>parameters

*T*<br/>
并发向量中存储的元素的数据类型。

*A1*<br/>
第一个 `concurrent_vector` 对象的分配器类型。

*A2*<br/>
第二个 `concurrent_vector` 对象的分配器类型。

*_A*<br/>
一个 `concurrent_vector` 类型的对象。

*_B*<br/>
一个 `concurrent_vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的并发向量大于或等于运算符右侧的并发向量，**则为 true** ; 否则为 false。否则**为 false**。

### <a name="remarks"></a>备注

此运算符的行为与 `std` 命名空间中 `vector` 类的等效运算符相同。

此方法对于可能修改并发向量 `_A` 或 `_B`的其他方法而言，并不是并发安全方法。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
