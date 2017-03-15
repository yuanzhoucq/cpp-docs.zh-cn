---
title: "concurrent_vector 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_vector/Concurrency::concurrent_vector
- concurrent_vector/concurrency::concurrent_vector
dev_langs:
- C++
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 21
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: fdc84a03c562a4efa336f62c0cf0a7529c420f95
ms.lasthandoff: 02/24/2017

---
# <a name="concurrentvector-class"></a>concurrent_vector 类
`concurrent_vector` 类是允许对任意元素进行随机访问的序列容器类。 它支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
 private details::_Concurrent_vector_base_v4;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 对向量中存储的元素数据类型。  
  
 `_Ax`  
 表示存储的分配器对象封装有关分配和解除分配的内存的并发向量的详细信息的类型。 此参数为可选参数，默认值为 `allocator<``T``>`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`allocator_type`|一种表示适用于并发向量的分配器类的类型。|  
|`const_iterator`|读取的类型提供的随机访问迭代器可`const`并发向量中的元素。|  
|`const_pointer`|提供指向的指针的类型`const`并发向量中的元素。|  
|`const_reference`|提供对引用的类型`const`用于读取和执行并发向量中存储元素`const`操作。|  
|`const_reverse_iterator`|一种提供随机访问迭代器可读取任何`const`并发向量中的元素。|  
|`difference_type`|提供并发向量中的两个元素间的带符号的距离的类型。|  
|`iterator`|提供可读取并发向量中的任何元素的随机访问迭代器的类型。 使用迭代器对元素的修改不是并发安全的。|  
|`pointer`|提供指向并发向量中元素的指针的类型。|  
|`reference`|提供对存储在并发向量的元素的引用的类型。|  
|`reverse_iterator`|提供可读取反向并发向量中的任何元素的随机访问迭代器的类型。 使用迭代器对元素的修改不是并发安全的。|  
|`size_type`|一种计算并发向量中元素的数目。|  
|`value_type`|一种表示存储在并发向量中的数据类型的类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[concurrent_vector 构造函数](#ctor)|已重载。 构造并发向量。|  
|[~ concurrent_vector 析构函数](#dtor)|清除所有元素，并销毁此并发向量。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[assign 方法](#assign)|已重载。 清除并发向量中的元素，并为它分配`_N`份`_Item`，或指定的迭代器范围的值 [ `_Begin`， `_End`)。 此方法不是并发安全的。|  
|[at 方法](#at)|已重载。 提供对并发向量中给定索引处的元素的访问。 此方法是并发安全的用于读操作，并且还增加向量中，只要您确保值`_Index`小于并发向量的大小。|  
|[back 方法](#back)|已重载。 返回的引用或`const`到最后一个引用并发向量中的元素。 如果并发向量为空，则返回值是不确定。 此方法是并发安全的。|  
|[begin 方法](#begin)|已重载。 返回一个迭代器类型的`iterator`或`const_iterator`到此并发向量的开头。 此方法是并发安全的。|  
|[容量方法](#capacity)|返回此并发向量可增长而无需分配更多内存的最大大小。 此方法是并发安全的。|  
|[cbegin 方法](#cbegin)|返回一个迭代器类型的`const_iterator`到此并发向量的开头。 此方法是并发安全的。|  
|[cend 方法](#cend)|返回一个迭代器类型的`const_iterator`到此并发向量末尾。 此方法是并发安全的。|  
|[clear 方法](#clear)|清除并发向量中的所有元素。 此方法不是并发安全的。|  
|[crbegin 方法](#crbegin)|返回一个迭代器类型的`const_reverse_iterator`到此并发向量的开头。 此方法是并发安全的。|  
|[crend 方法](#crend)|返回一个迭代器类型的`const_reverse_iterator`到此并发向量末尾。 此方法是并发安全的。|  
|[empty 方法](#empty)|测试是否并发向量为空时调用此方法。 此方法是并发安全的。|  
|[结束方法](#end)|已重载。 返回一个迭代器类型的`iterator`或`const_iterator`到此并发向量末尾。 此方法是并发安全的。|  
|[前面方法](#front)|已重载。 返回的引用或`const`并发向量中的第一个元素的引用。 如果并发向量为空，则返回值是不确定。 此方法是并发安全的。|  
|[get_allocator 方法](#get_allocator)|返回用于构造并发向量的分配器的副本。 此方法是并发安全的。|  
|[grow_by 方法](#grow_by)|已重载。 增大此并发向量的`_Delta`元素。 此方法是并发安全的。|  
|[grow_to_at_least 方法](#grow_to_at_least)|增大此并发向量，直到它具有至少`_N`元素。 此方法是并发安全的。|  
|[max_size 方法](#max_size)|返回的最大并发向量可容纳的元素数。 此方法是并发安全的。|  
|[push_back 方法](#push_back)|已重载。 将给定的项追加到此并发向量末尾。 此方法是并发安全的。|  
|[rbegin 方法](#rbegin)|已重载。 返回一个迭代器类型的`reverse_iterator`或`const_reverse_iterator`到此并发向量的开头。 此方法是并发安全的。|  
|[rend 方法](#rend)|已重载。 返回一个迭代器类型的`reverse_iterator`或`const_reverse_iterator`到此并发向量末尾。 此方法是并发安全的。|  
|[reserve 方法](#reserve)|分配足够的空间大小而变得并发向量`_N`而无需分配更多的内存更高版本。 此方法不是并发安全的。|  
|[resize 方法](#resize)|已重载。 并发向量的大小更改为所请求的大小，删除或根据需要添加元素。 此方法不是并发安全的。|  
|[shrink_to_fit 方法](#shrink_to_fit)|将压缩的内部表示形式要减少碎片并优化内存使用情况的并发向量。 此方法不是并发安全的。|  
|[size 方法](#size)|返回此并发向量中的元素的数目。 此方法是并发安全的。|  
|[swap 方法](#swap)|交换两个并发向量中的内容。 此方法不是并发安全的。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[operator [] 运算符](#operator_at)|已重载。 提供对并发向量中给定索引处的元素的访问。 此方法是并发安全的用于读操作，并且还增加向量中，只要您确保值`_Index`小于并发向量的大小。|  
|[运算符 = 运算符](#operator_eq)|已重载。 另一种内容分配`concurrent_vector`对象传递给它。 此方法不是并发安全的。|  
  
## <a name="remarks"></a>备注  
 有关详细信息`concurrent_vector`类，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>要求  
 **标头︰** concurrent_vector.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameassigna-assign"></a><a name="assign"></a>分配 

 清除并发向量中的元素，并为它分配`_N`份`_Item`，或指定的迭代器范围的值 [ `_Begin`， `_End`)。 此方法不是并发安全的。  
  
```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>参数  
 `_InputIterator`  
 指定的迭代器的类型。  
  
 `_N`  
 要复制到此并发向量的项目数。  
  
 `_Item`  
 对值用来填充此并发向量的引用。  
  
 `_Begin`  
 指向源范围的第一个元素的迭代器。  
  
 `_End`  
 指向一个源范围的最后一个元素之后的迭代器。  
  
### <a name="remarks"></a>备注  
 `assign`不是并发安全的。 您必须确保在调用此方法时，没有其他线程正在调用并发向量中的方法。  
  
##  <a name="a-nameata-at"></a><a name="at"></a>在 

 提供对并发向量中给定索引处的元素的访问。 此方法是并发安全的用于读操作，并且还增加向量中，只要您确保值`_Index`小于并发向量的大小。  
  
```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 要检索的元素的索引。  
  
### <a name="return-value"></a>返回值  
 对给定索引处的项的引用。  
  
### <a name="remarks"></a>备注  
 该函数的版本`at`，返回一个非`const`引用不能用于并发地写入来自不同线程的元素。 应使用不同的同步对象来同步并发读取和写入操作的同一个数据元素。  
  
 该方法将引发`out_of_range`如果`_Index`大于或等于此并发向量的大小和`range_error`如果索引不中断该向量中的一部分。 有关如何矢量变得中断的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
##  <a name="a-namebacka-back"></a><a name="back"></a>返回 

 返回的引用或`const`到最后一个引用并发向量中的元素。 如果并发向量为空，则返回值是不确定。 此方法是并发安全的。  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>返回值  
 引用或`const`到最后一个引用并发向量中的元素。  
  
##  <a name="a-namebegina-begin"></a><a name="begin"></a>开始 

 返回一个迭代器类型的`iterator`或`const_iterator`到此并发向量的开头。 此方法是并发安全的。  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`iterator`或`const_iterator`到此并发向量的开头。  
  
##  <a name="a-namecapacitya-capacity"></a><a name="capacity"></a>容量 

 返回此并发向量可增长而无需分配更多内存的最大大小。 此方法是并发安全的。  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>返回值  
 无需分配更多内存的情况下并发向量可增长到的最大大小。  
  
### <a name="remarks"></a>备注  
 与 c + + 标准库不同`vector`、`concurrent_vector`对象不会移动现有元素，前提是它分配更多的内存。  
  
##  <a name="a-namecbegina-cbegin"></a><a name="cbegin"></a>cbegin 

 返回一个迭代器类型的`const_iterator`到此并发向量的开头。 此方法是并发安全的。  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`const_iterator`到此并发向量的开头。  
  
##  <a name="a-namecenda-cend"></a><a name="cend"></a>cend 

 返回一个迭代器类型的`const_iterator`到此并发向量末尾。 此方法是并发安全的。  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`const_iterator`到此并发向量末尾。  
  
##  <a name="a-namecleara-clear"></a><a name="clear"></a>清除 

 清除并发向量中的所有元素。 此方法不是并发安全的。  
  
```
void clear();
```  
  
### <a name="remarks"></a>备注  
 `clear`不是并发安全的。 您必须确保在调用此方法时，没有其他线程正在调用并发向量中的方法。 `clear`不会释放内部数组。 若要释放内部数组，调用该函数`shrink_to_fit`后`clear`。  
  
##  <a name="a-namectora-concurrentvector"></a><a name="ctor"></a>concurrent_vector 

 构造并发向量。  
  
```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```  
  
### <a name="parameters"></a>参数  
 `M`  
 源向量分配器类型。  
  
 `_InputIterator`  
 输入迭代器的类型。  
  
 `_Al`  
 要用于此对象的分配器类。  
  
 `_Vector`  
 要从中复制或移动元素的源 `concurrent_vector` 对象。  
  
 `_N`  
 `concurrent_vector` 对象的初始容量。  
  
 `_Item`  
 在构造对象中的元素的值。  
  
 `_Begin`  
 要复制的元素范围内的第一个元素的位置。  
  
 `_End`  
 要复制的元素范围外的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 所有构造函数都会存储一个分配器对象`_Al`并初始化此矢量。  
  
 第一个构造函数指定一个空初始矢量，并显式指定的分配器类型。 要使用的。  
  
 第二个和第三个构造函数指定并发向量的副本`_Vector`。  
  
 第四个构造函数指定并发向量 `_Vector` 的移动。  
  
 第五个构造函数指定的指定数量的重复 ( `_N`) 的元素的默认值为类`T`。  
  
 第六个构造函数指定的重复 ( `_N`) 值的元素`_Item`。  
  
 最后一个构造函数指定由迭代器范围提供的值 [ `_Begin`， `_End`)。  
  
##  <a name="a-namedtora-concurrentvector"></a><a name="dtor"></a>~ concurrent_vector 

 清除所有元素，并销毁此并发向量。  
  
```
~concurrent_vector();
```  
  
##  <a name="a-namecrbegina-crbegin"></a><a name="crbegin"></a>crbegin 

 返回一个迭代器类型的`const_reverse_iterator`到此并发向量的开头。 此方法是并发安全的。  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`const_reverse_iterator`到此并发向量的开头。  
  
##  <a name="a-namecrenda-crend"></a><a name="crend"></a>crend 

 返回一个迭代器类型的`const_reverse_iterator`到此并发向量末尾。 此方法是并发安全的。  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`const_reverse_iterator`到此并发向量末尾。  
  
##  <a name="a-nameemptya-empty"></a><a name="empty"></a>为空 

 测试是否并发向量为空时调用此方法。 此方法是并发安全的。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 `true`如果已调用函数，此时该向量为空`false`否则为。  
  
##  <a name="a-nameenda-end"></a><a name="end"></a>结束 

 返回一个迭代器类型的`iterator`或`const_iterator`到此并发向量末尾。 此方法是并发安全的。  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`iterator`或`const_iterator`到此并发向量末尾。  
  
##  <a name="a-namefronta-front"></a><a name="front"></a>前端 

 返回的引用或`const`并发向量中的第一个元素的引用。 如果并发向量为空，则返回值是不确定。 此方法是并发安全的。  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>返回值  
 引用或`const`并发向量中的第一个元素的引用。  
  
##  <a name="a-namegetallocatora-getallocator"></a><a name="get_allocator"></a>get_allocator 

 返回用于构造并发向量的分配器的副本。 此方法是并发安全的。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 用于构造的分配器一份`concurrent_vector`对象。  
  
##  <a name="a-namegrowbya-growby"></a><a name="grow_by"></a>grow_by 

 增大此并发向量的`_Delta`元素。 此方法是并发安全的。  
  
```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```  
  
### <a name="parameters"></a>参数  
 `_Delta`  
 要追加到对象的元素数。  
  
 `_Item`  
 要初始化新元素的值。  
  
### <a name="return-value"></a>返回值  
 追加到第一项的迭代器。  
  
### <a name="remarks"></a>备注  
 如果`_Item`未指定，则为默认构造的新元素。  
  
##  <a name="a-namegrowtoatleasta-growtoatleast"></a><a name="grow_to_at_least"></a>grow_to_at_least 

 增大此并发向量，直到它具有至少`_N`元素。 此方法是并发安全的。  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>参数  
 `_N`  
 为新的最小大小`concurrent_vector`对象。  
  
### <a name="return-value"></a>返回值  
 指向追加序列的开头或索引处的元素的迭代器`_N`如果未追加元素。  
  
##  <a name="a-namemaxsizea-maxsize"></a><a name="max_size"></a>max_size 

 返回的最大并发向量可容纳的元素数。 此方法是并发安全的。  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 元素的最大数目`concurrent_vector`对象可以保存。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 另一种内容分配`concurrent_vector`对象传递给它。 此方法不是并发安全的。  
  
```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```  
  
### <a name="parameters"></a>参数  
 `M`  
 源向量分配器类型。  
  
 `_Vector`  
 源 `concurrent_vector` 对象。  
  
### <a name="return-value"></a>返回值  
 参考这`concurrent_vector`对象。  
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

 提供对并发向量中给定索引处的元素的访问。 此方法是并发安全的用于读操作，并且还增加向量中，只要您确保值`_Index`小于并发向量的大小。  
  
```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 要检索的元素的索引。  
  
### <a name="return-value"></a>返回值  
 对给定索引处的项的引用。  
  
### <a name="remarks"></a>备注  
 版本`operator []`，返回一个非`const`引用不能用于并发地写入来自不同线程的元素。 应使用不同的同步对象来同步并发读取和写入操作的同一个数据元素。  
  
 任何边界检查执行是为了确保`_Index`是到此并发向量的有效索引。  
  
##  <a name="a-namepushbacka-pushback"></a><a name="push_back"></a>push_back 

 将给定的项追加到此并发向量末尾。 此方法是并发安全的。  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>参数  
 `_Item`  
 要追加的值。  
  
### <a name="return-value"></a>返回值  
 追加到项的迭代器。  
  
##  <a name="a-namerbegina-rbegin"></a><a name="rbegin"></a>rbegin 

 返回一个迭代器类型的`reverse_iterator`或`const_reverse_iterator`到此并发向量的开头。 此方法是并发安全的。  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`reverse_iterator`或`const_reverse_iterator`到此并发向量的开头。  
  
##  <a name="a-namerenda-rend"></a><a name="rend"></a>rend 

 返回一个迭代器类型的`reverse_iterator`或`const_reverse_iterator`到此并发向量末尾。 此方法是并发安全的。  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`reverse_iterator`或`const_reverse_iterator`到此并发向量末尾。  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>保留 

 分配足够的空间大小而变得并发向量`_N`而无需分配更多的内存更高版本。 此方法不是并发安全的。  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>参数  
 `_N`  
 要保留的空间的元素数。  
  
### <a name="remarks"></a>备注  
 `reserve`不是并发安全的。 您必须确保在调用此方法时，没有其他线程正在调用并发向量中的方法。 该方法返回后并发向量的容量可能大于请求的保留。  
  
##  <a name="a-nameresizea-resize"></a><a name="resize"></a>调整大小 

 并发向量的大小更改为所请求的大小，删除或根据需要添加元素。 此方法不是并发安全的。  
  
```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```  
  
### <a name="parameters"></a>参数  
 `_N`  
 并发向量的新大小。  
  
 `val`  
 新的大小大于原始大小时添加至向量的新元素的值。 如果省略该值，则新对象分配的默认值为它们的类型。  
  
### <a name="remarks"></a>备注  
 如果容器的大小小于请求的大小，元素将添加到向量，直至到达所请求的大小。 如果容器的大小大于请求的大小，最接近容器末尾的元素删除，直到该容器达到大小`_N`。 如果容器的当前大小与请求的大小相同，则不采取任何操作。  
  
 `resize`不是并发安全的。 您必须确保在调用此方法时，没有其他线程正在调用并发向量中的方法。  
  
##  <a name="a-nameshrinktofita-shrinktofit"></a><a name="shrink_to_fit"></a>shrink_to_fit 

 将压缩的内部表示形式要减少碎片并优化内存使用情况的并发向量。 此方法不是并发安全的。  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>备注  
 此方法将在内部重新分配内存四处移动元素，使所有迭代器失效。 `shrink_to_fit`不是并发安全的。 您必须确保没有其他线程正在调用并发向量中的方法，当调用此函数。  
  
##  <a name="a-namesizea-size"></a><a name="size"></a>大小 

 返回此并发向量中的元素的数目。 此方法是并发安全的。  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 在此元素的数目`concurrent_vector`对象。  
  
### <a name="remarks"></a>备注  
 保证返回的大小包括对函数的调用所附加的所有元素`push_back`，或增大调用此方法之前已完成的操作。 但是，它还可能包括分配的元素，但仍在构建通过对任何增长方法的并发调用。  
  
##  <a name="a-nameswapa-swap"></a><a name="swap"></a>交换 

 交换两个并发向量中的内容。 此方法不是并发安全的。  
  
```
void swap(concurrent_vector& _Vector);
```  
  
### <a name="parameters"></a>参数  
 `_Vector`  
 `concurrent_vector`对象要与其交换内容。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)




