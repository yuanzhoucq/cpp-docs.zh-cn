---
title: "deque (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::deque
dev_langs:
- C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9bd847b2641e6670a91d2edf1eb926aca423ad2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="deque-stlclr"></a>deque (STL/CLR)
此模板类描述控制变长序列的元素具有随机访问的对象。 使用容器`deque`来管理，如下所示一块连续存储，但这可以增大或缩小在任何一端而无需复制剩余的所有元素的元素序列。 因此它的实现可以有效地`double-ended queue`。 (因此名称。)  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 GValue  
 受控序列中元素的泛型类型。  
  
 “值”  
 受控序列中的元素的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](../dotnet/deque-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[deque::const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[deque::const_reverse_iterator (STL/CLR)](../dotnet/deque-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[deque::difference_type (STL/CLR)](../dotnet/deque-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[deque::generic_iterator (STL/CLR)](../dotnet/deque-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[deque::generic_reverse_iterator (STL/CLR)](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[deque::generic_value (STL/CLR)](../dotnet/deque-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[deque::iterator (STL/CLR)](../dotnet/deque-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)|元素的引用的类型。|  
|[deque::reverse_iterator (STL/CLR)](../dotnet/deque-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[deque::size_type (STL/CLR)](../dotnet/deque-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[deque::value_type (STL/CLR)](../dotnet/deque-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)|替换所有元素。|  
|[deque::at (STL/CLR)](../dotnet/deque-at-stl-clr.md)|访问指定位置处的元素。|  
|[deque::back (STL/CLR)](../dotnet/deque-back-stl-clr.md)|访问最后一个元素。|  
|[deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)|指定受控序列的开头。|  
|[deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)|删除所有元素。|  
|[deque::deque (STL/CLR)](../dotnet/deque-deque-stl-clr.md)|构造容器对象。|  
|[deque::empty (STL/CLR)](../dotnet/deque-empty-stl-clr.md)|测试元素是否存在。|  
|[deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)|指定受控序列的末尾。|  
|[deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)|移除指定位置处的元素。|  
|[deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)|访问第一个元素。|  
|[deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)|将元素添加的指定位置。|  
|[deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)|移除的最后一个元素。|  
|[deque::pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)|移除的第一个元素。|  
|[deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)|添加新的最后一个元素。|  
|[deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)|添加新的第一个元素。|  
|[deque::rbegin (STL/CLR)](../dotnet/deque-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[deque::resize (STL/CLR)](../dotnet/deque-resize-stl-clr.md)|更改元素的数目。|  
|[deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md)|对元素数进行计数。|  
|[deque::swap (STL/CLR)](../dotnet/deque-swap-stl-clr.md)|交换两个容器的内容。|  
|[deque::to_array (STL/CLR)](../dotnet/deque-to-array-stl-clr.md)|受控的序列复制到新数组。|  
  
|属性|描述|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)|访问最后一个元素。|  
|[deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)|确定两个`deque`对象是否不相等。|  
|[deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)|访问指定位置处的元素。|  
|[operator< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)|确定如果`deque`对象是否小于另一个`deque`对象。|  
|[operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|确定如果`deque`对象是否小于或等于另一个`deque`对象。|  
|[operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)|替换受控序列。|  
|[operator== (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)|确定如果`deque`对象是否等于另一个`deque`对象。|  
|[operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)|确定如果`deque`对象是否大于另一个`deque`对象。|  
|[operator>= (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|确定如果`deque`对象是否大于或等于另一个`deque`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|<xref:System.Collections.Generic.IList%601>|维护类型化元素的有序的的组。|  
|IDeque < 值\>|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放其控制经过一组存储的句柄指定的块的序列的存储`Value`元素。 根据需要增长数组。 增长将在预先计算或追加新元素的成本常量时间，并且没有剩余的元素分布式的方式发生。 在常量时间内，并不影响剩余元素的情况下，你还可以删除任一端处的元素。 因此，deque 是模板类的基础容器的良好候选[队列 (STL/CLR)](../dotnet/queue-stl-clr.md)或模板类[堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`deque`对象支持随机访问迭代器，这意味着你可以引用元素直接给定其数字的位置，从第一个 （前端） 元素，零计数到[deque:: size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() - 1`最后一个 （后退） 元素。 它还意味着 deque 是模板类的基础容器的良好候选[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 Deque 迭代器存储其关联的 deque 对象，它指定的元素的偏差以及的句柄。 迭代器仅用于其关联的容器对象。 Deque 元素偏移是`not`一定与它的位置相同。 插入的第一个元素具有偏差零下, 一步追加的元素具有偏差 1，但下一步预先计算的元素具有偏差为-1。  
  
 插入或清除任意一端的元素未`not`更改存储在任何有效的偏差的元素的值。 插入或清除内部元素，但是，`can`更改存储在给定的偏移，因此还可以更改迭代器指定的值的元素值。 （该容器可能需要将元素复制向上或向下创建之前插入一个口或擦除后填充一个口。）尽管如此，deque 迭代器就保持有效，只要其偏差指定有效的元素。 此外，有效的迭代器保持 dereferencable-可用来访问或更改元素值，它指定-，只要其偏差是否不等于返回的迭代器的偏差放大`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)