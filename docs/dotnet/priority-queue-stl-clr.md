---
title: "priority_queue (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/queue> 标头 [STL/CLR]"
  - "<queue> 标头 [STL/CLR]"
  - "priority_queue 类 [STL/CLR]"
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制受限访问的变长有序元素序列的对象。  使用容器适配器 `priority_queue` 管理基础容器作为优先级队列。  
  
 在下面的解释中，`GValue` 与 `Value` 相同，除非后者是 ref （引用）类型，在这种情况下，它是 `Value^`。  同样，`GContainer` 与 `Container` 相同，除非后者是 ref 类型，在这种情况下，它是 `Container^`。  
  
## 语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### 参数  
 值  
 受控序列中的元素的类型。  
  
 容器  
 基础容器的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[priority\_queue::const\_reference](../dotnet/priority-queue-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[priority\_queue::container\_type](../dotnet/priority-queue-container-type-stl-clr.md)|基础容器的类型。|  
|[priority\_queue::difference\_type](../dotnet/priority-queue-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[priority\_queue::generic\_container](../dotnet/priority-queue-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[priority\_queue::generic\_value](../dotnet/priority-queue-generic-value-stl-clr.md)|容器适配器的泛型接口的元素的类型。|  
|[priority\_queue::reference](../dotnet/priority-queue-reference-stl-clr.md)|元素的引用的类型。|  
|[priority\_queue::size\_type](../dotnet/priority-queue-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)|两个元素的排序委托。|  
|[priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[priority\_queue::assign](../dotnet/priority-queue-assign-stl-clr.md)|替换任何元素。|  
|[priority\_queue::empty](../dotnet/priority-queue-empty-stl-clr.md)|测试元素是否存在。|  
|[priority\_queue::get\_container](../dotnet/priority-queue-get-container-stl-clr.md)|访问基础容器。|  
|[priority\_queue::pop](../dotnet/priority-queue-pop-stl-clr.md)|移除 hghest 优先级元素。|  
|[priority\_queue::priority\_queue](../dotnet/priority-queue-priority-queue-stl-clr.md)|构造容器对象。|  
|[priority\_queue::push](../dotnet/priority-queue-push-stl-clr.md)|添加一个新元素。|  
|[priority\_queue::size](../dotnet/priority-queue-size-stl-clr.md)|计算元素的数量。|  
|[priority\_queue::top](../dotnet/priority-queue-top-stl-clr.md)|访问要求优先级最高的元素。|  
|[priority\_queue::to\_array](../dotnet/priority-queue-to-array-stl-clr.md)|复制控制序列到新数组。|  
|[priority\_queue::value\_comp](../dotnet/priority-queue-value-comp-stl-clr.md)|复制两个元素的排序委托。|  
  
|Property|说明|  
|--------------|--------|  
|[priority\_queue::top\_item](../dotnet/priority-queue-top-item-stl-clr.md)|访问要求优先级最高的元素。|  
  
|运算符|说明|  
|---------|--------|  
|[priority\_queue::operator\=](../dotnet/priority-queue-operator-assign-stl-clr.md)|替换控件序列。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|IPriorityQueue\<Value，容器\>|维护泛型容器适配器。|  
  
## 备注  
 对象为它控制的序列分配和释放存储，通过基础容器 `Container` 类型，其存储了 `Value` 元素和成长的需求。  它以堆形式保持序列排序，并其优先级最高的元素 \(顶部元素\) 可以方便地访问和删除。  对象限制只能推入新元素并弹出优先级最高的元素，实现了优先级队列。  
  
 对象通过调用存储的 [priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md) 类型的委托对象，对它控制的序列进行排序。  当在构造 priority\_queue 时，您可以指定该存储的委托对象；如果您未指定委托对象，默认比较为 `operator<(value_type, value_type)`。  通过调用成员函数访问该存储区的对象[priority\_queue::value\_comp](../dotnet/priority-queue-value-comp-stl-clr.md)`()`。  
  
 此委托对象必须强加弱序化在 [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md) 类型的值上。  这意味着，任何两键的 `X` 和 `Y`:  
  
 `value_comp()(X, Y)` 返回对每个调用相同的布尔值结果。  
  
 如果 `value_comp()(X, Y)` 为 true，则 `value_comp()(Y, X)` 必须是错误的。  
  
 如果 `value_comp()(X, Y)` 为 true，则 `X` 被视为 `Y`之前的排序。  
  
 如果 `!value_comp()(X, Y) && !value_comp()(Y, X)` 为 true，则 `X` 和 `Y` 是具有相同顺序。  
  
 在控制序列中，对优先于`Y` 的所有元素 `X`来说，`key_comp()(Y, X)` 为 false。\(对于默认委托对象，键值从来不会是降序排列。\)  
  
 优先级最高的元素为在其他元素之前的未排序的一个元素。  
  
 因为基础容器保持元素顺序为堆：  
  
 容器必须支持随机访问迭代器。  
  
 具有等效的顺序元素可能以与它们推入的顺序不同的顺序弹出。\(排序不是稳定的。\)  
  
 因此，基础容器的候选对象包括 [deque](../dotnet/deque-stl-clr.md) [向量](../dotnet/vector-stl-clr.md)。  
  
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [stack](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)