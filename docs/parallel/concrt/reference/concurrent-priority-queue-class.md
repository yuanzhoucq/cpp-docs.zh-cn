---
title: "concurrent_priority_queue 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
dev_langs: C++
helpviewer_keywords: concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d6789bd74924912361b3045d112c91ec6dcaedbe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue 类
`concurrent_priority_queue` 类是允许多个线程并发推送和弹出项的容器。 项按优先级顺序弹出，其中优先级由作为模板自变量提供的涵子确定。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在优先级队列中的元素的数据类型。  
  
 `_Compare`  
 可将两个元素的值作为排序键进行比较以确定其在优先级队列中相对顺序的函数对象的类型。 此参数为可选自变量，默认值是二元谓词 `less<T>`。  
  
 `_Ax`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关并发优先级队列的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `allocator<T>`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`allocator_type`|一种表示适用于并发优先级队列的分配器类的类型。|  
|`const_reference`|一种表示存储在并发优先级队列中类型的一个元素的常量引用的类型。|  
|`reference`|一种表示存储在并发优先级队列中类型的一个元素的引用的类型。|  
|`size_type`|一种计算并发优先级队列中元素数量的类型。|  
|`value_type`|一种表示存储在并发优先级队列中的数据类型的类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[concurrent_priority_queue](#ctor)|已重载。 构造并发优先级队列。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[clear](#clear)|清除并发优先级中的所有元素。 此方法不是并发安全。|  
|[empty](#empty)|测试在调用此方法时并发优先级队列是否为空。 此方法是并发安全的。|  
|[get_allocator](#get_allocator)|返回用于构造并发优先级队列的分配器的副本。 此方法是并发安全的。|  
|[push](#push)|已重载。 在并发优先级队列中添加一个元素。 此方法是并发安全的。|  
|[size](#size)|返回并发优先级队列中元素的数量。 此方法是并发安全的。|  
|[swap](#swap)|交换两个并发优先级队列中的内容。 此方法不是并发安全。|  
|[try_pop](#try_pop)|如果队列非空，移除并返回队列中优先级最高的元素。 此方法是并发安全的。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|已重载。 将分配的另一个内容`concurrent_priority_queue`于此对象。 此方法不是并发安全。|  
  
## <a name="remarks"></a>备注  
 有关详细信息`concurrent_priority_queue`类，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `concurrent_priority_queue`  
  
## <a name="requirements"></a>要求  
 **标头：** concurrent_priority_queue.h  
  
 **命名空间：** 并发  
  
##  <a name="clear"></a>清除 

 清除并发优先级中的所有元素。 此方法不是并发安全。  
  
```
void clear();
```  
  
### <a name="remarks"></a>备注  
 `clear`不是并发安全。 你必须确保在调用此方法时，没有其他线程所调用上并发优先级队列的方法。 `clear`不会释放内存。  
  
##  <a name="ctor"></a>concurrent_priority_queue 

 构造并发优先级队列。  
  
```
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```  
  
### <a name="parameters"></a>参数  
 `_InputIterator`  
 输入迭代器的类型。  
  
 `_Al`  
 要用于此对象的分配器类。  
  
 `_Init_capacity`  
 `concurrent_priority_queue` 对象的初始容量。  
  
 `_Begin`  
 要复制的范围元素中的第一个元素的位置。  
  
 `_End`  
 要复制的元素范围以外的第一个元素的位置。  
  
 `_Src`  
 要从中复制或移动元素的源 `concurrent_priority_queue` 对象。  
  
### <a name="remarks"></a>备注  
 所有构造函数都会存储一个分配器对象`_Al`和初始化优先级队列。  
  
 第一个构造函数指定空的初始优先级队列，并 （可选） 指定的分配器。  
  
 第二个构造函数指定优先级队列的初始容量`_Init_capacity`和 （可选） 指定的分配器。  
  
 第三个构造函数指定值提供的迭代器范围 [ `_Begin`， `_End`) 和 （可选） 指定的分配器。  
  
 第四个和第五个构造函数指定优先级队列一份`_Src`。  
  
 第六个和第七个构造函数指定的优先级队列移动`_Src`。  
  
##  <a name="empty"></a>为空 

 测试在调用此方法时并发优先级队列是否为空。 此方法是并发安全的。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 `true`如果已调用函数，此时优先级队列为空`false`否则为。  
  
##  <a name="get_allocator"></a>get_allocator 

 返回用于构造并发优先级队列的分配器的副本。 此方法是并发安全的。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 用于构造的分配器一份`concurrent_priority_queue`对象。  
  
##  <a name="operator_eq"></a>运算符 = 

 将分配的另一个内容`concurrent_priority_queue`于此对象。 此方法不是并发安全。  
  
```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```  
  
### <a name="parameters"></a>参数  
 `_Src`  
 源 `concurrent_priority_queue` 对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`concurrent_priority_queue`对象。  
  
##  <a name="push"></a>推送 

 在并发优先级队列中添加一个元素。 此方法是并发安全的。  
  
```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```  
  
### <a name="parameters"></a>参数  
 `_Elem`  
 要添加到并发优先级队列的元素。  
  
##  <a name="size"></a>大小 

 返回并发优先级队列中元素的数量。 此方法是并发安全的。  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 在此元素的数目`concurrent_priority_queue`对象。  
  
### <a name="remarks"></a>备注  
 返回的大小保证将通过对函数的调用添加的所有元素都包含`push`。 但是，它可能不反映挂起的并发操作的结果。  
  
##  <a name="swap"></a>交换 

 交换两个并发优先级队列中的内容。 此方法不是并发安全。  
  
```
void swap(concurrent_priority_queue& _Queue);
```  
  
### <a name="parameters"></a>参数  
 `_Queue`  
 `concurrent_priority_queue`对象要与其交换内容。  
  
##  <a name="try_pop"></a>try_pop 

 如果队列非空，移除并返回队列中优先级最高的元素。 此方法是并发安全的。  
  
```
bool try_pop(reference _Elem);
```  
  
### <a name="parameters"></a>参数  
 `_Elem`  
 对非空队列是否将使用最高的优先级元素，填充的变量的引用。  
  
### <a name="return-value"></a>返回值  
 `true`如果弹出一个值，已`false`否则为。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)



