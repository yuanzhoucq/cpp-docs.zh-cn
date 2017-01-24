---
title: "vector (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/vector> 标头 [STL/CLR]"
  - "<vector> 标头 [STL/CLR]"
  - "vector 类 [STL/CLR]"
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类描述对象具有控件随机访问更改长度元素的序列。  使用容器 `vector` 管理元素序列作为存储连续块。  块实现为增大按需的数组。  
  
 在如下解释，`GValue` 与 `Value` 相同，除非是后者 ref 类型，在这种情况下，它是 `Value^`条件下。  
  
## 语法  
  
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
  
#### 参数  
 值  
 受控序列中的元素的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[vector::const\_iterator](../dotnet/vector-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[vector::const\_reference](../dotnet/vector-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[vector::const\_reverse\_iterator](../dotnet/vector-const-reverse-iterator-stl-clr.md)|常数进行反向迭代器类型的控制的序列。|  
|[vector::difference\_type](../dotnet/vector-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[vector::generic\_container](../dotnet/vector-generic-container-stl-clr.md)|泛型接口的类型容器中。|  
|[vector::generic\_iterator](../dotnet/vector-generic-iterator-stl-clr.md)|一迭代器的类型通用接口的容器的。|  
|[vector::generic\_reverse\_iterator](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|一进行反向迭代器的类型泛型接口的容器的。|  
|[vector::generic\_value](../dotnet/vector-generic-value-stl-clr.md)|的元素类型泛型接口的容器的。|  
|[vector::iterator](../dotnet/vector-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[vector::reference](../dotnet/vector-reference-stl-clr.md)|元素的引用的类型。|  
|[vector::reverse\_iterator](../dotnet/vector-reverse-iterator-stl-clr.md)|一进行反向迭代器类型的控制的序列。|  
|[vector::size\_type](../dotnet/vector-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[vector::value\_type](../dotnet/vector-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[vector::assign](../dotnet/vector-assign-stl-clr.md)|替换任何元素。|  
|[vector::at](../dotnet/vector-at-stl-clr.md)|访问元素中的指定位置。|  
|[vector::back](../dotnet/vector-back-stl-clr.md)|访问最后一个元素。|  
|[vector::begin](../dotnet/vector-begin-stl-clr.md)|指定受控序列的开头。|  
|[vector::capacity](../dotnet/vector-capacity-stl-clr.md)|报告为容器分配的存储大小。|  
|[vector::clear](../dotnet/vector-clear-stl-clr.md)|移除所有元素。|  
|[vector::empty](../dotnet/vector-empty-stl-clr.md)|测试元素不存在。|  
|[vector::end](../dotnet/vector-end-stl-clr.md)|指定受控序列的末尾。|  
|[vector::erase](../dotnet/vector-erase-stl-clr.md)|移除指定位置处的元素。|  
|[vector::front](../dotnet/vector-front-stl-clr.md)|访问第一个元素。|  
|[vector::insert](../dotnet/vector-insert-stl-clr.md)|将元素中的指定位置。|  
|[vector::pop\_back](../dotnet/vector-pop-back-stl-clr.md)|移除最后一个元素。|  
|[vector::push\_back](../dotnet/vector-push-back-stl-clr.md)|添加一个新的元素之前。|  
|[vector::rbegin](../dotnet/vector-rbegin-stl-clr.md)|指定反转的受控序列的开头。|  
|[vector::rend](../dotnet/vector-rend-stl-clr.md)|指定反转的受控序列的末尾。|  
|[vector::reserve](../dotnet/vector-reserve-stl-clr.md)|确保容器的最小的增加容量。|  
|[vector::resize](../dotnet/vector-resize-stl-clr.md)|更改元素的数量。|  
|[vector::size](../dotnet/vector-size-stl-clr.md)|计算元素的数量。|  
|[vector::swap](../dotnet/vector-swap-stl-clr.md)|交换两个容器的内容。|  
|[vector::to\_array](../dotnet/vector-to-array-stl-clr.md)|复制控件序列到新数组。|  
|[vector::vector](../dotnet/vector-vector-stl-clr.md)|构造容器对象。|  
  
|Property|说明|  
|--------------|--------|  
|[vector::back\_item](../dotnet/vector-back-item-stl-clr.md)|访问最后一个元素。|  
|[vector::front\_item](../dotnet/vector-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|说明|  
|---------|--------|  
|[vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)|控件替换序列。|  
|[vector::operator](../dotnet/vector-operator-stl-clr.md)|访问元素中的指定位置。|  
|[operator\!\= \(vector\)](../dotnet/operator-inequality-vector-stl-clr.md)|确定 `vector` 对象是否与另一 `vector` 对象不等于。|  
|[operator\< \(vector\)](../dotnet/operator-less-than-vector-stl-clr.md)|确定 `vector` 对象是否大于另一 `vector` 对象很低。|  
|[operator\<\= \(vector\)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|确定 `vector` 对象是否小于或等于另一个 `vector` 对象。|  
|[operator\=\= \(vector\)](../dotnet/operator-equality-vector-stl-clr.md)|确定 `vector` 对象是否与另一 `vector` 对象相同。|  
|[operator\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)|确定 `vector` 对象是否大于另一 `vector` 对象操作。|  
|[operator\>\= \(vector\)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|确定 `vector` 对象是否大于或等于另一个 `vector` 对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过序列元素。|  
|<xref:System.Collections.ICollection>|维护元素组。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列通过输出元素。|  
|<xref:System.Collections.Generic.ICollection%601>|打印维护元素组。|  
|<xref:System.Collections.Generic.IList%601>|打印 maintain 排序元素组。|  
|IVector\<Value\>|维护型容器。|  
  
## 备注  
 对象分配并通过的一些 `Value` 元素控制，增大在需要序列中未使用助记域。  根据发生，在这种情况下成本追加新的元素、常数的时间。  换言之，因为控制序列的长度越大，成本添加元素末尾未提高，平均。  因此，矢量是基础容器的理想候选项模板类的 [stack](../dotnet/stack-stl-clr.md)。  
  
 `vector` 支持随机访问迭代器，这意味着可以引用元素直接为其数字位置，从零开始计数第一个 \(\) 元素的之前，最后 \(返回\) [vector::size](../dotnet/vector-size-stl-clr.md)元素的`() - 1`。  同时也意味着矢量是基础容器的理想候选项模板类的 [priority\_queue](../dotnet/priority-queue-stl-clr.md)。  
  
 矢量迭代器存储处理为其关联矢量对象，以及其选定元素的偏差。  可以只使用迭代器与它们关联的容器对象。  向量元素那样偏重与其位置。  
  
 插入或清除元素可以更改元素的值存储在特定位置，所以，迭代器指定的值也可能更改。容器 \(可能必须向上或复制元素在插入之前创建漏洞或在清除后填充一个孔。\)但是，在中，只要其偏差在范围 `[0,` [vector::size](../dotnet/vector-size-stl-clr.md)`()]`，矢量迭代器保持有效。  而且，有效的迭代器保留 dereferencable\-\-可以使用该指定的或修改值访问该元素\-\-只要的偏差不等于 `size()`。  
  
 清除或移除元素调用其存储值的析构函数。  销毁容器清除所有元素。  因此，元素类型为 ref 类的容器元素确保不活动。的容器时间。  注释，但是，容器处理执行销毁 `not` 元素。  
  
## 要求  
 **页眉：** \<cliext\/矢量\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [stack](../dotnet/stack-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)