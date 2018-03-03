---
title: "堆栈 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::stack
dev_langs:
- C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7f6d9eac97fa1907a0901c725645f29dcdd5d9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
此模板类描述控制变长元素序列的最后一个单元中先进先出访问的对象。 使用容器适配器`stack`管理作为推堆栈的基础容器。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。 同样，`GContainer`相同`Container`后者为 ref 类型，除非在这种情况下很`Container^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)|基础容器的类型。|  
|[stack::difference_type (STL/CLR)](../dotnet/stack-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)|容器适配器泛型接口的类型。|  
|[stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)|容器适配器的泛型接口的元素的类型。|  
|[stack::reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)|元素的引用的类型。|  
|[stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[stack::value_type (STL/CLR)](../dotnet/stack-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[stack::assign (STL/CLR)](../dotnet/stack-assign-stl-clr.md)|替换所有元素。|  
|[stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)|测试元素是否存在。|  
|[stack::get_container (STL/CLR)](../dotnet/stack-get-container-stl-clr.md)|访问基础的容器。|  
|[stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)|移除的最后一个元素。|  
|[stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)|添加新的最后一个元素。|  
|[stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)|对元素数进行计数。|  
|[stack::stack (STL/CLR)](../dotnet/stack-stack-stl-clr.md)|构造容器对象。|  
|[stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)|访问最后一个元素。|  
|[stack::to_array (STL/CLR)](../dotnet/stack-to-array-stl-clr.md)|受控的序列复制到新数组。|  
  
|属性|描述|  
|--------------|-----------------|  
|[stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)|访问最后一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)|替换受控序列。|  
|[operator!= (stack) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)|确定如果`stack`对象是否不等于另一个`stack`对象。|  
|[operator< (stack) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)|确定如果`stack`对象是否小于另一个`stack`对象。|  
|[operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|确定如果`stack`对象是否小于或等于另一个`stack`对象。|  
|[operator== (stack) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)|确定如果`stack`对象是否等于另一个`stack`对象。|  
|[operator> (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)|确定如果`stack`对象是否大于另一个`stack`对象。|  
|[operator>= (stack) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|确定如果`stack`对象是否大于或等于另一个`stack`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|IStack\<值、 容器 >|维护泛型容器适配器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放它通过的基础的容器，类型的控制的序列的存储`Container`，存储`Value`元素和根据需要增长。 对象限制的访问权限推送和弹出只是最后一个的元素实现的上一次在先进先出队列 （也称为后进先出队列或堆栈）。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/堆栈 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)