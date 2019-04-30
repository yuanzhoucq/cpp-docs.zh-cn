---
title: value_compare 类
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 4b7fff1bef091a9d47e6ea4dc0e53e86ce39ad7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365284"
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

之间的 value_compare 提供的比较条件`value_types`的由 hash_map 包含的整个元素的比较将引发之间的相应元素的辅助类构造的密钥。 成员函数运算符使用的对象`comp`类型的`key_compare`存储在由 value_compare 用于比较两个元素的排序键组件提供的函数对象。

对于 hash_set 和 hash_multiset（二者均为键值与元素值完全相同的简单容器），value_compare 等效于 `key_compare`；对于 hash_map 和 hash_multimap，它们则不相等，因为类型 `pair` 元素的值与元素的键值不完全相同。

## <a name="example"></a>示例

有关如何声明和使用 value_compare 的示例，请参阅 [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) 的示例。

## <a name="requirements"></a>要求

**标头：**\<hash_map>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[binary_function 结构](../standard-library/binary-function-struct.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
