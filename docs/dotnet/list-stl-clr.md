---
title: "list (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/list> 标头 [STL/CLR]"
  - "<list> 标头 [STL/CLR]"
  - "list 类 [STL/CLR]"
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# list (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制双向访问的变长元素序列的对象。  使用容器 `list` 管理元素序列，就像节点双向链接列表，每个都存储的一个元素。  
  
 在下面的解释中，`GValue` 与 `Value` 相同，除非后者是 ref （引用）类型，在这种情况下，它是 `Value^`。  
  
## 语法  
  
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
  
#### 参数  
 值  
 受控序列中的元素的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[list::const\_iterator](../dotnet/list-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[list::const\_reference](../dotnet/list-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[list::const\_reverse\_iterator](../dotnet/list-const-reverse-iterator-stl-clr.md)|这种类型的常量为受控序列存储迭代器。|  
|[list::difference\_type](../dotnet/list-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[list::generic\_container](../dotnet/list-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[list::generic\_iterator](../dotnet/list-generic-iterator-stl-clr.md)|有关容器的泛型接口的迭代器的类型。|  
|[list::generic\_reverse\_iterator](../dotnet/list-generic-reverse-iterator-stl-clr.md)|与容器的泛型接口一起使用的迭代器的类型。|  
|[list::generic\_value](../dotnet/list-generic-value-stl-clr.md)|有关容器的泛型接口的元素的类型。|  
|[list::iterator](../dotnet/list-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[list::reference](../dotnet/list-reference-stl-clr.md)|元素的引用的类型。|  
|[list::reverse\_iterator](../dotnet/list-reverse-iterator-stl-clr.md)|受控序列的反转迭代器的类型。|  
|[list::size\_type](../dotnet/list-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[list::value\_type](../dotnet/list-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[list::assign](../dotnet/list-assign-stl-clr.md)|替换任何元素。|  
|[list::back](../dotnet/list-back-stl-clr.md)|访问最后一个元素。|  
|[list::begin](../dotnet/list-begin-stl-clr.md)|指定受控序列的开头。|  
|[list::clear](../dotnet/list-clear-stl-clr.md)|移除所有元素。|  
|[list::empty](../dotnet/list-empty-stl-clr.md)|测试元素是否存在。|  
|[list::end](../dotnet/list-end-stl-clr.md)|指定受控序列的末尾。|  
|[list::erase](../dotnet/list-erase-stl-clr.md)|移除指定位置处的元素。|  
|[list::front](../dotnet/list-front-stl-clr.md)|访问第一个元素。|  
|[list::insert](../dotnet/list-insert-stl-clr.md)|添加元素到一个指定位置处。|  
|[list::list](../dotnet/list-list-stl-clr.md)|构造容器对象。|  
|[list::merge](../dotnet/list-merge-stl-clr.md)|合并两个有序受控序列。|  
|[list::pop\_back](../dotnet/list-pop-back-stl-clr.md)|移除最后的元素。|  
|[list::pop\_front](../dotnet/list-pop-front-stl-clr.md)|移除第一个元素。|  
|[list::push\_back](../dotnet/list-push-back-stl-clr.md)|添加新的末尾元素。|  
|[list::push\_front](../dotnet/list-push-front-stl-clr.md)|添加新的第一个元素。|  
|[list::rbegin](../dotnet/list-rbegin-stl-clr.md)|指定反转的受控序列的开头。|  
|[list::remove](../dotnet/list-remove-stl-clr.md)|移除具有指定键值的元素。|  
|[list::remove\_if](../dotnet/list-remove-if-stl-clr.md)|移除通过指定测试的元素。|  
|[list::rend](../dotnet/list-rend-stl-clr.md)|指定反转的受控序列的末尾。|  
|[list::resize](../dotnet/list-resize-stl-clr.md)|更改元素的数量。|  
|[list::reverse](../dotnet/list-reverse-stl-clr.md)|对受控序列进行反转。|  
|[list::size](../dotnet/list-size-stl-clr.md)|计算元素的数量。|  
|[list::sort](../dotnet/list-sort-stl-clr.md)|对受控序列进行排序。|  
|[list::splice](../dotnet/list-splice-stl-clr.md)|节点之间的 Restitches 链接。|  
|[list::swap](../dotnet/list-swap-stl-clr.md)|交换两个容器的内容。|  
|[list::to\_array](../dotnet/list-to-array-stl-clr.md)|复制控制序列到新数组。|  
|[list::unique](../dotnet/list-unique-stl-clr.md)|移除通过指定测试的相邻元素。|  
  
|Property|说明|  
|--------------|--------|  
|[list::back\_item](../dotnet/list-back-item-stl-clr.md)|访问最后一个元素。|  
|[list::front\_item](../dotnet/list-front-item-stl-clr.md)|访问第一个元素。|  
  
|运算符|说明|  
|---------|--------|  
|[list::operator\=](../dotnet/list-operator-assign-stl-clr.md)|替换控件序列。|  
|[operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)|确定 `list` 对象是否等与不等于另一 `list` 对象。|  
|[operator\< \(list\)](../dotnet/operator-less-than-list-stl-clr.md)|确定 `list` 对象是否小于另一 `list` 对象。|  
|[operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)|确定一个 `list` 对象是否小于或等于另一个`list`对象。|  
|[operator\=\= \(list\)](../dotnet/operator-equality-list-stl-clr.md)|确定 `list` 对象是否等于另一 `list` 对象。|  
|[operator\> \(list\)](../dotnet/operator-greater-than-list-stl-clr.md)|确定 `list` 对象是否大于另一 `list` 对象。|  
|[operator\>\= \(list\)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|确定一个 `list` 对象是否大于或等于另一个`list`对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|元素的序列。|  
|<xref:System.Collections.ICollection>|维护元素组。|  
|<xref:System.Collections.Generic.IEnumerable%601>|输入元素的序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护输入元素组。|  
|IList\<Value\>|维护泛型容器。|  
  
## 备注  
 对象将它控制序列中未使用助记域，当一双向链接列表的各个节点。  它通过修改节点之间的链接从不重新排列元素，通过复制一节点内容到另一个。  这表示您可以自由插入和移除元素，而不干扰的其余元素。  因此，该列表为基础容器的理想候选项模板类[queue](../dotnet/queue-stl-clr.md) 或模板类[stack](../dotnet/stack-stl-clr.md)。  
  
 `list`集合支持双向迭代器，这意味着可以单步执行到给定的相邻元素迭代器指定控制在序列中的元素。  特定头节点对应于 [list::end](../dotnet/list-end-stl-clr.md)`()`返回的迭代器。  如果有，可以减小此迭代器达到控制序列中的最后一个元素。  您可以将列表迭代器增加到头节点，则将与 `end()`比较。  但是，您无法取消引用 `end()`返回的迭代器。  
  
 注意不可以直接引用基于数字的列表集合的元素\-\-这要求一个随机访问迭代器。  因此列表为 `not` 用作模板类的 [priority\_queue](../dotnet/priority-queue-stl-clr.md)基础容器。  
  
 列表迭代器存储其关列表合节点的句柄，而后者存储其关联的容器的句柄。  只可以在与它们关联的容器对象上使用迭代器。  只要关联列表节点与某些列表关联，迭代器列表保持有效。  而且，有效的迭代器是可重复引用的\-\-可以用来访问或修改指定的元素值\-\-只要它不等于 `end()`。  
  
 调用析构函数清除或移除元素的存储值。  销毁容器会清除所有元素。  因此，元素类型为参考类的容器确保元素存在容器内。  但是，注意容器的处理执行销毁 `not` 元素。  
  
## 要求  
 **标头:** \<cliext\/list\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [stack](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)