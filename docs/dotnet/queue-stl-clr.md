---
title: 队列 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e65d5a364f5886df2bad976e3c34dc57266b70f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172739"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
此模板类描述控制元素的长短序列，可先入先出访问的对象。 使用容器适配器`queue`来管理为队列的基础容器。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。 同样，`GContainer`相同`Container`后者为 ref 类型，除非在这种情况下很`Container^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 值  
 受控序列中的元素的类型。  
  
 容器  
 基础容器的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|基础容器的类型。|  
|[queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|容器适配器泛型接口的类型。|  
|[queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|容器适配器的泛型接口的元素的类型。|  
|[queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|元素的引用的类型。|  
|[queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|替换所有元素。|  
|[queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|访问最后一个元素。|  
|[queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|测试元素是否存在。|  
|[queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|访问第一个元素。|  
|[queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|访问基础的容器。|  
|[queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|移除的第一个元素。|  
|[queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|添加新的最后一个元素。|  
|[queue::queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|构造容器对象。|  
|[queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|对元素数进行计数。|  
|[queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|受控的序列复制到新数组。|  
  
|属性|描述|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|访问最后一个元素。|  
|[queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|替换受控序列。|  
|[operator!= (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|确定如果`queue`对象是否不等于另一个`queue`对象。|  
|[operator< (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|确定如果`queue`对象是否小于另一个`queue`对象。|  
|[operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|确定如果`queue`对象是否小于或等于另一个`queue`对象。|  
|[operator== (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|确定如果`queue`对象是否等于另一个`queue`对象。|  
|[operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|确定如果`queue`对象是否大于另一个`queue`对象。|  
|[operator>= (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|确定如果`queue`对象是否大于或等于另一个`queue`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|IQueue\<值、 容器 >|维护泛型容器适配器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放它通过的基础的容器，类型的控制的序列的存储`Container`，存储`Value`元素和根据需要增长。 对象限制的访问权限只将推送的第一个元素并弹出的最后一个元素，实现第一个在先进先出队列 （也称为 FIFO 队列或只需队列）。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)