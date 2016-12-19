---
title: "queue (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/queue> 标头 [STL/CLR]"
  - "<queue> 标头 [STL/CLR]"
  - "Queue 类 [STL/CLR]"
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于先进先出访问的变长有序元素的对象。  使用容器适配器 `queue` 管理基础容器作为级队列。  
  
 在下面的解释中，`GValue` 与 `Value` 相同，除非后者是 ref （引用）类型，在这种情况下，它是 `Value^`。  同样，`GContainer` 与 `Container` 相同，除非后者是 ref 类型，在这种情况下，它是 `Container^`。  
  
## 语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const\_reference](../dotnet/queue-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[queue::container\_type](../dotnet/queue-container-type-stl-clr.md)|基础容器的类型。|  
|[queue::difference\_type](../dotnet/queue-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[queue::generic\_container](../dotnet/queue-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[queue::generic\_value](../dotnet/queue-generic-value-stl-clr.md)|容器适配器的泛型接口的元素的类型。|  
|[queue::reference](../dotnet/queue-reference-stl-clr.md)|元素的引用的类型。|  
|[queue::size\_type](../dotnet/queue-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[queue::value\_type](../dotnet/queue-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[queue::assign](../dotnet/queue-assign-stl-clr.md)|替换任何元素。|  
|[queue::back](../dotnet/queue-back-stl-clr.md)|访问最后一个元素。|  
|[queue::empty](../dotnet/queue-empty-stl-clr.md)|测试元素是否存在。|  
|[queue::front](../dotnet/queue-front-stl-clr.md)|访问第一个元素。|  
|[queue::get\_container](../dotnet/queue-get-container-stl-clr.md)|访问基础容器。|  
|[queue::pop](../dotnet/queue-pop-stl-clr.md)|移除第一个元素。|  
|[queue::push](../dotnet/queue-push-stl-clr.md)|添加新的末尾元素。|  
|[queue::queue](../dotnet/queue-queue-stl-clr.md)|构造容器对象。|  
|[queue::size](../dotnet/queue-size-stl-clr.md)|计算元素的数量。|  
|[queue::to\_array](../dotnet/queue-to-array-stl-clr.md)|复制控制序列到新数组。|  
  
|Property|说明|  
|--------------|--------|  
|[queue::back\_item](../dotnet/queue-back-item-stl-clr.md)|访问最后一个元素。|  
|[queue::front\_item](../dotnet/queue-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|说明|  
|---------|--------|  
|[queue::operator\=](../dotnet/queue-operator-assign-stl-clr.md)|替换控件序列。|  
|[operator\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)|确定 `queue` 对象是否等与不等于另一 `queue` 对象。|  
|[operator\< \(queue\)](../dotnet/operator-less-than-queue-stl-clr.md)|确定 `queue` 对象是否小于另一 `queue` 对象。|  
|[operator\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|确定一个 `queue` 对象是否小于或等于另一个`queue`对象。|  
|[operator\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)|确定 `queue` 对象是否等于另一 `queue` 对象。|  
|[operator\> \(queue\)](../dotnet/operator-greater-than-queue-stl-clr.md)|确定 `queue` 对象是否大于另一 `queue` 对象。|  
|[operator\>\= \(queue\)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|确定一个 `queue` 对象是否大于或等于另一个`queue`对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|IQueue\<Value, Container\>|维护泛型容器适配器。|  
  
## 备注  
 对象为它控制的序列分配和释放存储，通过基础容器 `Container` 类型，其存储了 `Value` 元素和成长的需求。  对象限制推入第一个元素和最后弹出元素的访问，实现一先进先出初始队列 \(也称为 FIFO 队列或简称为队列\)。  
  
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [stack](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)