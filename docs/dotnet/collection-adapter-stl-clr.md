---
title: "collection_adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::collection_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collection_adapter 类 [STL/CLR]"
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# collection_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装了 .NET 一个用作 STL\/CLR 容器的集合。  `collection_adapter` 是描述了一个简单 STL\/CLR 容器对象的模板类。  其包装了基类库 \(BCL\) 接口，并返回用来操作控制序列的一个迭代器对。  
  
## 语法  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### 参数  
 Coll  
 包装集合的类型。  
  
## 专用化  
  
|专用化|说明|  
|---------|--------|  
|IEnumerable|元素的序列。|  
|ICollection|包含了一组元素。|  
|IList|维护一组有序的元素。|  
|IDictionary|维护一个{key，value}键值对。|  
|IEnumerable\<Value\>|输入元素的序列。|  
|ICollection\<Value\>|维护一组输入的元素。|  
|IList\<Value\>|维护一组有序的输入元素。|  
|IDictionary\<Value\>|维护一组输入的{key，value}键值对。|  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[collection\_adapter::difference\_type](../dotnet/collection-adapter-difference-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[collection\_adapter::iterator](../dotnet/collection-adapter-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[collection\_adapter::key\_type](../dotnet/collection-adapter-key-type-stl-clr.md)|字典键的类型。|  
|[collection\_adapter::mapped\_type](../dotnet/collection-adapter-mapped-type-stl-clr.md)|字典值的类型。|  
|[collection\_adapter::reference](../dotnet/collection-adapter-reference-stl-clr.md)|元素的引用的类型。|  
|[collection\_adapter::size\_type](../dotnet/collection-adapter-size-type-stl-clr.md)|两个元素间的带符号距离的类型。|  
|[collection\_adapter::value\_type](../dotnet/collection-adapter-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[collection\_adapter::base](../dotnet/collection-adapter-base-stl-clr.md)|指定包装的 BCL 接口。|  
|[collection\_adapter::begin](../dotnet/collection-adapter-begin-stl-clr.md)|指定受控序列的开头。|  
|[collection\_adapter::collection\_adapter](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|构造适配器对象。|  
|[collection\_adapter::end](../dotnet/collection-adapter-end-stl-clr.md)|指定受控序列的末尾。|  
|[collection\_adapter::size](../dotnet/collection-adapter-size-stl-clr.md)|计算元素的数量。|  
|[collection\_adapter::swap](../dotnet/collection-adapter-swap-stl-clr.md)|交换两个容器的内容。|  
  
|运算符|说明|  
|---------|--------|  
|[collection\_adapter::operator\=](../dotnet/collection-adapter-operator-assign-stl-clr.md)|替换存储 BCL 句柄。|  
  
## 备注  
 使用此模板类作为 STL\/CLR 容器来操作 BCL 容器。  `collection_adapter` 存储句柄到 BCL 接口，从而控制元素的序列。  `collection_adapter` 对象 `X` 返回一对迭代器 `X.begin()` 和 `X.end()`用于按顺序访问元素。  有些专用化还还需要让您编写 `X.size()` 来确定控制序列的长度。  
  
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)   
 [make\_collection](../dotnet/make-collection-stl-clr.md)