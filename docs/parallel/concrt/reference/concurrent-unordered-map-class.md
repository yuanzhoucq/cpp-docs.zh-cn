---
title: "concurrent_unordered_map 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_unordered_map/concurrency::concurrent_unordered_map
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 19244e5527207f852256e646abd18ad298fb28cd
ms.openlocfilehash: ec35d0e410efcc7861df0ab39ad561de04518d91
ms.lasthandoff: 02/24/2017

---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map 类
`concurrent_unordered_map` 类是控制 `std::pair<const K, _Element_type>` 类型元素的长短不一序列的并发安全容器。 序列以支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作的方式表示。  
  
## <a name="syntax"></a>语法  
  
```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
 typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
 details::_Hash_compare<K,
    _Hasher,
 key_equality>,
    _Allocator_type,
 false>>;
```  
  
#### <a name="parameters"></a>参数  
 `K`  
 密钥类型。  
  
 `_Element_type`  
 映射类型。  
  
 `_Hasher`  
 哈希函数对象类型。 此参数为可选参数，默认值为 `std::hash<``K``>`。  
  
 `key_equality`  
 相等比较函数对象类型。 此参数为可选参数，默认值为 `std::equal_to<``K``>`。  
  
 `_Allocator_type`  
 表示存储的分配器对象封装有关分配和解除分配的内存用于并发无序映射的详细信息的类型。 此参数为可选，默认值是`std::allocator<std::pair<``K`， `_Element_type``>>`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
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
|`mapped_type`|与每个键关联的映射值的类型。|  
|`pointer`|指向元素的指针的类型。|  
|`reference`|元素的引用的类型。|  
|`size_type`|两个元素间的无符号距离的类型。|  
|`value_type`|元素的类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[concurrent_unordered_map 构造函数](#ctor)|已重载。 构造并发无序的映射。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[at 方法](#at)|已重载。 查找中的元素`concurrent_unordered_map`与指定的密钥值... 此方法是并发安全的。|  
|[hash_function 方法](#hash_function)|获取存储的哈希函数对象。|  
|[insert 方法](#insert)|已重载。 添加到元素`concurrent_unordered_map`对象。|  
|[key_eq 方法](#key_eq)|获取存储的相等性比较函数对象。|  
|[swap 方法](#swap)|交换两个内容`concurrent_unordered_map`对象。 此方法不是并发安全的。|  
|[unsafe_erase 方法](#unsafe_erase)|已重载。 从其中移除元素`concurrent_unordered_map`指定位置处。 此方法不是并发安全的。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[operator [] 运算符](#operator_at)|已重载。 查找或插入具有指定键的元素。 此方法是并发安全的。|  
|[运算符 = 运算符](#operator_eq)|已重载。 另一种内容分配`concurrent_unordered_map`对象传递给它。 此方法不是并发安全的。|  
  
## <a name="remarks"></a>备注  
 有关详细信息`concurrent_unordered_map`类，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>要求  
 **标头︰** concurrent_unordered_map.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameata-at"></a><a name="at"></a>在 

 查找中的元素`concurrent_unordered_map`与指定的密钥值... 此方法是并发安全的。  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要查找的键值。  
  
### <a name="return-value"></a>返回值  
 对找到的元素数据值的引用。  
  
### <a name="remarks"></a>备注  
 如果未找到参数键值，函数将引发类 `out_of_range` 的对象。  
  
##  <a name="a-namebegina-begin"></a><a name="begin"></a>开始 

 返回指向并发容器中的第一个元素的迭代器。 此方法是并发安全。  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>返回值  
 指向并发容器中的第一个元素的迭代器。  
  
##  <a name="a-namecbegina-cbegin"></a><a name="cbegin"></a>cbegin 

 返回指向并发容器中的第一个元素的常量迭代器。 此方法是并发安全。  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 并发容器中的第一个元素的常量迭代器。  
  
##  <a name="a-namecenda-cend"></a><a name="cend"></a>cend 

 返回指向并发容器中的最后一个元素之后的位置的常量迭代器。 此方法是并发安全。  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 一个指向并发容器中的最后一个元素之后的位置的常量迭代器。  
  
##  <a name="a-namecleara-clear"></a><a name="clear"></a>清除 

 清除并发容器中的所有元素。 此函数不是并发安全。  
  
```
void clear();
```  
  
##  <a name="a-namectora-concurrentunorderedmap"></a><a name="ctor"></a>concurrent_unordered_map 

 构造并发无序的映射。  
  
```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>参数  
 `_Iterator`  
 输入迭代器的类型。  
  
 `_Number_of_buckets`  
 此无序映射的初始存储桶数。  
  
 `_Hasher`  
 此无序映射的哈希函数。  
  
 `key_equality`  
 此无序映射的相等性比较函数。  
  
 `_Allocator`  
 此无序映射的分配器。  
  
 `_Begin`  
 要复制的范围元素中的第一个元素的位置。  
  
 `_End`  
 要复制的元素范围以外的第一个元素的位置。  
  
 `_Umap`  
 要从中复制或移动元素的源 `concurrent_unordered_map` 对象。  
  
### <a name="remarks"></a>备注  
 所有构造函数都会存储一个分配器对象 `_Allocator` 并初始化无序映射。  
  
 第一个构造函数指定一个空的初始映射，并显式指定要使用的存储桶的数量、哈希函数、相等性比较函数和分配器类型。  
  
 第二个构造函数指定无序映射的分配器。  
  
 第三个构造函数指定由迭代器范围提供的值 [ `_Begin`， `_End`)。  
  
 第四个和第五个构造函数指定并发无序映射 `_Umap` 的副本。  
  
 最后一个构造函数指定并发无序映射 `_Umap`的移动。  
  
##  <a name="a-namecounta-count"></a><a name="count"></a>计数 

 对与指定的键匹配的元素数进行计数。 此函数是并发安全。  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的键。  
  
### <a name="return-value"></a>返回值  
 密钥容器中出现的次数的次数。  
  
##  <a name="a-nameemptya-empty"></a><a name="empty"></a>为空 

 测试元素是否存在。 此方法是并发安全。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 `true`如果并发容器为空，`false`否则为。  
  
### <a name="remarks"></a>备注  
 在存在并发插入时，并发容器为空可能更改在甚至读取返回的值之前调用此函数后立即。  
  
##  <a name="a-nameenda-end"></a><a name="end"></a>结束 

 返回指向并发容器中的最后一个元素之后的位置的迭代器。 此方法是并发安全。  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>返回值  
 指向并发容器中的最后一个元素之后的位置的迭代器。  
  
##  <a name="a-nameequalrangea-equalrange"></a><a name="equal_range"></a>equal_range 

 查找与指定的键匹配的范围。 此函数是并发安全。  
  
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
 要搜索的密钥值。  
  
### <a name="return-value"></a>返回值  
 一个[对](http://msdn.microsoft.com/en-us/c5a37023-d939-4eb2-ae24-ce8e0cd4505d)其中第一个元素是指向开头的迭代器，第二个元素是指向范围的末尾的迭代器。  
  
### <a name="remarks"></a>备注  
 很可能会导致其他密钥，从而在开始迭代器之后和结束迭代器之前插入并发插入操作。  
  
##  <a name="a-namefinda-find"></a><a name="find"></a>查找 

 查找与指定键匹配的元素。 此函数是并发安全。  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的密钥值。  
  
### <a name="return-value"></a>返回值  
 指向的位置的迭代器匹配中, 提供的密钥的第一个元素或迭代器`end()`如果此类元素不存在。  
  
##  <a name="a-namegetallocatora-getallocator"></a><a name="get_allocator"></a>get_allocator 

 返回此并发容器的存储的分配器对象。 此方法是并发安全。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 此并发容器的的存储的分配器对象。  
  
##  <a name="a-namehashfunctiona-hashfunction"></a><a name="hash_function"></a>hash_function 

 获取存储的哈希函数对象。  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>返回值  
 存储的哈希函数对象。  
  
##  <a name="a-nameinserta-insert"></a><a name="insert"></a>插入 

 添加到元素`concurrent_unordered_map`对象。  
  
```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
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
 插入到映射的值的类型。  
  
 `value`  
 要插入的值。  
  
 `_Where`  
 搜索插入点的起始位置。  
  
 `first`  
 要插入的范围的开始处。  
  
 `last`  
 要插入的范围的结尾处。  
  
### <a name="return-value"></a>返回值  
 对，包含一个迭代器和一个布尔值。 请参阅备注部分以了解更多信息。  
  
### <a name="remarks"></a>备注  
 第一个成员函数确定其键具有等效顺序的序列中是否存在某个元素 X `value`。 如果不是，它将创建此类的元素 X 并初始化其与`value`。 然后，该函数会确定迭代器`where`指定的 X。如果插入发生，则该函数将返回`std::pair(where, true)`。 否则，它将返回 `std::pair(where, false)`。  
  
 第二个成员函数将返回插入 ( `value`)，并使用`_Where`作为受控序列中搜索插入点的开始位置。  
  
 第三个成员函数插入范围的元素值序列 [ `first`， `last`)。  
  
 最后两个成员函数与前两个成员函数的行为相同，除了 `value` 用于构造插入值外。  
  
##  <a name="a-namekeyeqa-keyeq"></a><a name="key_eq"></a>key_eq 

 获取存储的相等性比较函数对象。  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>返回值  
 存储的相等性比较函数对象。  
  
##  <a name="a-nameloadfactora-loadfactor"></a><a name="load_factor"></a>load_factor 

 计算并返回容器的当前加载因子。 加载因子是除以存储桶的数量的容器中的元素数。  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>返回值  
 容器的加载因子。  
  
##  <a name="a-namemaxloadfactora-maxloadfactor"></a><a name="max_load_factor"></a>max_load_factor 

 获取或设置容器的最大加载因子。 不是之前容器增大其内部表可存在于任何存储桶中，最大加载因子将是最大数量的元素。  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>参数  
 `_Newmax`  
  
### <a name="return-value"></a>返回值  
 第一个成员函数将返回存储的最大加载因子。 第二个成员函数不返回一个值，但会引发[out_of_range](../../../standard-library/out-of-range-class.md)异常提供的加载因子是否无效...  
  
##  <a name="a-namemaxsizea-maxsize"></a><a name="max_size"></a>max_size 

 返回并发容器，由分配器的最大大小。 此方法是并发安全。  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 可以插入到此并发容器的元素的最大数目。  
  
### <a name="remarks"></a>备注  
 此上限值实际上可能高于容器实际上可以如何保存。  
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

 查找或插入具有指定键的元素。 此方法是并发安全的。  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要  
  
 查找或插入的键值。  
  
### <a name="return-value"></a>返回值  
 对找到或插入的元素数据值的引用。  
  
### <a name="remarks"></a>备注  
 如果未找到自变量键值，则它将与数据类型的默认值一起插入。  
  
 `operator[]` 可用于将元素插入使用 `m`（其中 `m[key] = DataValue;` 是具有键值 `DataValue` 的元素 `mapped_type` 的值）的映射 `key`。  
  
 使用 `operator[]` 插入元素时，返回的引用不指示插入是更改预先存在的元素还是创建一个新元素。 成员函数`find`和[插入](#insert)可以用于确定具有指定键的元素是否已插入前存在。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 另一种内容分配`concurrent_unordered_map`对象传递给它。 此方法不是并发安全的。  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>参数  
 `_Umap`  
 源 `concurrent_unordered_map` 对象。  
  
### <a name="return-value"></a>返回值  
 参考这`concurrent_unordered_map`对象。  
  
### <a name="remarks"></a>备注  
 在清除并发向量中的所有现有元素后，`operator=` 会将 `_Umap` 的内容复制或移动到此并发向量中。  
  
##  <a name="a-namerehasha-rehash"></a><a name="rehash"></a>rehash 

 重新生成哈希表。  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>参数  
 `_Buckets`  
 所需的存储桶数。  
  
### <a name="remarks"></a>备注  
 成员函数将存储桶数更改为至少 `_Buckets` 并根据需要重新生成哈希表。 存储桶的数目必须是 2 的幂。 如果没有 2 的幂，它将舍入到下一个最大的 2 次幂。  
  
 它将引发[out_of_range](../../../standard-library/out-of-range-class.md)异常，如果是无效的存储桶的数量 （0 或大于存储桶的最大数量）。  
  
##  <a name="a-namesizea-size"></a><a name="size"></a>大小 

 返回此并发容器中的元素数量。 此方法是并发安全。  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 容器中的项数。  
  
### <a name="remarks"></a>备注  
 在存在并发插入时，并发容器中的元素数量可能会在调用此函数后立即更改，甚至会在读取返回值之前。  
  
##  <a name="a-nameswapa-swap"></a><a name="swap"></a>交换 

 交换两个内容`concurrent_unordered_map`对象。 此方法不是并发安全的。  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>参数  
 `_Umap`  
 要交换的 `concurrent_unordered_map` 对象。  
  
##  <a name="a-nameunsafebegina-unsafebegin"></a><a name="unsafe_begin"></a>unsafe_begin 

 在此容器中为特定的存储桶中的第一个元素返回迭代器。  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶的索引。  
  
### <a name="return-value"></a>返回值  
 指向开头的存储桶迭代器。  
  
##  <a name="a-nameunsafebucketa-unsafebucket"></a><a name="unsafe_bucket"></a>unsafe_bucket 

 返回特定键映射到此容器中的存储桶索引。  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>参数  
 `KVal`  
 要搜索的元素键。  
  
### <a name="return-value"></a>返回值  
 此容器中的密钥的的存储桶索引。  
  
##  <a name="a-nameunsafebucketcounta-unsafebucketcount"></a><a name="unsafe_bucket_count"></a>unsafe_bucket_count 

 返回此容器中的存储桶的当前数量。  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>返回值  
 此容器中的存储桶的当前数量。  
  
##  <a name="a-nameunsafebucketsizea-unsafebucketsize"></a><a name="unsafe_bucket_size"></a>unsafe_bucket_size 

 在此容器的特定的存储桶中返回的项数。  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 搜索存储桶。  
  
### <a name="return-value"></a>返回值  
 此容器中的存储桶的当前数量。  
  
##  <a name="a-nameunsafecbegina-unsafecbegin"></a><a name="unsafe_cbegin"></a>unsafe_cbegin 

 在此容器中为特定的存储桶中的第一个元素返回迭代器。  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶的索引。  
  
### <a name="return-value"></a>返回值  
 指向开头的存储桶迭代器。  
  
##  <a name="a-nameunsafecenda-unsafecend"></a><a name="unsafe_cend"></a>unsafe_cend 

 返回一个迭代之后的位置特定的存储桶中的最后一个元素。  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶的索引。  
  
### <a name="return-value"></a>返回值  
 指向开头的存储桶迭代器。  
  
##  <a name="a-nameunsafeenda-unsafeend"></a><a name="unsafe_end"></a>unsafe_end 

 返回到此容器中为特定的存储桶中的最后一个元素的迭代器。  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>参数  
 `_Bucket`  
 存储桶的索引。  
  
### <a name="return-value"></a>返回值  
 迭代器指向的存储段的末尾。  
  
##  <a name="a-nameunsafeerasea-unsafeerase"></a><a name="unsafe_erase"></a>unsafe_erase 

 从其中移除元素`concurrent_unordered_map`指定位置处。 此方法不是并发安全的。  
  
```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```  
  
### <a name="parameters"></a>参数  
 `_Where`  
 要从删除的迭代器位置。  
  
 `_Begin`  
 要消除的元素范围中第一个元素的位置。  
  
 `_End`  
 要消除的元素范围之外的第一个元素的位置。  
  
 `KVal`  
 要删除的密钥值。  
  
### <a name="return-value"></a>返回值  
 前两个成员函数返回一个迭代器，指定已移除，任何元素之外保留的第一个元素或`concurrent_unordered_map::end`（); 如果不存在此元素。 第三个成员函数返回它会移除的元素的数目。  
  
### <a name="remarks"></a>备注  
 第一个成员函数将移除 `_Where` 所指向的受控序列的元素。 第二个成员函数范围内移除的元素 [ `_Begin`， `_End`)。  
  
 第三个成员函数中由分隔的范围内移除的元素`concurrent_unordered_map::equal_range`(KVal)。  
  
##  <a name="a-nameunsafemaxbucketcounta-unsafemaxbucketcount"></a><a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count 

 返回此容器中的存储桶的最大数量。  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>返回值  
 此容器中的存储桶的最大数量。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)




