---
title: value_compare 类（&lt;映射&gt;）| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46f8d00877aa4147e4b3e4ec2a6a23b70d8154c8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965843"
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

提供的比较条件`value_compare`之间`value_types`的由 map 包含的整个元素的比较将引发之间的相应元素的辅助类构造的密钥。 成员函数运算符使用的对象`comp`类型的`key_compare`提供的函数对象中存储`value_compare`用于比较两个元素的排序键组件。

对于 set 和 multiset（二者均为键值与元素值完全相同的简单容器），`value_compare` 等效于 `key_compare`；对于 map 和 multimap，它们则不相等，因为类型 `pair` 元素的值与元素的键值不完全相同。

## <a name="example"></a>示例

有关如何声明和使用 `value_compare` 的示例，请参阅 [value_comp](../standard-library/map-class.md#value_comp) 的示例。

## <a name="requirements"></a>要求

**Header:** \<map>

**命名空间：** std

## <a name="see-also"></a>请参阅

[binary_function 结构](../standard-library/binary-function-struct.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
