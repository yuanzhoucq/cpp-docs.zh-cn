---
title: "priority_queue (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue
dev_langs: C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7d1459da07f7e392a2da1fbf5d6e9d72c8f4653
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
此模板类描述控制不同的长度为排序的元素序列，具有有限访问权限的对象。 使用容器适配器`priority_queue`管理作为优先级队列的基础容器。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。 同样，`GContainer`相同`Container`后者为 ref 类型，除非在这种情况下很`Container^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 “值”  
 受控序列中的元素的类型。  
  
 容器  
 基础容器的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[priority_queue::container_type (STL/CLR)](../dotnet/priority-queue-container-type-stl-clr.md)|基础容器的类型。|  
|[priority_queue::difference_type (STL/CLR)](../dotnet/priority-queue-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)|容器适配器泛型接口的类型。|  
|[priority_queue::generic_value (STL/CLR)](../dotnet/priority-queue-generic-value-stl-clr.md)|容器适配器的泛型接口的元素的类型。|  
|[priority_queue::reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)|元素的引用的类型。|  
|[priority_queue::size_type (STL/CLR)](../dotnet/priority-queue-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)|用于两个元素的排序委托。|  
|[priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)|替换所有元素。|  
|[priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)|测试元素是否存在。|  
|[priority_queue::get_container (STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)|访问基础的容器。|  
|[priority_queue::pop (STL/CLR)](../dotnet/priority-queue-pop-stl-clr.md)|移除 hghest 优先级的元素。|  
|[priority_queue::priority_queue (STL/CLR)](../dotnet/priority-queue-priority-queue-stl-clr.md)|构造容器对象。|  
|[priority_queue::push (STL/CLR)](../dotnet/priority-queue-push-stl-clr.md)|添加新元素。|  
|[priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)|对元素数进行计数。|  
|[priority_queue::top (STL/CLR)](../dotnet/priority-queue-top-stl-clr.md)|访问优先级最高的元素。|  
|[priority_queue::to_array (STL/CLR)](../dotnet/priority-queue-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)|将复制两个元素的排序委托。|  
  
|属性|描述|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](../dotnet/priority-queue-top-item-stl-clr.md)|访问优先级最高的元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)|替换受控序列。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|IPriorityQueue\<值、 容器 >|维护泛型容器适配器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放它通过的基础的容器，类型的控制的序列的存储`Container`，存储`Value`元素和根据需要增长。 它会保留为堆，与的优先级最高的元素 （顶部元素） 轻松地访问和可移动排序的序列。 对象限制的访问权限将新元素推送和弹出只是优先级最高的元素，实现优先级队列。  
  
 该对象进行排序它通过调用类型的存储的委托对象控制的序列[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)。 在构造 priority_queue; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<(value_type, value_type)`。 通过调用成员函数来访问此存储的对象[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`。  
  
 此类委托对象必须对进行严格弱排序类型的值[priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `value_comp()(X, Y)`返回相同的布尔值导致每次调用。  
  
 如果`value_comp()(X, Y)`为 true，然后`value_comp()(Y, X)`必须是 false。  
  
 如果`value_comp()(X, Y)`为 true，然后`X`称为才能进行排序之前`Y`。  
  
 如果`!value_comp()(X, Y) && !value_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 任何元素`X`，之前`Y`受控序列中中,`key_comp()(Y, X)`为 false。 （对于默认委托对象，密钥永远不会减小值中。）  
  
 最高优先级元素，因此是任何其他元素之前不会对其进行排序的元素。  
  
 由于基础容器保留为堆排序的元素：  
  
 容器必须支持随机访问迭代器。  
  
 具有等效排序的元素可能按不同顺序弹出，不是它们已推送。 （排序不稳定。）  
  
 因此，适合基础容器包括[deque (STL/CLR)](../dotnet/deque-stl-clr.md)和[向量 (STL/CLR)](../dotnet/vector-stl-clr.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)