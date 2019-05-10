---
title: hash_compare 类
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: f535122b67f854b8b204664b829ce9da5fe3c6a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159816"
---
# <a name="hashcompare-class"></a>hash_compare 类

此模板类描述了一个对象，任何哈希关联容器（hash_map、hash_multimap、hash_set 或 hash_multiset）都可将该对象用作默认的 **Traits** 参数对象，以对其所包含的元素进行排序和哈希处理。

## <a name="syntax"></a>语法

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>备注

每个哈希关联容器都存储类型的哈希特征对象`Traits`（模板参数）。 可以从 hash_compare 专用化中派生一个类，用于选择性地重写某些函数和对象，也可以在满足某些最低要求时提供你所拥有的该类的版本。 具体而言，对于类型的对象 hash_comp `hash_compare<Key, Traits>`，上述容器需要以下行为：

- 所有值`key`类型的`Key`，在调用**hash_comp**(`key`) 用作哈希函数，这将产生的类型的值的分布`size_t`。 由 hash_compare 提供的函数将返回 `key`。

- 对于任何值`key1`类型的`Key`前面`key2`序列中且具有相同哈希值 （由哈希函数返回的值）， **hash_comp**(`key2`， `key1`) 为 false。 该函数必须施加全面排序类型的值`Key`。 由 hash_compare 提供的函数返回*comp*(`key2`， `key1`)`,`其中*comp*是类型的存储的对象`Traits`，可以指定当您构造对象 hash_comp。 默认情况下`Traits`参数类型`less<Key>`，排序关键字永远不会减小值。

- 整数常量`bucket_size`指定平均每个"存储桶"（哈希表项） 的容器不应尝试超过的元素数目。 该数目必须大于零。 由 hash_compare 提供的值为 4。

- 整数常量`min_buckets`指定要保留在哈希表中的存储桶的最小数目。 该数目必须是 2 的幂且大于零。 Hash_compare 提供的值为 8。

## <a name="example"></a>示例

有关如何声明和使用 hash_compare 的示例，请参阅 [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map)、[hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap)、[hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) 和 [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) 的示例。

## <a name="requirements"></a>要求

**标头：**\<hash_map>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
