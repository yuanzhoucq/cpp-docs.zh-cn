---
title: "stack (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/stack> 标头 [STL/CLR]"
  - "<stack> 标头 [STL/CLR]"
  - "堆栈类 [STL/CLR]"
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# stack (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于后进先出访问的变长有序元素的对象。  使用容器适配器的 `stack` 管理基础容器为下压堆叠器。  
  
 在下面的解释中，`GValue` 与 `Value` 相同，除非后者是 ref （引用）类型，在这种情况下，它是 `Value^`。  同样，`GContainer` 与 `Container` 相同，除非后者是 ref 类型，在这种情况下，它是 `Container^`。  
  
## 语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[stack::const\_reference](../dotnet/stack-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[stack::container\_type](../dotnet/stack-container-type-stl-clr.md)|基础容器的类型。|  
|[stack::difference\_type](../dotnet/stack-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[stack::generic\_container](../dotnet/stack-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[stack::generic\_value](../dotnet/stack-generic-value-stl-clr.md)|容器适配器的泛型接口的元素的类型。|  
|[stack::reference](../dotnet/stack-reference-stl-clr.md)|元素的引用的类型。|  
|[stack::size\_type](../dotnet/stack-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[stack::value\_type](../dotnet/stack-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[stack::assign](../dotnet/stack-assign-stl-clr.md)|替换任何元素。|  
|[stack::empty](../dotnet/stack-empty-stl-clr.md)|测试元素是否存在。|  
|[stack::get\_container](../dotnet/stack-get-container-stl-clr.md)|访问基础容器。|  
|[stack::pop](../dotnet/stack-pop-stl-clr.md)|移除最后的元素。|  
|[stack::push](../dotnet/stack-push-stl-clr.md)|添加新的末尾元素。|  
|[stack::size](../dotnet/stack-size-stl-clr.md)|计算元素的数量。|  
|[stack::stack](../dotnet/stack-stack-stl-clr.md)|构造容器对象。|  
|[stack::top](../dotnet/stack-top-stl-clr.md)|访问最后一个元素。|  
|[stack::to\_array](../dotnet/stack-to-array-stl-clr.md)|复制控制序列到新数组。|  
  
|Property|说明|  
|--------------|--------|  
|[stack::top\_item](../dotnet/stack-top-item-stl-clr.md)|访问最后一个元素。|  
  
|运算符|说明|  
|---------|--------|  
|[stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)|替换控件序列。|  
|[operator\!\= \(stack\)](../dotnet/operator-inequality-stack-stl-clr.md)|确定 `stack` 对象是否等与不等于另一 `stack` 对象。|  
|[operator\< \(stack\)](../dotnet/operator-less-than-stack-stl-clr.md)|确定 `stack` 对象是否小于另一 `stack` 对象。|  
|[operator\<\= \(stack\)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|确定一个 `stack` 对象是否小于或等于另一个`stack`对象。|  
|[operator\=\= \(stack\)](../dotnet/operator-equality-stack-stl-clr.md)|确定 `stack` 对象是否等于另一 `stack` 对象。|  
|[operator\> \(stack\)](../dotnet/operator-greater-than-stack-stl-clr.md)|确定 `stack` 对象是否大于另一 `stack` 对象。|  
|[operator\>\= \(stack\)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|确定一个 `stack` 对象是否大于或等于另一个`stack`对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|IStackValue\<，容器\>|维护泛型容器适配器。|  
  
## 备注  
 对象为它控制的序列分配和释放存储，通过基础容器 `Container` 类型，其存储了 `Value` 元素和成长的需求。  对象限制推送和弹出一元素的访问，实现一个后进先出 \(LIFO\) 的队列 \(也称为 LIFO 队列、堆栈\)。  
  
## 要求  
 **标头:** \<cliext\/stack\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)