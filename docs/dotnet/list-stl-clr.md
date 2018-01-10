---
title: "列表 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list
dev_langs: C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 40046e2b7263559765c2aab2bef13a17c341f7c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="list-stlclr"></a>list (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`list`来管理的元素序列作为双向链接列表节点，各个存储一个元素。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 “值”  
 受控序列中的元素的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[list::const_reference (STL/CLR)](../dotnet/list-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[list::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[list::difference_type (STL/CLR)](../dotnet/list-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[list::generic_iterator (STL/CLR)](../dotnet/list-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[list::generic_reverse_iterator (STL/CLR)](../dotnet/list-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[list::generic_value (STL/CLR)](../dotnet/list-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[list::reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)|元素的引用的类型。|  
|[list::reverse_iterator (STL/CLR)](../dotnet/list-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[list::size_type (STL/CLR)](../dotnet/list-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)|替换所有元素。|  
|[list::back (STL/CLR)](../dotnet/list-back-stl-clr.md)|访问最后一个元素。|  
|[list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)|指定受控序列的开头。|  
|[list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)|删除所有元素。|  
|[list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)|测试元素是否存在。|  
|[list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)|指定受控序列的末尾。|  
|[list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)|移除指定位置处的元素。|  
|[list::front (STL/CLR)](../dotnet/list-front-stl-clr.md)|访问第一个元素。|  
|[list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)|将元素添加的指定位置。|  
|[list::list (STL/CLR)](../dotnet/list-list-stl-clr.md)|构造容器对象。|  
|[list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)|合并两个有序受控的序列。|  
|[list::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)|移除的最后一个元素。|  
|[list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)|移除的第一个元素。|  
|[list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)|添加新的最后一个元素。|  
|[list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)|添加新的第一个元素。|  
|[list::rbegin (STL/CLR)](../dotnet/list-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[list::remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)|删除具有指定值的元素。|  
|[list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)|删除通过了指定的测试的元素。|  
|[list::rend (STL/CLR)](../dotnet/list-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[list::resize (STL/CLR)](../dotnet/list-resize-stl-clr.md)|更改元素的数目。|  
|[list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)|反转受控的序列。|  
|[list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)|对元素数进行计数。|  
|[list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)|受控的序列进行排序。|  
|[list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)|重新联结节点间的链接。|  
|[list::swap (STL/CLR)](../dotnet/list-swap-stl-clr.md)|交换两个容器的内容。|  
|[list::to_array (STL/CLR)](../dotnet/list-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)|删除通过了指定测试的相邻元素。|  
  
|属性|描述|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)|访问最后一个元素。|  
|[list::front_item (STL/CLR)](../dotnet/list-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)|替换受控序列。|  
|[operator!= (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)|确定如果`list`对象是否不等于另一个`list`对象。|  
|[operator< (list) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)|确定如果`list`对象是否小于另一个`list`对象。|  
|[operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)|确定如果`list`对象是否小于或等于另一个`list`对象。|  
|[operator== (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)|确定如果`list`对象是否等于另一个`list`对象。|  
|[operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)|确定如果`list`对象是否大于另一个`list`对象。|  
|[operator>= (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|确定如果`list`对象是否大于或等于另一个`list`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|IList\<值 >|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放的双向链接列表中的各个节点作为其控制的序列的存储。 它可以更改节点，永远不会通过将一个节点的内容复制到另一个之间的链接，重新排列元素。 这意味着可以插入和移除自由不影响剩余元素的元素。 因此，列表是模板类的基础容器的良好候选[队列 (STL/CLR)](../dotnet/queue-stl-clr.md)或模板类[堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`list`对象支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的列表迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用直接给定其数字位置-需要随机访问迭代器的列表元素。 因此列表是`not`用作模板类的基础容器[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 列表迭代器存储其关联的列表节点，后者反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 只要其关联的列表节点是与某些列表相关联，列表迭代器就保持有效。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)