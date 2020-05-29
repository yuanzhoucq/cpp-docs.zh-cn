---
title: '&lt;hash_set&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370587"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; 函数

|||
|-|-|
|[交换](#swap)|[交换 （hash_multiset）](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>交换

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。

交换两个 hash_set 的元素。

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*对*\
提供要交换的元素的hash_set，或hash_set其元素要与*hash_set的*要素交换。

*离开*\
hash_set，其要素将与hash_set*权利*者交换。

### <a name="remarks"></a>备注

模板`swap`函数是hash_set执行成员函数`left.`[交换](../standard-library/hash-set-class.md#swap)（）`right`的容器类中专用的算法。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本 

**template \<class T> void swap(T&, T&),**

在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员类 [hash_set::swap](../standard-library/hash-set-class.md#swap) 的代码示例。

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>交换 （hash_multiset）

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。

交换两个 hash_multiset 的元素。

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*对*\
提供要交换的元素hash_multiset，或hash_multiset其元素要与*hash_multiset的*要素交换。

*离开*\
hash_multiset，其要素将与hash_multiset*权*的要素交换。

### <a name="remarks"></a>备注

模板`swap`函数是容器类上专门hash_multiset执行成员函数`left.`[交换](../standard-library/hash-multiset-class.md#swap)（）`right`的算法。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本 

**template \<class T> void swap(T&, T&),**

在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员类 [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) 的代码示例。

## <a name="see-also"></a>另请参阅

[<hash_set>](../standard-library/hash-set.md)
