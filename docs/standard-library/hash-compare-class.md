---
title: hash_compare 类
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 4fb44a371630a66275f6ef59a0bf66b4cb73a71f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689564"
---
# <a name="hash_compare-class"></a>hash_compare 类

类模板描述了一个对象，任何哈希关联容器（hash_map、hash_multimap、hash_set 或 hash_multiset）都可使用该对象来对它们所包含的元素进行排序和哈希处理。

## <a name="syntax"></a>语法

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>备注

每个哈希关联容器都存储一个 `Traits` 类型的哈希特征对象（模板参数）。 可以从 hash_compare 专用化中派生一个类，用于选择性地重写某些函数和对象，也可以在满足某些最低要求时提供你所拥有的该类的版本。 具体而言，对于类型 `hash_compare<Key, Traits>` 的对象 hash_comp，上述容器需要以下行为：

- 对于 `Key` 类型 `key` 的所有值，调用**hash_comp**（`key`）将用作哈希函数，该函数将生成类型 `size_t` 的值的分布。 由 hash_compare 提供的函数将返回 `key`。

- 对于在序列中 `key2` 前面 `key1` 类型 `Key` 的任何值，并且具有相同的哈希值（由哈希函数返回的值）， **hash_comp**（`key2`，`key1`）为 false。 函数必须对类型 `Key` 的值施加总计排序。 Hash_compare 提供的函数将返回*comp*（`key2`、`key1`） `,` 其中， *comp*是在构造对象 hash_comp 时可以指定的类型 `Traits` 的存储对象。 对于默认 `Traits` 参数类型 `less<Key>`，排序键从不减小值。

- 整数常量 `bucket_size` 指定容器不应尝试超过的每个 "存储桶" （哈希表项）的平均元素数。 该数目必须大于零。 由 hash_compare 提供的值为 4。

- 整数常量 `min_buckets` 指定要在哈希表中维护的最小存储桶数。 该数目必须是 2 的幂且大于零。 Hash_compare 提供的值为 8。

## <a name="example"></a>示例

有关如何声明和使用 hash_compare 的示例，请参阅 [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map)、[hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap)、[hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) 和 [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) 的示例。

## <a name="requirements"></a>要求

**标头：** \<hash_map>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
