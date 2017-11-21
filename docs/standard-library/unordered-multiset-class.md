---
title: "unordered_multiset 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_set/std::unordered_multiset
- unordered_set/std::unordered_multiset::allocator_type
- unordered_set/std::unordered_multiset::const_iterator
- unordered_set/std::unordered_multiset::const_local_iterator
- unordered_set/std::unordered_multiset::const_pointer
- unordered_set/std::unordered_multiset::const_reference
- unordered_set/std::unordered_multiset::difference_type
- unordered_set/std::unordered_multiset::hasher
- unordered_set/std::unordered_multiset::iterator
- unordered_set/std::unordered_multiset::key_equal
- unordered_set/std::unordered_multiset::key_type
- unordered_set/std::unordered_multiset::local_iterator
- unordered_set/std::unordered_multiset::pointer
- unordered_set/std::unordered_multiset::reference
- unordered_set/std::unordered_multiset::size_type
- unordered_set/std::unordered_multiset::value_type
- unordered_set/std::unordered_multiset::begin
- unordered_set/std::unordered_multiset::bucket
- unordered_set/std::unordered_multiset::bucket_count
- unordered_set/std::unordered_multiset::bucket_size
- unordered_set/std::unordered_multiset::cbegin
- unordered_set/std::unordered_multiset::cend
- unordered_set/std::unordered_multiset::clear
- unordered_set/std::unordered_multiset::count
- unordered_set/std::unordered_multiset::emplace
- unordered_set/std::unordered_multiset::emplace_hint
- unordered_set/std::unordered_multiset::empty
- unordered_set/std::unordered_multiset::end
- unordered_set/std::unordered_multiset::equal_range
- unordered_set/std::unordered_multiset::erase
- unordered_set/std::unordered_multiset::find
- unordered_set/std::unordered_multiset::get_allocator
- unordered_set/std::unordered_multiset::hash
- unordered_set/std::unordered_multiset::insert
- unordered_set/std::unordered_multiset::key_eq
- unordered_set/std::unordered_multiset::load_factor
- unordered_set/std::unordered_multiset::max_bucket_count
- unordered_set/std::unordered_multiset::max_load_factor
- unordered_set/std::unordered_multiset::max_size
- unordered_set/std::unordered_multiset::rehash
- unordered_set/std::unordered_multiset::size
- unordered_set/std::unordered_multiset::swap
- unordered_set/std::unordered_multiset::unordered_multiset
- unordered_set/std::unordered_multiset::operator=
- unordered_set/std::unordered_multiset::hash_function
dev_langs: C++
helpviewer_keywords:
- std::unordered_multiset
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
- std::unordered_multiset::unordered_multiset
- std::unordered_multiset::operator=
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash_function
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
ms.assetid: 70c8dfc5-492a-4af2-84f5-1aa9cb04b71c
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9033d754830a173e261ca7977302da09ef4a809b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="unorderedmultiset-class"></a>unordered_multiset 类
此模板类描述用于控制 `const Key` 类型的变长元素序列的对象。 序列由哈希函数弱排序，哈希函数将此序列分区到称为存储桶的有序序列集中。 在每个存储桶中，比较函数将确定任一元素对是否具有等效顺序。 每个元素同时用作排序键和值。 序列以允许查找、插入和移除任意元素的方式表示，并包含与序列中的元素数量无关的多个操作（常量时间），至少在所有存储桶长度大致相等时如此。 在最坏情况下，当所有元素位于一个存储桶中时，操作数量与序列中的元素数量成比例（线性时间）。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key>>  
class unordered_multiset;  
```  
  
#### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Key`|密钥类型。|  
|`Hash`|哈希函数对象类型。|  
|`Pred`|相等比较函数对象类型。|  
|`Alloc`|allocator 类。|  
  
## <a name="members"></a>成员  
  
|||  
|-|-|  
|类型定义|描述|  
|[allocator_type](#allocator_type)|用于管理存储的分配器的类型。|  
|[const_iterator](#const_iterator)|受控序列的常量迭代器的类型。|  
|[const_local_iterator](#const_local_iterator)|受控序列的常量存储桶迭代器的类型。|  
|[const_pointer](#const_pointer)|元素的常量指针的类型。|  
|[const_reference](#const_reference)|元素的常量引用的类型。|  
|[difference_type](#difference_type)|两个元素间的带符号距离的类型。|  
|[hasher](#hasher)|哈希函数的类型。|  
|[iterator](#iterator)|受控序列的迭代器的类型。|  
|[key_equal](#key_equal)|比较函数的类型。|  
|[key_type](#key_type)|排序键的类型。|  
|[local_iterator](#local_iterator)|受控序列的存储桶迭代器的类型。|  
|[pointer](#pointer)|指向元素的指针的类型。|  
|[reference](#reference)|元素的引用的类型。|  
|[size_type](#size_type)|两个元素间的无符号距离的类型。|  
|[value_type](#value_type)|元素的类型。|  
  
|||  
|-|-|  
|成员函数|描述|  
|[begin](#begin)|指定受控序列的开头。|  
|[存储桶](#bucket)|获取键值的存储桶编号。|  
|[bucket_count](#bucket_count)|获取存储桶数。|  
|[bucket_size](#bucket_size)|获取存储桶的大小。|  
|[cbegin](#cbegin)|指定受控序列的开头。|  
|[cend](#cend)|指定受控序列的末尾。|  
|[clear](#clear)|删除所有元素。|  
|[count](#count)|查找与指定键匹配的元素数。|  
|[emplace](#emplace)|添加就地构造的元素。|  
|[emplace_hint](#emplace_hint)|添加就地构造的元素，附带提示。|  
|[empty](#empty)|测试元素是否存在。|  
|[end](#end)|指定受控序列的末尾。|  
|[equal_range](#equal_range)|查找与指定键匹配的范围。|  
|[erase](#erase)|移除指定位置处的元素。|  
|[find](#find)|查找与指定键匹配的元素。|  
|[get_allocator](#get_allocator)|获取存储的分配器对象。|  
|[hash_function](#hash)|获取存储的哈希函数对象。|  
|[insert](#insert)|添加元素。|  
|[key_eq](#key_eq)|获取存储的比较函数对象。|  
|[load_factor](#load_factor)|对每个存储桶的平均元素数进行计数。|  
|[max_bucket_count](#max_bucket_count)|获取最大的存储桶数。|  
|[max_load_factor](#max_load_factor)|获取或设置每个存储桶的最多元素数。|  
|[max_size](#max_size)|获取受控序列的最大大小。|  
|[rehash](#rehash)|重新生成哈希表。|  
|[size](#size)|对元素数进行计数。|  
|[swap](#swap)|交换两个容器的内容。|  
|[unordered_multiset](#unordered_multiset)|构造容器对象。|  
  
|||  
|-|-|  
|运算符|描述|  
|[unordered_multiset::operator=](#op_eq)|复制哈希表。|  
  
## <a name="remarks"></a>备注  
 对象通过调用两个存储对象，即一个 [unordered_multiset::key_equal](#key_equal) 类型的比较函数对象和一个 [unordered_multiset::hasher](#hasher) 类型的哈希函数对象，对它控制的序列进行排序。 可以通过调用成员函数 [unordered_multiset::key_eq](#key_eq)`()` 访问第一个存储对象；通过调用成员函数 [unordered_multiset::hash_function](#hash)`()` 访问第二个存储对象。 具体而言，对于所有 `X` 类型的值 `Y` 和 `Key`，`key_eq()(X, Y)` 调用将仅在两个参数值拥有等效顺序时返回 true；`hash_function()(keyval)` 调用将生成 `size_t` 类型的值的分布。 与模板类 [unordered_set 类](../standard-library/unordered-set-class.md)不同，模板类 `unordered_multiset` 的对象不确保 `key_eq()(X, Y)` 对于受控序列的任意两个元素始终为 false。 （键不需要唯一。）  
  
 此对象还存储最大加载因子，用于指定每个存储桶的元素的最大所需平均数量。 如果插入元素导致 [unordered_multiset::load_factor](#load_factor)`()` 超出最大加载因子，容器将增加存储桶的数量并根据需要重新生成哈希表。  
  
 受控序列中元素的实际顺序取决于哈希函数、比较函数、插入顺序、最大加载因子和存储桶的当前数量。 通常无法预测受控序列中的元素顺序。 但是，可以始终确保具有等效顺序的任何元素子集在受控序列中相邻。  
  
 对象通过 [unordered_multiset::allocator_type](#allocator_type) 类型的存储分配器对象为其控制的序列分配并释放存储。 此分配器对象必须与 `allocator` 模板类的对象的外部接口相同。 请注意，分配容器对象时不会复制存储的分配器对象。  
  
## <a name="requirements"></a>要求  
 **标头：**\<unordered_set>  
  
 **命名空间：** std  
  
##  <a name="allocator_type"></a>  unordered_multiset::allocator_type  
 用于管理存储的分配器的类型。  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Alloc`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_allocator_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Myset c1;   
  
    Myset::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="begin"></a>  unordered_multiset::begin  
 指定受控序列或存储桶的开头。  
  
```  
iterator begin();

const_iterator begin() const;

 
local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`nbucket`|存储桶编号。|  
  
### <a name="remarks"></a>备注  
 前两个编号函数返回向前迭代器，指向序列的第一个元素（或紧邻空序列后的位置）。 最后两个成员函数返回一个向前迭代器，指向存储桶 `nbucket` 的第一个元素（或刚超出空存储桶末尾的位置）。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_begin.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect first two items " [c] [b]"   
    Myset::iterator it2 = c1.begin();   
    std::cout << " [" << *it2 << "]";   
    ++it2;   
    std::cout << " [" << *it2 << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[c] [b]  
[a]  
```  
  
##  <a name="bucket"></a>  unordered_multiset::bucket  
 获取键值的存储桶编号。  
  
```  
size_type bucket(const Key& keyval) const;
```  
  
### <a name="parameters"></a>参数  
 keyval  
 要映射的键值。  
  
### <a name="remarks"></a>备注  
 成员函数返回当前与键值 `keyval`对应的存储桶编号。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Myset::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="bucket_count"></a>  unordered_multiset::bucket_count  
 获取存储桶数。  
  
```  
size_type bucket_count() const;
```  
  
### <a name="remarks"></a>备注  
 该成员函数将返回存储桶的当前数量。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="bucket_size"></a>  unordered_multiset::bucket_size  
 获取存储桶的大小  
  
```  
size_type bucket_size(size_type nbucket) const;
```  
  
### <a name="parameters"></a>参数  
 `nbucket`  
 存储桶编号。  
  
### <a name="remarks"></a>备注  
 成员函数返回编号为 `nbucket`的存储桶的大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Myset::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="cbegin"></a>  unordered_multiset::cbegin  
 返回确定范围中第一个元素地址的 `const` 迭代器。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 `const` 前向访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，`cbegin() == cend()`）。  
  
### <a name="remarks"></a>备注  
 由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。  
  
 可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在该示例中，将 `Container` 视为支持 `begin()` 和 `cbegin()` 的任何类型的可修改（非 `const`）的容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  unordered_multiset::cend  
 返回一个 `const` 迭代器，此迭代器用于发现刚超出范围中最后一个元素的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 指向刚超出范围末尾的位置的 `const` 向前访问迭代器。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否超过了其范围的末尾。  
  
 可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `end()` 和 `cend()` 的可修改的任何类型的（非- `const`）容器。  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 不应对 `cend` 返回的值取消引用。  
  
##  <a name="clear"></a>  unordered_multiset::clear  
 删除所有元素。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>备注  
 此成员函数调用 [unordered_multiset::erase](#erase)`(` [unordered_multiset::begin](#begin)`(),` [unordered_multiset::end](#end)`())`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_clear.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="const_iterator"></a>  unordered_multiset::const_iterator  
 受控序列的常量迭代器的类型。  
  
```  
typedef T1 const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述为可用作受控序列的常量向前迭代器的对象。 在此处描述为实现定义的 `T1`类型的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_const_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="const_local_iterator"></a>  unordered_multiset::const_local_iterator  
 受控序列的常量存储桶迭代器的类型。  
  
```  
typedef T5 const_local_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作存储桶的常量向前迭代器的对象。 在此处描述为实现定义的 `T5`类型的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_const_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a]  
```  
  
##  <a name="const_pointer"></a>  unordered_multiset::const_pointer  
 元素的常量指针的类型。  
  
```  
typedef Alloc::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作指向受控序列中元素的常量指针的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_const_pointer.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::const_pointer p = &*it;   
        std::cout << " [" << *p << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="const_reference"></a>  unordered_multiset::const_reference  
 元素的常量引用的类型。  
  
```  
typedef Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型将可作为常量引用的对象描述为受控序列中的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_const_reference.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::const_reference ref = *it;   
        std::cout << " [" << ref << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="count"></a>  unordered_multiset::count  
 查找与指定键匹配的元素数。  
  
```  
size_type count(const Key& keyval) const;
```  
  
### <a name="parameters"></a>参数  
 `keyval`  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 该成员函数返回由 [unordered_multiset::equal_range](#equal_range)`(keyval)` 分隔的范围内的元素数量。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "count('A') == " << c1.count('A') << std::endl;   
    std::cout << "count('b') == " << c1.count('b') << std::endl;   
    std::cout << "count('C') == " << c1.count('C') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
count('A') == 0  
count('b') == 1  
count('C') == 0  
```  
  
##  <a name="difference_type"></a>  unordered_multiset::difference_type  
 两个元素间的带符号距离的类型。  
  
```  
typedef T3 difference_type;  
```  
  
### <a name="remarks"></a>备注  
 带符号的整数类型描述一个可表示受控序列中任意两个元素的地址之间的差异的对象。 在此处描述为实现定义的 `T3`类型的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_difference_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    std::cout << "end()-begin() == " << diff << std::endl;   
  
// compute negative difference   
    diff = 0;   
    for (Myset::const_iterator it = c1.end();   
        it != c1.begin(); --it)   
        --diff;   
    std::cout << "begin()-end() == " << diff << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
end()-begin() == 3  
begin()-end() == -3  
```  
  
##  <a name="emplace"></a>  unordered_multiset::emplace  
 就地插入构造的元素（不执行复制或移动操作）。  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`args`|用于构造要插入到 unordered_multiset 中的元素的转发参数。|  
  
### <a name="return-value"></a>返回值  
 指向新插入的元素的迭代器。  
  
### <a name="remarks"></a>备注  
 对容器元素的引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。  
  
 在插入期间，如果引发了异常但未发生在容器的哈希函数中，则不会修改此容器。 如果在哈希函数中引发异常，则未定义此结果。  
  
 有关代码示例，请参阅 [multiset::emplace](../standard-library/multiset-class.md#emplace)。  
  
##  <a name="emplace_hint"></a>  unordered_multiset::emplace_hint  
 使用位置提示就地插入构造的元素（不执行复制或移动操作）。  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`args`|用于构造要插入到 unordered_multiset 中的元素的转发参数。|  
|`where`|有关开始搜索正确插入点的位置的提示。|  
  
### <a name="return-value"></a>返回值  
 指向新插入的元素的迭代器。  
  
### <a name="remarks"></a>备注  
 对容器元素的引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。  
  
 在插入期间，如果引发了异常但未发生在容器的哈希函数中，则不会修改此容器。 如果在哈希函数中引发异常，则未定义此结果。  
  
 有关代码示例，请参阅 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)。  
  
##  <a name="empty"></a>  unordered_multiset::empty  
 测试元素是否存在。  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_empty.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="end"></a>  unordered_multiset::end  
 指定受控序列的末尾。  
  
```  
iterator end();
const_iterator end() const;

 
    local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```  
  
### <a name="parameters"></a>参数  
 `nbucket`  
 存储桶编号。  
  
### <a name="remarks"></a>备注  
 前两个成员函数返回一个向前迭代器，它指向刚超出序列末尾的位置。 最后两个成员函数返回一个向前迭代器，它指向刚超出存储桶 `nbucket` 末尾的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_end.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect last two items " [a] [b]"   
    Myset::iterator it2 = c1.end();   
    --it2;   
    std::cout << " [" << *it2 << "]";   
    --it2;   
    std::cout << " [" << *it2 << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));   
    --lit;   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a] [b]  
[a]  
```  
  
##  <a name="equal_range"></a>  unordered_multiset::equal_range  
 查找与指定键匹配的范围。  
  
```  
std::pair<iterator, iterator>  
    equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>  
    equal_range(const Key& keyval) const;
```  
  
### <a name="parameters"></a>参数  
 `keyval`  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数返回一对迭代器 `X` ，以便 `[X.first, X.second)` 仅分隔受控序列中与 `keyval`具有等效排序的那些元素。 如果不存在此类元素，则两个迭代器均为 `end()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_equal_range.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display results of failed search   
    std::pair<Myset::iterator, Myset::iterator> pair1 =   
        c1.equal_range('x');   
    std::cout << "equal_range('x'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << *pair1.first << "]";   
    std::cout << std::endl;   
  
// display results of successful search   
    pair1 = c1.equal_range('b');   
    std::cout << "equal_range('b'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << *pair1.first << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
equal_range('x'):  
equal_range('b'): [b]  
```  
  
##  <a name="erase"></a>  unordered_multiset::erase  
 从 unordered_multiset 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>参数  
 `Where`  
 要移除的元素的位置。  
  
 `First`  
 要移除的第一个元素的位置。  
  
 `Last`  
 要移除的刚超出最后一个元素的位置。  
  
 `Key`  
 要移除的元素的关键值。  
  
### <a name="return-value"></a>返回值  
 对于前两个成员函数，可为指定已移除的任何元素之外保留的第一个元素；如果此类元素不存在，则为 unordered_multiset 末尾的元素。  
  
 对于第三个成员函数，返回已从 unordered_multiset 中移除的元素的数目。  
  
### <a name="remarks"></a>备注  
 有关代码示例，请参阅 [set::erase](../standard-library/set-class.md#erase)。  
  
##  <a name="find"></a>  unordered_multiset::find  
 查找与指定键匹配的元素。  
  
```  
const_iterator find(const Key& keyval) const;
```  
  
### <a name="parameters"></a>参数  
 `keyval`  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数返回 [unordered_multiset::equal_range](#equal_range)`(keyval).first`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_find.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// try to find and fail   
    std::cout << "find('A') == "   
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;   
  
// try to find and succeed   
    Myset::iterator it = c1.find('b');   
    std::cout << "find('b') == "   
        << std::boolalpha << (it != c1.end())   
        << ": [" << *it << "]" << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
find('A') == false  
find('b') == true: [b]  
```  
  
##  <a name="get_allocator"></a>  unordered_multiset::get_allocator  
 获取存储的分配器对象。  
  
```  
Alloc get_allocator() const;
```  
  
### <a name="remarks"></a>备注  
 该成员函数将返回存储的分配器对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_get_allocator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Myset c1;   
  
    Myset::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="hash"></a>  unordered_multiset::hash_function  
 获取存储的哈希函数对象。  
  
```  
Hash hash_function() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回存储的哈希函数对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_hash_function.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="hasher"></a>  unordered_multiset::hasher  
 哈希函数的类型。  
  
```  
typedef Hash hasher;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Hash`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_hasher.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="insert"></a>  unordered_multiset::insert  
 将一个元素或元素范围插入到 unordered_multiset 中。  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Val`|要插入到 unordered_multiset 中的元素的值。|  
|`Where`|开始搜索正确插入点的位置。|  
|`ValTy`|一种模板参数，它指定 unordered_multiset 可用于构造 [value_type](../standard-library/map-class.md#value_type) 元素的参数类型，并将 `Val` 作为参数完美转发。|  
|`First`|要复制的第一个元素的位置。|  
|`Last`|要复制的最后一个元素以外的位置。|  
|`InputIterator`|满足[输入迭代器](../standard-library/input-iterator-tag-struct.md)需求的模板函数自变量，该输入迭代器指向可用于构造 [value_type](../standard-library/map-class.md#value_type) 对象的类型的元素。|  
|`IList`|从中复制元素的 [initializer_list](../standard-library/initializer-list.md)。|  
  
### <a name="return-value"></a>返回值  
 单个元素插入成员函数 (1) 和 (2) 返回迭代器，该迭代器指向将新元素插入到 unordered_multiset 中的位置。  
  
 附带提示的单个元素成员函数 (3) 和 (4) 返回迭代器，该迭代器指向将新元素插入到 unordered_multiset 中的位置。  
  
### <a name="remarks"></a>备注  
 指针或引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。  
  
 在只插入单个元素的过程中，如果引发异常，但是异常并未在容器的哈希函数中发生，则不会修改该容器的状态。 如果在哈希函数中引发异常，则未定义此结果。 在插入多个元素的过程中，如果引发异常，则会使容器处于未指定但有效的状态。  
  
 容器的 [value_type](../standard-library/map-class.md#value_type) 是属于该容器的 typedef；对于集，`unordered_multiset<V>::value_type` 是 `const V` 类型。  
  
 范围成员函数 (5) 将元素值序列插到 unordered_multiset 中，它对应于迭代器在范围 `[First, Last)` 中所处理的每一个元素；因此，不会插入 `Last`。 容器成员函数 `end()` 是指容器中最后一个元素之后的位置，例如，`m.insert(v.begin(), v.end());` 语句会将 `v` 的所有元素插入到 `m` 中。  
  
 初始化表达式列表成员函数 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 将元素复制到 unordered_multiset 中。  
  
 有关就地插入构造的元素（即不执行复制或移动操作），请参阅 [unordered_multiset::emplace](#emplace) 和 [unordered_multiset::emplace_hint](#emplace_hint)。  
  
 有关代码示例，请参阅 [multiset::insert](../standard-library/multiset-class.md#insert)。  
  
##  <a name="iterator"></a>  unordered_multiset::iterator  
 一种类型，此类型提供可读取 unordered_multiset 中的元素的[向前迭代器](../standard-library/forward-iterator-tag-struct.md)。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>示例  
  有关如何声明和使用 **iterator** 的示例，请参阅 [begin](../standard-library/multiset-class.md#begin) 的示例。  
  
##  <a name="key_eq"></a>  unordered_multiset::key_eq  
 获取存储的比较函数对象。  
  
```  
Pred key_eq() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回存储的比较函数对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_key_eq.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="key_equal"></a>  unordered_multiset::key_equal  
 比较函数的类型。  
  
```  
typedef Pred key_equal;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Pred`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_key_equal.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="key_type"></a>  unordered_multiset::key_type  
 排序键的类型。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Key`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_key_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Myset::key_type key = 'd';   
    Myset::value_type val = key;   
    c1.insert(val);   
  
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[d] [c] [b] [a]  
```  
  
##  <a name="load_factor"></a>  unordered_multiset::load_factor  
 对每个存储桶的平均元素数进行计数。  
  
```  
float load_factor() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回每个存储桶的平均元素数 `(float)`[unordered_multiset::size](#size)`() / (float)`[unordered_multiset::bucket_count](#bucket_count)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
##  <a name="local_iterator"></a>  unordered_multiset::local_iterator  
 存储桶迭代器类型。  
  
```  
typedef T4 local_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述可用作存储桶的向前迭代器的对象。 在此处描述为实现定义的 `T4`类型的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a]  
```  
  
##  <a name="max_bucket_count"></a>  unordered_multiset::max_bucket_count  
 获取最大的存储桶数。  
  
```  
size_type max_bucket_count() const;
```  
  
### <a name="remarks"></a>备注  
 该成员函数将返回当前允许的最大存储桶数。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_max_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="max_load_factor"></a>  unordered_multiset::max_load_factor  
 获取或设置每个存储桶的最多元素数。  
  
```  
float max_load_factor() const;

 
void max_load_factor(float factor);
```  
  
### <a name="parameters"></a>参数  
 `factor`  
 新的最大加载因子。  
  
### <a name="remarks"></a>备注  
 第一个成员函数将返回存储的最大加载因子。 第二个成员函数将用 `factor`替换已存储的最大加载因子。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_max_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="max_size"></a>  unordered_multiset::max_size  
 获取受控序列的最大大小。  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>备注  
 该成员函数将返回对象可控制的最长序列的长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_max_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    std::cout << "max_size() == " << c1.max_size() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
max_size() == 4294967295  
```  
  
##  <a name="op_eq"></a>unordered_multiset::operator=  
 复制哈希表。  
  
```  
unordered_multiset& operator=(const unordered_multiset& right);

unordered_multiset& operator=(unordered_multiset&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`right`|正在被复制到 `unordered_multiset` 中的 [unordered_multiset](../standard-library/unordered-multiset-class.md)。|  
  
### <a name="remarks"></a>备注  
 清除 `unordered_multiset` 中的任何现有元素后，`operator=` 会将 `right` 的内容复制或移动到 `unordered_multiset`。  
  
### <a name="example"></a>示例  
  
```cpp  
// unordered_multiset_operator_as.cpp  
// compile with: /EHsc  
#include <unordered_set>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   unordered_multiset<int> v1, v2, v3;  
   unordered_multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>  unordered_multiset::pointer  
 指向元素的指针的类型。  
  
```  
typedef Alloc::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作指向受控序列中元素的指针的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_pointer.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::key_type key = *it;   
        Myset::pointer p = &key;   
        std::cout << " [" << *p << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="reference"></a>  unordered_multiset::reference  
 元素的引用的类型。  
  
```  
typedef Alloc::reference reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作对受控序列中元素的引用的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_reference.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::key_type key = *it;   
        Myset::reference ref = key;   
        std::cout << " [" << ref << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="rehash"></a>  unordered_multiset::rehash  
 重新生成哈希表。  
  
```  
void rehash(size_type nbuckets);
```  
  
### <a name="parameters"></a>参数  
 `nbuckets`  
 请求的存储桶数。  
  
### <a name="remarks"></a>备注  
 成员函数将存储桶数更改为至少 `nbuckets` 并根据需要重新生成哈希表。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_rehash.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_load_factor() == 0.1  
```  
  
##  <a name="size"></a>  unordered_multiset::size  
 对元素数进行计数。  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="size_type"></a>  unordered_multiset::size_type  
 两个元素间的无符号距离的类型。  
  
```  
typedef T2 size_type;  
```  
  
### <a name="remarks"></a>备注  
 无符号的整数类型描述可表示任何受控序列长度的对象。 在此处描述为实现定义的 `T2`类型的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_size_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::size_type sz = c1.size();   
  
    std::cout << "size == " << sz << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
size == 0  
```  
  
##  <a name="swap"></a>  unordered_multiset::swap  
 交换两个容器的内容。  
  
```  
void swap(unordered_multiset& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要交换的容器。  
  
### <a name="remarks"></a>备注  
 成员函数交换 `*this` 和 `right`之间的受控序列。 如果为 [unordered_multiset::get_allocator](#get_allocator)`() == right.get_allocator()`，则它在固定时间内执行此操作，它仅在对类型 `Tr` 的存储特征对象进行复制时引发异常，并且不使任何引用、指针或指定两个受控序列中的元素的迭代器失效。 否则，它所执行的元素分配和构造函数调用数量会与两个受控序列中的元素数量成正比。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_swap.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    Myset c2;   
  
    c2.insert('d');   
    c2.insert('e');   
    c2.insert('f');   
  
    c1.swap(c2);   
  
// display contents " [f] [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[f] [e] [d]  
[c] [b] [a]  
```  
  
##  <a name="unordered_multiset"></a>  unordered_multiset::unordered_multiset  
 构造容器对象。  
  
```  
unordered_multiset(
    const unordered_multiset& Right);

explicit unordered_multiset(
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());

unordered_multiset(
    unordered_multiset&& Right);

unordered_set(
    initializer_list<Type> IList);

unordered_set(
    initializer_list<Typ> IList,  
    size_type Bucket_count);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,   
    const Key& Key);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,   
    const Key& Key,   
    const Allocator& Al);

template <class InputIterator>  
unordered_multiset(
 InputIterator First,   
    InputIterator Last,  
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`InputIterator`|迭代器类型。|  
|`Al`|要存储的分配器对象。|  
|`Comp`|要存储的比较函数对象。|  
|`Hash`|要存储的哈希函数对象。|  
|`Bucket_count`|存储桶的最少数量。|  
|`Right`|要复制的容器。|  
|`IList`|要从中进行复制的 initializer_list。|  
  
### <a name="remarks"></a>备注  
 第一个构造函数指定通过 `Right` 控制的序列副本。 第二个构造函数指定空的受控序列。 第三个构造函数插入元素值 `[First, Last)` 的序列。 第四个构造函数通过移动 `Right` 指定序列副本。  
  
 所有构造函数还初始化若干存储的值。 对于复制构造函数，值从 `Right` 获取。 否则：  
  
 存储桶的最少数量是参数 `Bucket_count`（如果有）；否则为此处说明的默认值 `N0`。  
  
 哈希函数对象是参数 `Hash`（如果有）；否则为 `Hash()`。  
  
 比较函数对象是参数 `Comp`（如果有）；否则为 `Comp()`。  
  
 分配器对象是参数 `Al`（如果有）；否则为 `Alloc()`。  
  
##  <a name="value_type"></a>  unordered_multiset::value_type  
 元素的类型。  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了受控序列的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__unordered_set__unordered_multiset_value_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Myset::key_type key = 'd';   
    Myset::value_type val = key;   
    c1.insert(val);   
  
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[d] [c] [b] [a]  
```  
  
## <a name="see-also"></a>另请参阅  
 [<unordered_set>](../standard-library/unordered-set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

