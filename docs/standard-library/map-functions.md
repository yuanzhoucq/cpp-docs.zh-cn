---
title: '&lt;map&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 6c3480e9ffbbab46a42ae790d8b70afbcd823457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517294"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 函数

|||
|-|-|
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|

## <a name="swap_multimap"></a>swap (map)

交换两个映射的元素。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
提供要交换的元素的映射或其元素将要进行交换与地图的地图*左*。

*left*<br/>
其元素将要进行交换与地图的地图*右*。

### <a name="remarks"></a>备注

模板函数是专用于容器类映射用以执行成员函数的算法`left`。[交换](../standard-library/map-class.md#swap)( `right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员函数 [map::swap](../standard-library/map-class.md#swap) 的代码示例。

## <a name="swap"></a>swap (multimap)

交换两个多重映射的元素。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
多重映射提供要交换的元素或其元素将要进行交换的多重映射使用 multimap*左*。

*left*<br/>
其元素将要进行交换的多重映射使用的多重映射*右*。

### <a name="remarks"></a>备注

模板函数是专用于容器类映射容器容器类多重映射，用以执行成员函数上执行的算法`left`。[交换](../standard-library/multimap-class.md#swap)(`right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员函数 [multimap::swap](../standard-library/multimap-class.md#swap) 的代码示例。

## <a name="see-also"></a>请参阅

[\<map>](../standard-library/map.md)<br/>
