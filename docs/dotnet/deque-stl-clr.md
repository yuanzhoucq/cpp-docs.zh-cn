---
title: "deque (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/deque> 标头 [STL/CLR]"
  - "<deque> 标头 [STL/CLR]"
  - "deque 类 [STL/CLR]"
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# deque (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类描述对象具有控件随机访问更改长度元素的序列。  使用 `deque` 容器类似于管理存储连续块，但是，可以增大或缩小的任一端，而无需将剩余的元素的序列。  因而它可以有效地实现 `double-ended queue`。\(该名称。\)  
  
 在如下解释，`GValue` 与 `Value` 相同，除非是后者 ref 类型，在这种情况下，它是 `Value^`条件下。  
  
## 语法  
  
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
  
#### 参数  
 G 值  
 一元素的泛型类型。控制的序列。  
  
 值  
 受控序列中的元素的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[deque::const\_iterator](../dotnet/deque-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[deque::const\_reference](../dotnet/deque-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[deque::const\_reverse\_iterator](../dotnet/deque-const-reverse-iterator-stl-clr.md)|常数进行反向迭代器类型的控制的序列。|  
|[deque::difference\_type](../dotnet/deque-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)|泛型接口的类型容器中。|  
|[deque::generic\_iterator](../dotnet/deque-generic-iterator-stl-clr.md)|一迭代器的类型通用接口的容器的。|  
|[deque::generic\_reverse\_iterator](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|一进行反向迭代器的类型泛型接口的容器的。|  
|[deque::generic\_value](../dotnet/deque-generic-value-stl-clr.md)|的元素类型泛型接口的容器的。|  
|[deque::iterator](../dotnet/deque-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[deque::reference](../dotnet/deque-reference-stl-clr.md)|元素的引用的类型。|  
|[deque::reverse\_iterator](../dotnet/deque-reverse-iterator-stl-clr.md)|一进行反向迭代器类型的控制的序列。|  
|[deque::size\_type](../dotnet/deque-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[deque::value\_type](../dotnet/deque-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[deque::assign](../dotnet/deque-assign-stl-clr.md)|替换任何元素。|  
|[deque::at](../dotnet/deque-at-stl-clr.md)|访问元素中的指定位置。|  
|[deque::back](../dotnet/deque-back-stl-clr.md)|访问最后一个元素。|  
|[deque::begin](../dotnet/deque-begin-stl-clr.md)|指定受控序列的开头。|  
|[deque::clear](../dotnet/deque-clear-stl-clr.md)|移除所有元素。|  
|[deque::deque](../dotnet/deque-deque-stl-clr.md)|构造容器对象。|  
|[deque::empty](../dotnet/deque-empty-stl-clr.md)|测试元素不存在。|  
|[deque::end](../dotnet/deque-end-stl-clr.md)|指定受控序列的末尾。|  
|[deque::erase](../dotnet/deque-erase-stl-clr.md)|移除指定位置处的元素。|  
|[deque::front](../dotnet/deque-front-stl-clr.md)|访问第一个元素。|  
|[deque::insert](../dotnet/deque-insert-stl-clr.md)|将元素中的指定位置。|  
|[deque::pop\_back](../dotnet/deque-pop-back-stl-clr.md)|移除最后一个元素。|  
|[deque::pop\_front](../dotnet/deque-pop-front-stl-clr.md)|移除第一个元素。|  
|[deque::push\_back](../dotnet/deque-push-back-stl-clr.md)|添加一个新的元素之前。|  
|[deque::push\_front](../dotnet/deque-push-front-stl-clr.md)|添加新的第一个元素。|  
|[deque::rbegin](../dotnet/deque-rbegin-stl-clr.md)|指定反转的受控序列的开头。|  
|[deque::rend](../dotnet/deque-rend-stl-clr.md)|指定反转的受控序列的末尾。|  
|[deque::resize](../dotnet/deque-resize-stl-clr.md)|更改元素的数量。|  
|[deque::size](../dotnet/deque-size-stl-clr.md)|计算元素的数量。|  
|[deque::swap](../dotnet/deque-swap-stl-clr.md)|交换两个容器的内容。|  
|[deque::to\_array](../dotnet/deque-to-array-stl-clr.md)|复制控件序列到新数组。|  
  
|Property|说明|  
|--------------|--------|  
|[deque::back\_item](../dotnet/deque-back-item-stl-clr.md)|访问最后一个元素。|  
|[deque::front\_item](../dotnet/deque-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|说明|  
|---------|--------|  
|[deque::operator\!\=](../dotnet/deque-operator-inequality-stl-clr.md)|确定两个 `deque` 对象是否不相等。|  
|[deque::operator](../dotnet/deque-operator-stl-clr.md)|访问元素中的指定位置。|  
|[operator\< \(deque\)](../dotnet/operator-less-than-deque-stl-clr.md)|确定 `deque` 对象是否大于另一 `deque` 对象很低。|  
|[operator\<\= \(deque\)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|确定 `deque` 对象是否小于或等于另一个 `deque` 对象。|  
|[operator\= \(deque\)](../dotnet/operator-assign-deque-stl-clr.md)|控件替换序列。|  
|[operator\=\= \(deque\)](../dotnet/operator-equality-deque-stl-clr.md)|确定 `deque` 对象是否与另一 `deque` 对象相同。|  
|[operator\> \(deque\)](../dotnet/operator-greater-than-deque-stl-clr.md)|确定 `deque` 对象是否大于另一 `deque` 对象操作。|  
|[operator\>\= \(deque\)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|确定 `deque` 对象是否大于或等于另一个 `deque` 对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过序列元素。|  
|<xref:System.Collections.ICollection>|维护元素组。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列通过输出元素。|  
|<xref:System.Collections.Generic.ICollection%601>|打印维护元素组。|  
|<xref:System.Collections.Generic.IList%601>|打印 maintain 排序元素组。|  
|IDeque\<Value\>|维护型容器。|  
  
## 备注  
 对象分配并通过的某些处理控制 `Value` 元素指定块序列中未使用助记域。  数组增大在要求。  根据发生，在这种情况下成本前面添加或追加新的元素。是一成不变的时间，并且，剩余的元素不会干扰。  还可以移除元素。任意一端。常量时间和不干扰的其余元素。  因此，deque 是基础容器的理想候选项模板类或模板类。[queue](../dotnet/queue-stl-clr.md)[stack](../dotnet/stack-stl-clr.md)。  
  
 `deque` 对象支持随机访问迭代器，这意味着可以引用元素直接为其数字位置，从零开始计数第一个 \(\) 元素的之前，最后 \(返回\) [deque::size](../dotnet/deque-size-stl-clr.md)元素的`() - 1`。  同时也意味着 deque 是基础容器的理想候选项模板类的 [priority\_queue](../dotnet/priority-queue-stl-clr.md)。  
  
 deque 迭代器存储句柄与其关联 deque 对象，以及其选定元素的偏差。  可以只使用迭代器与它们关联的容器对象。  deque 元素那样偏重必须是 `not` 与其位置相同。  插入的第一个元素有偏差零，下的元素追加有偏差 1，但后面带有在前面的元素有偏差 \-1。  
  
 插入或元素清除在任意一端执行修改 `not` 元素的值存储在所有有效的偏差。  插入或清除的内部元素，但是，`can` 元素将值存储在给定偏差，因此，迭代器指定的值也可能更改。容器 \(可能必须向上或复制元素在插入之前创建漏洞或在清除后填充一个孔。\)但是，在中，只要其偏差指定有效的元素，deque 迭代器仍然有效。  而且，有效的迭代器保留 dereferencable\-\-可以使用该指定的或修改值访问该元素\-\-只要的偏差与 `end()`返回的迭代器的偏差不相等。  
  
 清除或移除元素调用其存储值的析构函数。  销毁容器清除所有元素。  因此，元素类型为 ref 类的容器元素确保不活动。的容器时间。  注释，但是，容器处理执行销毁 `not` 元素。  
  
## 要求  
 **页眉：** \<cliext\/deque\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [stack](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)