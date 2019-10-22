---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 19068de41cfdcb17ae624858c137bf624851479f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684073"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

定义容器类模板向量和多个支持模板。

`vector` 是将给定类型的元素组织到线性序列中的容器。 它使用户可以快速随机访问任何元素，并动态添加到序列和动态从序列中删除。 `vector` 是随机访问性能超出限制时的首选序列容器。

> [!NOTE]
> > 库 \<vector 也使用了 `#include <initializer_list>` 语句。

有关类 `vector` 的详细信息，请参阅 [vector 类](../standard-library/vector-class.md)。 有关专业化 `vector<bool>` 的信息，请参阅 [vector\<bool> 类](../standard-library/vector-bool-class.md)。

## <a name="syntax"></a>语法

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>参数

*类型*\
向量中所存储的数据类型的模板参数。

*分配*器 \
负责分配和释放内存的已存储分配器对象的模板参数。

*左*\
比较操作中的第一个（左）向量

*right* \
比较操作中的第二个（右）向量。

## <a name="members"></a>Members

### <a name="operators"></a>运算符

|||
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|测试运算符左侧的向量对象是否等于右侧的向量对象。|
|[operator<](../standard-library/vector-operators.md#op_lt)|测试运算符左侧的向量对象是否小于右侧的向量对象。|
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|测试运算符左侧的向量对象是否小于或等于右侧的向量对象。|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|测试运算符左侧的向量对象是否等于右侧的向量对象。|
|[operator>](../standard-library/vector-operators.md#op_gt)|测试运算符左侧的向量对象是否大于右侧的向量对象。|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|测试运算符左侧的向量对象是否大于或等于右侧的向量对象。|

### <a name="classes"></a>类

|||
|-|-|
|[vector 类](../standard-library/vector-class.md)|序列容器的一个类模板，它将给定类型的元素以线性排列方式进行排列，并且允许快速随机访问任何元素。|

### <a name="specializations"></a>专用化

|||
|-|-|
|hash|返回向量的哈希值。|
|[vector\<bool> 类](../standard-library/vector-bool-class.md)|@No__t_0 类型的元素的类模板向量的完全专用化，其中包含用于专用化的基础类型的分配器。|

## <a name="requirements"></a>要求

**标头：** \<vector>

**命名空间:** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
