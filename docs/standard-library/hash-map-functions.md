---
title: '&lt;hash_map&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 7cb2e46f19bd30e3eb313cde867c6a055cb8bca5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370615"
---
# <a name="lthash_mapgt-functions"></a>&lt;hash_map&gt; 函数

|||
|-|-|
|[交换](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a>交换 （hash_map）

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。

交换两个 hash_map 的元素。

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*对*\
hash_map的元素要与*左边*的地图的元素交换。

*离开*\
hash_map的元素要与地图*右侧*的元素交换。

### <a name="remarks"></a>备注

模板函数是容器类 hash_map 上专用化的算法，用以执行成员函数 `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法头文件中，模板函数的通用版本（**模板 \<class T> void swap(T&, T&)**）按分配工作，是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

## <a name="swap"></a><a name="swap"></a>交换

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。

交换两个 hash_multimap 的元素。

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*对*\
hash_multimap的元素要与*左边*的地图的元素交换。

*离开*\
其元素要与地图*右侧*的元素交换的hash_multimap。

### <a name="remarks"></a>备注

模板函数是容器类 hash_multimap 上专用化的算法，用以执行成员函数 `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法头文件中，模板函数的通用版本（**模板 \<class T> void swap(T&, T&)**）按分配工作，是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

## <a name="see-also"></a>另请参阅

[<hash_map>](../standard-library/hash-map.md)
