---
title: value_compare 类
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 0e057a6229c903402a51b34a8f4e844e80ace187
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452373"
---
# <a name="valuecompare-class"></a>value_compare 类

提供一个函数对象，该对象能通过比较 hash_map 元素的键值来比较这些元素，以确定其在 hash_map 中的相对顺序。

## <a name="syntax"></a>语法

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>备注

Value_compare 提供的比较条件由 hash_map `value_types`包含的整个元素之间的比较结果, 由辅助类构造的各个元素的键之间的比较引起。 成员函数运算符使用 value_compare 提供的`comp`函数对象`key_compare`中存储的类型的对象来比较两个元素的排序键组件。

对于 hash_set 和 hash_multiset（二者均为键值与元素值完全相同的简单容器），value_compare 等效于 `key_compare`；对于 hash_map 和 hash_multimap，它们则不相等，因为类型 `pair` 元素的值与元素的键值不完全相同。

## <a name="example"></a>示例

有关如何声明和使用 value_compare 的示例，请参阅 [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) 的示例。

## <a name="requirements"></a>要求

**标头：** \<hash_map>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[binary_function 结构](../standard-library/binary-function-struct.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
