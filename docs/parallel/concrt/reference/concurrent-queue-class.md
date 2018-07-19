---
title: concurrent_queue 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
dev_langs:
- C++
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9a3ee82b8b81532b4e63f080ad321a93725ce41
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693115"
---
# <a name="concurrentqueue-class"></a>concurrent_queue 类
`concurrent_queue` 类是允许对其元素进行先进先出访问的序列容器类。 它支持一组有限的并发安全操作，例如 `push` 和 `try_pop`。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 存储在队列中的元素数据类型。  
  
 `_Ax`  
 表示存储的分配器对象封装有关分配和解除分配此并发队列的内存的详细信息的类型。 此参数为可选参数，默认值为 `allocator<T>`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`allocator_type`|表示适用于并发队列的分配器类的类型。|  
|`const_iterator`|表示非线程安全的类型`const`在并发队列中的元素的迭代器。|  
|`const_reference`|提供对引用的类型`const`元素存储在并发队列供读取和执行`const`操作。|  
|`difference_type`|提供并发队列中的两个元素间的带符号的距离的类型。|  
|`iterator`|表示非线程安全迭代器在并发队列中元素的类型。|  
|`reference`|提供对存储在并发队列中的元素的引用的类型。|  
|`size_type`|一种计算并发队列中的元素数。|  
|`value_type`|表示存储在并发队列中的数据类型的类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[concurrent_queue](#ctor)|已重载。 构造并发队列。|  
|[~ concurrent_queue 析构函数](#dtor)|销毁并发队列。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[clear](#clear)|清除并发队列，销毁所有当前排队元素。 此方法不是并发安全。|  
|[empty](#empty)|调用此方法测试是否目前并发队列为空。 此方法是并发安全的。|  
|[get_allocator](#get_allocator)|返回用于构造并发队列的分配器的副本。 此方法是并发安全的。|  
|[push](#push)|已重载。 将并发队列结尾处的项排。 此方法是并发安全的。|  
|[try_pop](#try_pop)|如果有的话，取消排队队列中的一个项。 此方法是并发安全的。|  
|[unsafe_begin](#unsafe_begin)|已重载。 返回类型的迭代器`iterator`或`const_iterator`到并发队列开头。 此方法不是并发安全。|  
|[unsafe_end](#unsafe_end)|已重载。 返回类型的迭代器`iterator`或`const_iterator`到并发队列的末尾。 此方法不是并发安全。|  
|[unsafe_size](#unsafe_size)|返回队列中的项的数目。 此方法不是并发安全。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `concurrent_queue`  
  
## <a name="requirements"></a>要求  
 **标头：** concurrent_queue.h  
  
 **命名空间：** 并发  
  
##  <a name="clear"></a> 清除 

 清除并发队列，销毁所有当前排队元素。 此方法不是并发安全。  
  
```
void clear();
```  
  
##  <a name="ctor"></a> concurrent_queue 

 构造并发队列。  
  
```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>参数  
 `_InputIterator`  
 指定的值范围的输入迭代器的类型。  
  
 `_Al`  
 要用于此对象的分配器类。  
  
 `_OtherQ`  
 要从中复制或移动元素的源 `concurrent_queue` 对象。  
  
 `_Begin`  
 要复制的元素范围内的第一个元素的位置。  
  
 `_End`  
 要复制的元素范围外的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 所有构造函数都会存储一个分配器对象`_Al`和初始化队列。  
  
 第一个构造函数指定空的初始队列，并显式指定要使用的分配器类型。  
  
 第二个构造函数指定并发队列一份`_OtherQ`。  
  
 第三个构造函数指定并发队列 `_OtherQ` 的移动。  
  
 第四个构造函数指定值提供的迭代器范围 [ `_Begin`， `_End`)。  
  
##  <a name="dtor"></a> ~concurrent_queue 

 销毁并发队列。  
  
```
~concurrent_queue();
```  
  
##  <a name="empty"></a> 为空 

 调用此方法测试是否目前并发队列为空。 此方法是并发安全的。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果我们讨论时刻并发队列为空`false`否则为。  
  
### <a name="remarks"></a>备注  
 此方法时并发安全方面对方法的调用`push`， `try_pop`，和`empty`，则检查它由调用线程时，返回的值可能不正确。  
  
##  <a name="get_allocator"></a> get_allocator 

 返回用于构造并发队列的分配器的副本。 此方法是并发安全的。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 用于构造并发队列的分配器的副本。  
  
##  <a name="push"></a> 推送 

 将并发队列结尾处的项排。 此方法是并发安全的。  
  
```
void push(const T& _Src);

void push(T&& _Src);
```  
  
### <a name="parameters"></a>参数  
 `_Src`  
 要添加到队列的项。  
  
### <a name="remarks"></a>备注  
 `push` 是并发安全方面对方法的调用`push`， `try_pop`，和`empty`。  
  
##  <a name="try_pop"></a> try_pop 

 如果有的话，取消排队队列中的一个项。 此方法是并发安全的。  
  
```
bool try_pop(T& _Dest);
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
 对存储的取消排队的项的位置的引用。  
  
### <a name="return-value"></a>返回值  
 `true` 如果项目已成功取消排队，`false`否则为。  
  
### <a name="remarks"></a>备注  
 如果项目已成功取消排队，参数`_Dest`接收的取消排队的值，将销毁保留在队列中的原始值，并且此函数将返回`true`。 如果没有项要取消排队，则此函数将返回`false`而无需阻止，和的内容`_Dest`参数是不确定。  
  
 `try_pop` 是并发安全方面对方法的调用`push`， `try_pop`，和`empty`。  
  
##  <a name="unsafe_begin"></a> unsafe_begin 

 返回类型的迭代器`iterator`或`const_iterator`到并发队列开头。 此方法不是并发安全。  
  
```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`iterator`或`const_iterator`到并发队列对象的开头。  
  
### <a name="remarks"></a>备注  
 有关迭代器`concurrent_queue`类主要用于调试，它们较慢，以及迭代不是相对于其他队列操作的并发安全。  
  
##  <a name="unsafe_end"></a> unsafe_end 

 返回类型的迭代器`iterator`或`const_iterator`到并发队列的末尾。 此方法不是并发安全。  
  
```
iterator unsafe_end();

const_iterator unsafe_end() const;
```  
  
### <a name="return-value"></a>返回值  
 类型的迭代器`iterator`或`const_iterator`到并发队列的末尾。  
  
### <a name="remarks"></a>备注  
 有关迭代器`concurrent_queue`类主要用于调试，它们较慢，以及迭代不是相对于其他队列操作的并发安全。  
  
##  <a name="unsafe_size"></a> unsafe_size 

 返回队列中的项的数目。 此方法不是并发安全。  
  
```
size_type unsafe_size() const;
```  
  
### <a name="return-value"></a>返回值  
 并发队列的大小。  
  
### <a name="remarks"></a>备注  
 `unsafe_size` 不是并发安全的如果调用同时对方法的调用可能会产生不正确的结果`push`， `try_pop`，和`empty`。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
