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
ms.openlocfilehash: 9dc5b37730742e7deec20b12232de672679e956f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75297474"
---
# <a name="concurrent_unordered_set-class"></a>concurrent_unordered_set 类

`concurrent_unordered_set` 类是一种并发安全容器，用于控制 K 类型的不同长度的元素序列。序列以启用并发安全追加、元素访问、迭代器访问和迭代器遍历操作的方式表示。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。

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
键类型。

*_Hasher*<br/>
哈希函数对象类型。 此参数为可选参数，默认值为 `std::hash<K>`。

*key_equality*<br/>
相等比较函数对象类型。 此参数为可选参数，默认值为 `std::equal_to<K>`。

*_Allocator_type*<br/>
表示存储分配器对象的类型，该对象封装有关并发无序集的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `std::allocator<K>`。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|Name|描述|
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

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[concurrent_unordered_set](#ctor)|已重载。 构造并发的无序集。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[hash_function](#hash_function)|返回存储的哈希函数对象。|
|[insert](#insert)|已重载。 向 `concurrent_unordered_set` 对象添加元素。|
|[key_eq](#key_eq)|返回存储的相等比较函数对象。|
|[swap](#swap)|交换两个 `concurrent_unordered_set` 对象的内容。 此方法不是并发安全方法。|
|[unsafe_erase](#unsafe_erase)|已重载。 从 `concurrent_unordered_set` 中移除指定位置处的元素。 此方法不是并发安全方法。|

### <a name="public-operators"></a>公用運算子

|Name|描述|
|----------|-----------------|
|[operator=](#operator_eq)|已重载。 将另一个 `concurrent_unordered_set` 对象的内容分配给此对象。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关 `concurrent_unordered_set` 类的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_set`

## <a name="requirements"></a>需求

**标头：** concurrent_unordered_set。h

**命名空间：** 并发

##  <a name="begin"></a>准备

返回一个迭代器，该迭代器指向并发容器中的第一个元素。 此方法是并发安全方法。

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>返回值

指向并发容器中第一个元素的迭代器。

##  <a name="cbegin"></a> cbegin

返回一个常量迭代器，该迭代器指向并发容器中的第一个元素。 此方法是并发安全方法。

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

并发容器中第一个元素的常量迭代器。

##  <a name="cend"></a>cend

返回一个常量迭代器，该迭代器指向并发容器中最后一个元素之后的位置。 此方法是并发安全方法。

```
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

指向并发容器中最后一个元素之后的位置的常量迭代器。

##  <a name="clear"></a>清除

清除并发容器中的所有元素。 此函数不是并发安全函数。

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_set

构造并发的无序集。

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

第三个构造函数指定迭代器范围 [`_Begin`，`_End`）提供的值。

第四个和第五个构造函数指定并发无序集 `_Uset` 的副本。

最后一个构造函数指定并发无序集 `_Uset`的移动。

##  <a name="count"></a>计

计算与指定键匹配的元素的数目。 此函数是并发安全函数。

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>参数

*KVal*<br/>
要搜索的键。

### <a name="return-value"></a>返回值

键在容器中出现的次数。

##  <a name="empty"></a>空白处

测试元素是否存在。 此方法是并发安全方法。

```
bool empty() const;
```

### <a name="return-value"></a>返回值

如果并发容器为空，**则为 true** ; 否则为**false** 。

### <a name="remarks"></a>备注

在出现并发插入时，无论并发容器是否为空，在调用此函数后，甚至在读取返回值之前都可能会立即更改。

##  <a name="end"></a>端面

返回一个迭代器，该迭代器指向并发容器中最后一个元素之后的位置。 此方法是并发安全方法。

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

指向并发容器中最后一个元素之后的位置的迭代器。

##  <a name="equal_range"></a>equal_range

查找与指定键匹配的范围。 此函数是并发安全函数。

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
要搜索的键值。

### <a name="return-value"></a>返回值

一[对](../../../standard-library/pair-structure.md)，其中第一个元素是开始迭代器，第二个元素是指向范围末尾的迭代器。

### <a name="remarks"></a>备注

并发插入可能会导致在开始迭代器之后以及结束迭代器之前插入额外的键。

##  <a name="find"></a>查找

查找与指定键匹配的元素。 此函数是并发安全函数。

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>参数

*KVal*<br/>
要搜索的键值。

### <a name="return-value"></a>返回值

一个迭代器，该迭代器指向与所提供的键相匹配的第一个元素的位置，如果此类元素不存在，则为迭代器 `end()`。

##  <a name="get_allocator"></a> get_allocator

返回此并发容器的存储分配器对象。 此方法是并发安全方法。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

此并发容器的存储分配器对象。

##  <a name="hash_function"></a>hash_function

返回存储的哈希函数对象。

```
hasher hash_function() const;
```

### <a name="return-value"></a>返回值

存储的哈希函数对象。

##  <a name="insert"></a>&

向 `concurrent_unordered_set` 对象添加元素。

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

一个包含迭代器和一个布尔值的对。 有关更多详细信息，请参阅“备注”部分。

### <a name="remarks"></a>备注

第一个成员函数确定元素 X 是否存在于其键具有与 `value`的等效顺序相同的序列中。 否则，它将创建此类元素 X 并使用 `value`对其进行初始化。 然后，该函数确定指定 X 的迭代器 `where`。如果发生插入，函数将返回 `std::pair(where, true)`。 否则，它将返回 `std::pair(where, false)`。

第二个成员函数返回 insert （`value`），使用 `_Where` 作为受控序列内的开始位置来搜索插入点。

第三个成员函数将从 [`first`，`last`）范围中插入元素值序列。

最后两个成员函数与前两个成员函数的行为相同，除了 `value` 用于构造插入值外。

##  <a name="key_eq"></a> key_eq

返回存储的相等比较函数对象。

```
key_equal key_eq() const;
```

### <a name="return-value"></a>返回值

存储的相等比较函数对象。

##  <a name="load_factor"></a>load_factor

计算并返回容器的当前加载因子。 加载因子是容器中的元素数除以 bucket 数。

```
float load_factor() const;
```

### <a name="return-value"></a>返回值

容器的加载因子。

##  <a name="max_load_factor"></a>max_load_factor

获取或设置容器的最大加载因子。 最大加载因子是在容器增长其内部表之前，在任何存储桶中都可以有的元素的最大数目。

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>参数

`_Newmax`

### <a name="return-value"></a>返回值

第一个成员函数将返回存储的最大加载因子。 第二个成员函数不返回值，但如果提供的加载因子无效，则会引发[out_of_range](../../../standard-library/out-of-range-class.md)异常。

##  <a name="max_size"></a>max_size

返回由分配器确定的并发容器的最大大小。 此方法是并发安全方法。

```
size_type max_size() const;
```

### <a name="return-value"></a>返回值

可插入此并发容器中的元素的最大数目。

### <a name="remarks"></a>备注

此上限值实际上可能比容器实际保存的值高。

##  <a name="operator_eq"></a>operator =

将另一个 `concurrent_unordered_set` 对象的内容分配给此对象。 此方法不是并发安全方法。

```
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>参数

*_Uset*<br/>
源 `concurrent_unordered_set` 对象。

### <a name="return-value"></a>返回值

对此 `concurrent_unordered_set` 对象的引用。

### <a name="remarks"></a>备注

在清除并发无序集中的所有现有元素之后，`operator=` 会将 `_Uset` 的内容复制或移动到此并发无序集。

##  <a name="rehash"></a>rehash

重新生成哈希表。

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>参数

*_Buckets*<br/>
所需的存储桶数。

### <a name="remarks"></a>备注

成员函数将存储桶数更改为至少 `_Buckets` 并根据需要重新生成哈希表。 存储桶的数目必须是2的幂。 如果不是2的幂，则它将向上舍入到2的下一个最大的幂。

如果 bucket 数无效（0或大于最大存储桶数），则会引发[out_of_range](../../../standard-library/out-of-range-class.md)异常。

##  <a name="size"></a>规格

返回此并发容器中的元素数量。 此方法是并发安全方法。

```
size_type size() const;
```

### <a name="return-value"></a>返回值

容器中的项数。

### <a name="remarks"></a>备注

在存在并发插入时，并发容器中的元素数量可能会在调用此函数后立即更改，甚至会在读取返回值之前。

##  <a name="swap"></a>购

交换两个 `concurrent_unordered_set` 对象的内容。 此方法不是并发安全方法。

```
void swap(concurrent_unordered_set& _Uset);
```

### <a name="parameters"></a>参数

*_Uset*<br/>
要交换的 `concurrent_unordered_set` 对象。

##  <a name="unsafe_begin"></a> unsafe_begin

返回一个迭代器，该迭代器指向特定 bucket 的此容器中的第一个元素。

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 开头的迭代器。

##  <a name="unsafe_bucket"></a> unsafe_bucket

返回特定键在此容器中映射到的 bucket 索引。

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>参数

*KVal*<br/>
要搜索的元素键。

### <a name="return-value"></a>返回值

此容器中的密钥的 bucket 索引。

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

返回此容器中的当前 bucket 数。

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>返回值

此容器中的当前 bucket 数。

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

返回此容器的特定存储桶中的项数。

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
要搜索的存储桶。

### <a name="return-value"></a>返回值

此容器中的当前 bucket 数。

##  <a name="unsafe_cbegin"></a> unsafe_cbegin

返回一个迭代器，该迭代器指向特定 bucket 的此容器中的第一个元素。

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 开头的迭代器。

##  <a name="unsafe_cend"></a> unsafe_cend

返回一个迭代器，该迭代器指向特定存储桶中最后一个元素之后的位置。

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 开头的迭代器。

##  <a name="unsafe_end"></a> unsafe_end

返回一个迭代器，该迭代器指向特定 bucket 的此容器中的最后一个元素。

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>参数

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 末尾的迭代器。

##  <a name="unsafe_erase"></a> unsafe_erase

从 `concurrent_unordered_set` 中移除指定位置处的元素。 此方法不是并发安全方法。

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
要从中拭除的迭代器位置。

*KVal*<br/>
要清除的键值。

*first*<br/>
*last*<br/>
迭代器.

### <a name="return-value"></a>返回值

前两个成员函数返回一个迭代器，该迭代器指定在删除的任何元素之外保留的第一个元素; 如果此类元素不存在，则为[end](#end)（）。 第三个成员函数返回它删除的元素的数目。

### <a name="remarks"></a>备注

第一个成员函数 `_Where`删除指向的元素。 第二个成员函数将移除 [`_Begin`，`_End`）范围内的元素。

第三个成员函数删除由[equal_range](#equal_range)（KVal）分隔的范围中的元素。

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

返回此容器中的最大存储桶数。

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>返回值

此容器中的最大存储桶数。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)
