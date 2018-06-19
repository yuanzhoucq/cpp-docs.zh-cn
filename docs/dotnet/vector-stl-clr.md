---
title: 向量 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de5d09d569933dc06666ed2008081703d59c1564
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172633"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
此模板类描述控制变长序列的元素具有随机访问的对象。 使用容器`vector`管理作为一个连续存储的块的元素序列。 块以根据需要增长数组的形式实现。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 值  
 受控序列中的元素的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[vector::const_reference (STL/CLR)](../dotnet/vector-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[vector::const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[vector::difference_type (STL/CLR)](../dotnet/vector-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[vector::reference (STL/CLR)](../dotnet/vector-reference-stl-clr.md)|元素的引用的类型。|  
|[vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[vector::size_type (STL/CLR)](../dotnet/vector-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[vector::value_type (STL/CLR)](../dotnet/vector-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)|替换所有元素。|  
|[vector::at (STL/CLR)](../dotnet/vector-at-stl-clr.md)|访问指定位置处的元素。|  
|[vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)|访问最后一个元素。|  
|[vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)|指定受控序列的开头。|  
|[vector::capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)|报告已分配存储容器的大小。|  
|[vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)|删除所有元素。|  
|[vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)|测试元素是否存在。|  
|[vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)|指定受控序列的末尾。|  
|[vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)|移除指定位置处的元素。|  
|[vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)|访问第一个元素。|  
|[vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)|将元素添加的指定位置。|  
|[vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)|移除的最后一个元素。|  
|[vector::push_back (STL/CLR)](../dotnet/vector-push-back-stl-clr.md)|添加新的最后一个元素。|  
|[vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[vector::rend (STL/CLR)](../dotnet/vector-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)|可确保容器的最小增长容量。|  
|[vector::resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)|更改元素的数目。|  
|[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)|对元素数进行计数。|  
|[vector::swap (STL/CLR)](../dotnet/vector-swap-stl-clr.md)|交换两个容器的内容。|  
|[vector::to_array (STL/CLR)](../dotnet/vector-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[vector::vector (STL/CLR)](../dotnet/vector-vector-stl-clr.md)|构造容器对象。|  
  
|属性|描述|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)|访问最后一个元素。|  
|[vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)|替换受控序列。|  
|[vector::operator(STL/CLR)](../dotnet/vector-operator-stl-clr.md)|访问指定位置处的元素。|  
|[operator!= (vector) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)|确定如果`vector`对象是否不等于另一个`vector`对象。|  
|[operator< (vector) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)|确定如果`vector`对象是否小于另一个`vector`对象。|  
|[operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|确定如果`vector`对象是否小于或等于另一个`vector`对象。|  
|[operator== (vector) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)|确定如果`vector`对象是否等于另一个`vector`对象。|  
|[operator> (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)|确定如果`vector`对象是否大于另一个`vector`对象。|  
|[operator>= (vector) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|确定如果`vector`对象是否大于或等于另一个`vector`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|<xref:System.Collections.Generic.IList%601>|维护类型化元素的有序的的组。|  
|IVector < 值\>|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放其经过一组存储的控制的序列的存储`Value`元素，根据需要增长。 以这种方式将追加一个新的元素的成本是分期常量时间内发生增长。 换而言之，在末尾添加元素的成本不会增加，一般情况下，作为受控的序列获取更大的长度。 因此，一个向量是模板类的基础容器的良好候选[堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`vector`支持随机访问迭代器，这意味着你可以引用元素直接给定其数字的位置，从第一个 （前端） 元素，零计数到`size() - 1`的最后一个 （返回） 元素。 它还意味着向量是模板类的基础容器的良好候选[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 向量迭代器存储其关联的向量对象，它指定的元素的偏差以及的句柄。 迭代器仅用于其关联的容器对象。 向量元素的偏移是它的位置相同。  
  
 插入或清除元素可以更改存储在给定的位置，因此迭代器指定的值还可以更改的元素值。 （该容器可能需要将元素复制向上或向下创建之前插入一个口或擦除后填充一个口。）尽管如此，向量迭代器就保持有效，只要其偏差处于范围内`[0, size()]`。 此外，有效的迭代器保持 dereferencable-可用来访问或更改元素值，它指定-，只要其偏差是否不等于`size()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但是，请注意的容器的句柄不会销毁它的元素。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)  
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)