---
title: "concurrent_unordered_multiset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::unsafe_erase
dev_langs: C++
helpviewer_keywords: concurrent_unordered_multiset class
ms.assetid: 219d7d67-1ff0-45f4-9400-e9cc272991a4
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58dd056bc3a4d397fc8e77b8e2c0b508b489eb2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="concurrentunorderedmultiset-class"></a>concurrent_unordered_multiset 类
`concurrent_unordered_multiset`类是并发安全容器，用于控制变长元素序列的类型 k。序列表示方式支持并发安全追加、 元素访问、 迭代器访问和迭代器遍历操作。  
  
## <a name="syntax"></a>语法  
  
```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_multiset : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
 _Hasher,
    key_equality>,
 _Allocator_type,
    true>>;
```   
  
#### <a name="parameters"></a>参数  
 `K`  
 密钥类型。  
  
 `_Hasher`  
 哈希函数对象类型。 此参数为可选参数，默认值为 `std::hash<K>`。  
  
 `key_equality`  
 相等比较函数对象类型。 此参数为可选参数，默认值为 `std::equal_to<K>`。  
  
 `_Allocator_type`  
 表示存储的分配器对象封装有关分配和解除分配适用于并发向量的内存的详细信息的类型。 此参数为可选参数，默认值为 `std::allocator<K>`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`allocator_type`|用于管理存储的分配器的类型。|  
|`const_iterator`|受控序列的常量迭代器的类型。|  
|`const_local_iterator`|受控序列的常量存储桶迭代器的类型。|  
|`const_pointer`|元素的常量指针的类型。|  
|`const_reference`|元素的常量引用的类型。|  
|`difference_type`|两个元素间的带符号距离的类型。|  
|`hasher`|哈希函数的类型。|  
|`iterator`|受控序列的迭代器的类型。|  
|`key_equal`|比较函数的类型。|  
|`key_type`|排序键的类型。|  
|`local_iterator`|受控序列的存储桶迭代器的类型。|  
|`pointer`|指向元素的指针的类型。|  
|`reference`|元素的引用的类型。|  
|`size_type`|两个元素间的无符号距离的类型。|  
|`value_type`|元素的类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[concurrent_unordered_multiset](#ctor)|已重载。 构造并发无序多重集。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[hash_function](#hash_function)|返回存储的哈希函数对象。|  
|[insert](#insert)|已重载。 添加到元素`concurrent_unordered_multiset`对象。|  
|[key_eq](#key_eq)|存储的相等性比较函数对象。|  
|[swap](#swap)|交换两个内容`concurrent_unordered_multiset`对象。 此方法不是并发安全。|  
|[unsafe_erase](#unsafe_erase)|已重载。 从其中移除元素`concurrent_unordered_multiset`指定位置处。 此方法不是并发安全。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|已重载。 将分配的另一个内容`concurrent_unordered_multiset`于此对象。 此方法不是并发安全。|  
  
## <a name="remarks"></a>备注  
 有关详细信息`concurrent_unordered_multiset`类，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_multiset`  
  
## <a name="requirements"></a>要求  
 **标头：** concurrent_unordered_set.h  
  
 **命名空间：** 并发  
  
##  <a name="begin"></a>开始 

 返回指向并发容器中的第一个元素的迭代器。 此方法是并发安全。  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>返回值  
 指向并发容器中的第一个元素的迭代器。  
  
##  <a name="cbegin"></a>cbegin 

 返回指向并发容器中的第一个元素的常量迭代器。 此方法是并发安全。  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 对并发容器中的第一个元素的常量迭代器。  
  
##  <a name="cend"></a>cend 

 返回指向并发容器中的最后一个元素之后的位置的常量迭代器。 此方法是并发安全。  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 对并发容器中的最后一个元素之后的位置的常量迭代器。  
  
##  <a name="clear"></a>清除 

 清除并发容器中的所有元素。 此函数不是并发安全。  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_unordered_multiset 

 构造并发无序多重集。  
  
```
explicit concurrent_unordered_multiset(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multiset(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multiset(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multiset(
    const concurrent_unordered_multiset& _Uset);

concurrent_unordered_multiset(
    const concurrent_unordered_multiset& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_multiset(
    concurrent_unordered_multiset&& _Uset);
```  
  
### <a name="parameters"></a>参数  
 `_Iterator`  
 输入迭代器的类型。  
  
 `_Number_of_buckets`  
 此无序多重集的初始存储桶数。  
  
 `_Hasher`  
 此无序多重集的哈希函数。  
  
 `key_equality`  
 此无序多重集的相等性比较函数。  
  
 `_Allocator`  
 此无序多重集的分配器。  
  
 `first`  
 `last`  
 `_Uset`  
 要从中移动元素的源 `concurrent_unordered_multiset` 对象。  
  
### <a name="remarks"></a>备注  
 所有构造函数都会存储一个分配器对象 `_Allocator` 并初始化无序的多重集。  
  
 第一个构造函数指定一个空的初始多重集，并显式指定要使用的存储桶的数量、哈希函数、相等性比较函数和分配器类型。  
  
 第二个构造函数指定无序多重集的分配器。  
  
 第三个构造函数指定值提供的迭代器范围 [ `_Begin`， `_End`)。  
  
 第四个和第五个构造函数指定并发无序多重集 `_Uset` 的副本。  
  
 最后一个构造函数指定并发无序多重集 `_Uset` 的移动。  
  
##  <a name="count"></a>计数 

 对与指定的键匹配的元素数进行计数。 此函数是安全的并发。  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的键。  
  
### <a name="return-value"></a>返回值  
 密钥容器中的出现次数的次数。  
  
##  <a name="empty"></a>为空 

 测试元素是否存在。 此方法是并发安全。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 `true`如果并发容器为空，`false`否则为。  
  
### <a name="remarks"></a>备注  
 在存在并发插入，并发容器为空可能后立即更改甚至读取返回的值之前调用此函数。  
  
##  <a name="end"></a>结束 

 返回一个迭代器，指向并发容器中的最后一个元素之后的位置。 此方法是并发安全。  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>返回值  
 指向并发容器中的最后一个元素之后的位置的迭代器。  
  
##  <a name="equal_range"></a>equal_range 

 查找与指定的键匹配的范围。 此函数是安全的并发。  
  
```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的键值。  
  
### <a name="return-value"></a>返回值  
 A[对](http://msdn.microsoft.com/en-us/32e72d66-3020-4cb9-92c3-f7a5fa7998ff)其中第一个元素是指向开头的迭代器，第二个元素是指向范围的末尾的迭代器。  
  
### <a name="remarks"></a>备注  
 它有可能并发插入操作会导致其他密钥要插入的开始迭代器之后和之前末尾迭代器。  
  
##  <a name="find"></a>查找 

 查找与指定键匹配的元素。 此函数是安全的并发。  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的键值。  
  
### <a name="return-value"></a>返回值  
 指向的位置的迭代器的匹配提供的密钥的第一个元素或迭代器`end()`如果此类元素不存在。  
  
##  <a name="get_allocator"></a>get_allocator 

 返回此并发容器的存储的分配器对象。 此方法是并发安全。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 此并发容器的的存储的分配器对象。  
  
##  <a name="hash_function"></a>hash_function 

 返回存储的哈希函数对象。  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>返回值  
 存储的哈希函数对象。  
  
##  <a name="insert"></a>插入 

 添加到元素`concurrent_unordered_multiset`对象。  
  
```
iterator insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
iterator insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```  
  
### <a name="parameters"></a>参数  
 `_Iterator`  
 用于插入的迭代器类型。  
  
 `V`  
 插入值的类型。  
  
 `value`  
 要插入的值。  
  
 `_Where`  
 搜索插入点的起始位置。  
  
 `first`  
 要插入的范围的开始处。  
  
 `last`  
 要插入的范围的结尾处。  
  
### <a name="return-value"></a>返回值  
 指向插入位置的迭代器。  
  
### <a name="remarks"></a>备注  
 第一个成员函数将元素 `value` 插入受控序列，然后返回指定插入元素的迭代器。  
  
 第二个成员函数返回插入 ( `value`)，并使用`_Where`作为受控序列中搜索插入点的起始位置。  
  
 第三个成员函数将元素值序列插入范围 [ `first`， `last`)。  
  
 最后两个成员函数与前两个成员函数的行为相同，除了 `value` 用于构造插入值外。  
  
##  <a name="key_eq"></a>key_eq 

 存储的相等性比较函数对象。  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>返回值  
 存储的相等性比较函数对象。  
  
##  <a name="load_factor"></a>load_factor 

 计算并返回容器的当前加载因子。 加载因子是除以存储桶的数量与容器中元素数。  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>返回值  
 容器已加载因子。  
  
##  <a name="max_load_factor"></a>max_load_factor 

 获取或设置容器的最大加载因子。 最大加载因子比之前容器增长其内部表可存在于任何存储桶中，将元素的最大数目。  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>参数  
 `_Newmax`  
  
### <a name="return-value"></a>返回值  
 第一个成员函数将返回存储的最大加载因子。 第二个成员函数不返回一个值，但会引发[out_of_range](../../../standard-library/out-of-range-class.md)异常如果提供的负载因子无效...  
  
##  <a name="max_size"></a>max_size 

 返回并发容器，并确定由分配器的最大大小。 此方法是并发安全。  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 要插入到此并发容器的元素的最大数目。  
  
### <a name="remarks"></a>备注  
 此上限值实际上可能高于容器实际上可以如何保存。  
  
##  <a name="operator_eq"></a>运算符 = 

 将分配的另一个内容`concurrent_unordered_multiset`于此对象。 此方法不是并发安全。  
  
```
concurrent_unordered_multiset& operator= (const concurrent_unordered_multiset& _Uset);

concurrent_unordered_multiset& operator= (concurrent_unordered_multiset&& _Uset);
```  
  
### <a name="parameters"></a>参数  
 `_Uset`  
 源 `concurrent_unordered_multiset` 对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`concurrent_unordered_multiset`对象。  
  
### <a name="remarks"></a>备注  
 在清除并发无序多重集中的所有现有元素后，`operator=` 会将 `_Uset` 的内容复制或移动到并发无序多重集中。  
  
##  <a name="rehash"></a>rehash 

 重新生成哈希表。  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>参数  
 `_Buckets`  
 所需的存储桶数。  
  
### <a name="remarks"></a>备注  
 成员函数将存储桶数更改为至少 `_Buckets` 并根据需要重新生成哈希表。 存储桶的数量必须是 2 的幂。 如果不 2 的幂，它将向上舍入到下一个最大的 2 次幂。  
  
 它将引发[out_of_range](../../../standard-library/out-of-range-class.md)异常如果是无效的存储桶的数量 （0 或大于存储桶的最大数量）。  
  
##  <a name="size"></a>大小 

 返回此并发容器中的元素数量。 此方法是并发安全。  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 容器中的项数。  
  
### <a name="remarks"></a>备注  
 在存在并发插入时，并发容器中的元素数量可能会在调用此函数后立即更改，甚至会在读取返回值之前。  
  
##  <a name="swap"></a>交换 

 交换两个内容`concurrent_unordered_multiset`对象。 此方法不是并发安全。  
  
```
void swap(concurrent_unordered_multiset& _Uset);
```  
  
### <a name="parameters"></a>参数  
 `_Uset`  
 要交换的 `concurrent_unordered_multiset` 对象。  
  
##  <a name="unsafe_begin"></a>unsafe_begin 

 返回特定的存储桶此容器中的第一个元素的迭代器。  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶索引中。  
  
### <a name="return-value"></a>返回值  
 迭代器指向存储桶的开头。  
  
##  <a name="unsafe_bucket"></a>unsafe_bucket 

 返回特定键映射到此容器中的存储桶索引。  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的元素键。  
  
### <a name="return-value"></a>返回值  
 此容器中的密钥存储桶索引。  
  
##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count 

 返回此容器中的存储桶的当前数量。  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>返回值  
 此容器中的存储桶的当前数量。  
  
##  <a name="unsafe_bucket_size"></a>unsafe_bucket_size 

 在此容器的特定的存储桶中返回的项数。  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶，以搜索。  
  
### <a name="return-value"></a>返回值  
 此容器中的存储桶的当前数量。  
  
##  <a name="unsafe_cbegin"></a>unsafe_cbegin 

 返回特定的存储桶此容器中的第一个元素的迭代器。  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶索引中。  
  
### <a name="return-value"></a>返回值  
 迭代器指向存储桶的开头。  
  
##  <a name="unsafe_cend"></a>unsafe_cend 

 返回特定的存储桶中最后一个元素之后的位置的迭代器。  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶索引中。  
  
### <a name="return-value"></a>返回值  
 迭代器指向存储桶的开头。  
  
##  <a name="unsafe_end"></a>unsafe_end 

 返回特定的存储桶此容器中的最后一个元素的迭代器。  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶索引中。  
  
### <a name="return-value"></a>返回值  
 一个指向存储桶末尾的迭代器。  
  
##  <a name="unsafe_erase"></a>unsafe_erase 

 从其中移除元素`concurrent_unordered_multiset`指定位置处。 此方法不是并发安全。  
  
```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);

size_type unsafe_erase(
    const key_type& KVal);
```  
  
### <a name="parameters"></a>参数  
 `_Where`  
 要从擦除的迭代器位置。  
  
 `first`  
 `last`  
 `KVal`  
 要擦除的键值。  
  
### <a name="return-value"></a>返回值  
 前两个成员函数返回一个迭代器，它指定已移除，任何元素之外保留的第一个元素或[结束](#end)（); 如果此类元素不存在。 第三个成员函数返回它中移除的元素数目。  
  
### <a name="remarks"></a>备注  
 第一个成员函数中移除的元素指向`_Where`。 第二个成员函数范围中移除的元素 [ `_Begin`， `_End`)。  
  
 第三个成员函数在由分隔的范围中移除的元素[equal_range](#equal_range)(KVal)。  
  
##  <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count 

 返回此容器中的存储桶的最大数量。  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>返回值  
 此容器中的存储桶的最大数量。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)



