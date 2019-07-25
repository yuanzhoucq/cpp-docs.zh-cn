---
title: value_compare 类（&lt;映射&gt;）
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: d098e947aec1ea543f29c168a632d1f4c9412e82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448328"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare 类（&lt;映射&gt;）

提供一个函数对象，它能通过比较其键的值来比较映射的元素，以确定其在映射中的相对顺序。

## <a name="syntax"></a>语法

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>备注

由映射所包含的`value_compare`整个`value_types`元素之间提供的比较条件由辅助类构造的各个元素的键之间的比较引起。 成员函数运算符使用由`comp` `value_compare`提供的函数对象`key_compare`中存储的类型的对象来比较两个元素的排序键组件。

对于 set 和 multiset（二者均为键值与元素值完全相同的简单容器），`value_compare` 等效于 `key_compare`；对于 map 和 multimap，它们则不相等，因为类型 `pair` 元素的值与元素的键值不完全相同。

## <a name="example"></a>示例

有关如何声明和使用 `value_compare` 的示例，请参阅 [value_comp](../standard-library/map-class.md#value_comp) 的示例。

## <a name="requirements"></a>要求

**Header:** \<map>

**命名空间：** std

## <a name="see-also"></a>请参阅

[binary_function 结构](../standard-library/binary-function-struct.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
