---
title: concurrent_unordered_set 类
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_set class
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
ms.openlocfilehash: 43bce15f001e0daee817d9dae345b5d0858f2baa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286200"
---
# <a name="concurrentunorderedset-class"></a>concurrent_unordered_set 类

`concurrent_unordered_set`类是控制元素的类型 K.变长序列的并发安全容器序列表示方式支持并发安全追加、 元素访问、 迭代器访问和迭代器遍历操作。

## <a name="syntax"></a>语法

```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_set : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    false>>;
```

#### <a name="parameters"></a>参数

*K*<br/>
密钥类型。

*_Hasher*<br/>
哈希函数对象类型。 此参数为可选参数，默认值为 `std::hash<K>`。

*key_equality*<br/>
相等比较函数对象类型。 此参数为可选参数，默认值为 `std::equal_to<K>`。

*_Allocator_type*<br/>
表示存储的分配器对象封装有关分配和解除分配的内存用于并发无序集的详细信息的类型。 此参数为可选参数，默认值为 `std::allocator<K>`。

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
|[concurrent_unordered_set](#ctor)|已重载。 构造并发无序的集。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[hash_function](#hash_function)|返回存储的哈希函数对象。|
|[insert](#insert)|已重载。 将元素添加到`concurrent_unordered_set`对象。|
|[key_eq](#key_eq)|返回存储的相等比较函数对象。|
|[swap](#swap)|交换两个内容`concurrent_unordered_set`对象。 此方法不是并发安全的。|
|[unsafe_erase](#unsafe_erase)|已重载。 从其中移除元素`concurrent_unordered_set`指定位置处。 此方法不是并发安全的。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator=](#operator_eq)|已重载。 另一种内容分配`concurrent_unordered_set`到此对象。 此方法不是并发安全的。|

## <a name="remarks"></a>备注

有关详细信息`concurrent_unordered_set`类，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_set`

## <a name="requirements"></a>要求

**标头：** concurrent_unordered_set.h

**命名空间：** 并发

##  <a name="begin"></a> begin

返回一个迭代器，指向并发容器中的第一个元素。 此方法是并发安全。

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>返回值

指向并发容器中的第一个元素的迭代器。

##  <a name="cbegin"></a> cbegin

返回指向并发容器中的第一个元素的常量迭代器。 此方法是并发安全。

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

并发容器中的第一个元素到一个常量迭代器。

##  <a name="cend"></a> cend

返回指向并发容器中的最后一个元素之后的位置的常量迭代器。 此方法是并发安全。

```
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

指向并发容器中的最后一个元素之后的位置的常量迭代器。

##  <a name="clear"></a> 清除

清除并发容器中的所有元素。 此函数不是并发安全。

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_set

构造并发无序的集。

```
explicit concurrent_unordered_set(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_set(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset);

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_set(
    concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>参数

*_Iterator*<br/>
输入迭代器的类型。

*_Number_of_buckets*<br/>
此无序集的初始存储桶数。

*_Hasher*<br/>
此无序集的哈希函数。

*key_equality*<br/>
此无序集的相等性比较函数。

*_Allocator*<br/>
此无序集的分配器。

*first*<br/>
*last*<br/>
*_Uset*<br/>
要从中复制或移动元素的源 `concurrent_unordered_set` 对象。

### <a name="remarks"></a>备注

所有构造函数都会存储一个分配器对象 `_Allocator` 并初始化无序集。

第一个构造函数指定一个空的初始集，并显式指定要使用的存储桶的数量、哈希函数、相等性比较函数和分配器类型。

第二个构造函数指定无序集的分配器。

第三个构造函数指定值提供的迭代器范围 [ `_Begin`， `_End`)。

第四个和第五个构造函数指定并发无序集 `_Uset` 的副本。

最后一个构造函数指定并发无序集 `_Uset`的移动。

##  <a name="count"></a> count

计算指定的键相匹配的元素的数目。 此函数是并发安全。

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>参数

*KVal*<br/>
要搜索的键。

### <a name="return-value"></a>返回值

密钥容器中的出现次数的次数。

##  <a name="empty"></a> empty

测试元素是否存在。 此方法是并发安全。

```
bool empty() const;
```

### <a name="return-value"></a>返回值

**true**是否为空，并发容器**false**否则为。

### <a name="remarks"></a>备注

在存在并发插入，并发容器为空可能后立即更改返回值甚至会在读取之前调用此函数。

##  <a name="end"></a> 结束

返回一个迭代器，指向并发容器中的最后一个元素之后的位置。 此方法是并发安全。

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

指向并发容器中的最后一个元素之后的位置的迭代器。

##  <a name="equal_range"></a> equal_range

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

*KVal*<br/>
要搜索的密钥值。

### <a name="return-value"></a>返回值

一个[对](../../../standard-library/pair-structure.md)其中第一个元素是开头的迭代器，第二个元素是指向范围末尾的迭代器。

### <a name="remarks"></a>备注

很可能并发插入操作会导致其他密钥，从而在插入之后开始迭代器和之前末尾迭代器。

##  <a name="find"></a> find

查找与指定键匹配的元素。 此函数是并发安全。

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>参数

*KVal*<br/>
要搜索的密钥值。

### <a name="return-value"></a>返回值

迭代器指向匹配提供的键的第一个元素位置或迭代器`end()`如果此类元素不存在。

##  <a name="get_allocator"></a> get_allocator

返回此并发容器的存储分配器对象。 此方法是并发安全。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

此并发容器存储分配器对象。

##  <a name="hash_function"></a> hash_function

返回存储的哈希函数对象。

```
hasher hash_function() const;
```

### <a name="return-value"></a>返回值

存储的哈希函数对象。

##  <a name="insert"></a> insert

将元素添加到`concurrent_unordered_set`对象。

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

*_Iterator*<br/>
用于插入的迭代器类型。

*V*<br/>
插入到集中的值的类型。

*值*<br/>
要插入的值。

*_Where*<br/>
搜索插入点的起始位置。

*first*<br/>
要插入的范围的开始处。

*last*<br/>
要插入的范围的结尾处。

### <a name="return-value"></a>返回值

一个对，包含一个迭代器，以及一个布尔值。 请参阅更多详细信息备注部分。

### <a name="remarks"></a>备注

第一个成员函数确定其键具有相同的排序的序列中是否存在的元素 X `value`。 如果不是，它会创建这样的元素 X 并初始化其与`value`。 然后，该函数确定迭代器`where`指定 X。如果完成插入操作发生，该函数将返回`std::pair(where, true)`。 否则，它将返回 `std::pair(where, false)`。

第二个成员函数返回插入 ( `value`)，并使用`_Where`作为受控序列中搜索插入点的开始位置。

第三个成员函数将元素值序列插入范围 [ `first`， `last`)。

最后两个成员函数与前两个成员函数的行为相同，除了 `value` 用于构造插入值外。

##  <a name="key_eq"></a> key_eq

返回存储的相等比较函数对象。

```
key_equal key_eq() const;
```

### <a name="return-value"></a>返回值

存储的相等比较函数对象。

##  <a name="load_factor"></a> load_factor

计算并返回当前的加载因子，容器。 加载因子是除以存储桶的数量的容器中的元素数。

```
float load_factor() const;
```

### <a name="return-value"></a>返回值

容器加载因子。

##  <a name="max_load_factor"></a> max_load_factor

获取或设置容器的最大加载因子。 最大加载因子是元素的最大数目，而在任何存储桶中无法，容器将增加其内部表。

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>参数

`_Newmax`

### <a name="return-value"></a>返回值

第一个成员函数将返回存储的最大加载因子。 第二个成员函数不会返回一个值，但会引发[out_of_range](../../../standard-library/out-of-range-class.md)异常如果提供的负载因子无效...

##  <a name="max_size"></a> max_size

返回由分配器的并发容器的最大大小。 此方法是并发安全。

```
size_type max_size() const;
```

### <a name="return-value"></a>返回值

最大可以插入到此并发容器的元素数。

### <a name="remarks"></a>备注

实际上，此上限值可能高于容器实际上可以如何保存。

##  <a name="operator_eq"></a> 运算符 =

另一种内容分配`concurrent_unordered_set`到此对象。 此方法不是并发安全的。

```
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>参数

*_Uset*<br/>
源 `concurrent_unordered_set` 对象。

### <a name="return-value"></a>返回值

对此引用`concurrent_unordered_set`对象。

### <a name="remarks"></a>备注

在清除并发无序集中的所有现有元素之后，`operator=` 会将 `_Uset` 的内容复制或移动到此并发无序集。

##  <a name="rehash"></a> rehash

重新生成哈希表。

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>参数

*_Buckets*<br/>
所需的存储桶数。

### <a name="remarks"></a>备注

成员函数将存储桶数更改为至少 `_Buckets` 并根据需要重新生成哈希表。 存储桶的数量必须是 2 的幂。 如果不 2 的幂，它将舍入到下一步最大的 2 次幂。

它将引发[out_of_range](../../../standard-library/out-of-range-class.md)异常是否无效的存储桶数 （0 或大于最大存储桶数）。

##  <a name="size"></a> 大小

返回此并发容器中的元素数量。 此方法是并发安全。

```
size_type size() const;
```

### <a name="return-value"></a>返回值

容器中的项数。

### <a name="remarks"></a>备注

在存在并发插入时，并发容器中的元素数量可能会在调用此函数后立即更改，甚至会在读取返回值之前。

##  <a name="swap"></a> swap

交换两个内容`concurrent_unordered_set`对象。 此方法不是并发安全的。

```
void swap(concurrent_unordered_set& _Uset);
```

### <a name="parameters"></a>参数

*_Uset*<br/>
要交换的 `concurrent_unordered_set` 对象。

##  <a name="unsafe_begin"></a> unsafe_begin

在此容器中为特定的存储桶中的第一个元素返回一个迭代器。

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
存储桶的索引。

### <a name="return-value"></a>返回值

迭代器指向的存储桶开头。

##  <a name="unsafe_bucket"></a> unsafe_bucket

返回特定键映射到此容器中的存储桶索引。

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>参数

*KVal*<br/>
要搜索的元素键。

### <a name="return-value"></a>返回值

此容器中的密钥的的存储桶索引。

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

返回此容器中的存储桶的当前数量。

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>返回值

当前此容器中的存储桶数。

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

在此容器的特定的存储桶中返回的项数。

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
若要搜索的存储桶。

### <a name="return-value"></a>返回值

当前此容器中的存储桶数。

##  <a name="unsafe_cbegin"></a> unsafe_cbegin

在此容器中为特定的存储桶中的第一个元素返回一个迭代器。

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
存储桶的索引。

### <a name="return-value"></a>返回值

迭代器指向的存储桶开头。

##  <a name="unsafe_cend"></a> unsafe_cend

返回一个迭代器，之后在特定的存储桶中的最后一个元素的位置。

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
存储桶的索引。

### <a name="return-value"></a>返回值

迭代器指向的存储桶开头。

##  <a name="unsafe_end"></a> unsafe_end

返回到此容器中为特定的存储桶中的最后一个元素的迭代器。

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
存储桶的索引。

### <a name="return-value"></a>返回值

迭代器指向的存储桶末尾。

##  <a name="unsafe_erase"></a> unsafe_erase

从其中移除元素`concurrent_unordered_set`指定位置处。 此方法不是并发安全的。

```
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>参数

*_Where*<br/>
要从删除的迭代器位置。

*KVal*<br/>
要清除的键值。

*first*<br/>
*last*<br/>
迭代器。

### <a name="return-value"></a>返回值

前两个成员函数返回一个迭代器，指定已删除的任何元素之外保留的第一个元素或[最终](#end)（); 如果此类元素不存在。 第三个成员函数返回它会删除的元素数。

### <a name="remarks"></a>备注

第一个成员函数删除由指向的元素`_Where`。 第二个成员函数的范围内移除的元素 [ `_Begin`， `_End`)。

第三个成员函数由分隔的范围内移除的元素[equal_range](#equal_range)(KVal)。

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

在此容器中返回的最大存储桶数。

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>返回值

此容器中的存储桶数目上限。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)
