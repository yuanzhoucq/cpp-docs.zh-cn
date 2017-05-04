---
title: "Platform::Collections::VectorViewIterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator 类"
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Collections::VectorViewIterator 类
为从 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] `IVectorView` 接口派生的对象提供标准模板库迭代器。  
  
 `ViewVectorIterator` 是存储 `VectorProxy<T>` 类型的元素的代理迭代器。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 语法  
  
```  
template <  
   typename T  
>  
class VectorViewIterator;  
```  
  
#### 参数  
 `T`  
 VectorViewIterator 模板类的类型名称。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|描述|  
|--------|--------|  
|`difference_type`|指针差异 \(ptrdiff\_t\)。|  
|`iterator_category`|随机访问迭代器 \(::std::random\_access\_iterator\_tag\) 的类别。|  
|`pointer`|指向实现 VectorViewIterator 所需的内部类型的指针。|  
|`reference`|对实现 VectorViewIterator 所需的内部类型的引用。|  
|`value_type`|`T` 类型名称。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[VectorViewIterator::VectorViewIterator 构造函数](../cppcx/vectorviewiterator-vectorviewiterator-constructor.md)|初始化 VectorViewIterator 类的新实例。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[VectorViewIterator::operator\- 运算符](../cppcx/vectorviewiterator-operator-minus-operator.md)|从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。|  
|[VectorViewIterator::operator\-\- 运算符](../cppcx/vectorviewiterator-operator-decrement-operator.md)|递减当前 VectorViewIterator。|  
|[VectorViewIterator::operator\!\= 运算符](../cppcx/vectorviewiterator-operator-inequality-operator.md)|指示当前 VectorViewIterator 是否不等于指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\* 运算符](../cppcx/vectorviewiterator-operator-dereference-operator.md)|检索对当前 VectorViewIterator 指定的元素的引用。|  
|[VectorViewIterator::operatorOperator](../cppcx/vectorviewiterator-operatoroperator.md)|检索对偏移当前 VectorViewIterator 指定量的元素的引用。|  
|[VectorViewIterator::operator\+ 运算符](../cppcx/vectorviewiterator-operator-plus-operator.md)|返回引用偏移指定 VectorViewIterator 指定偏移量处的元素的 VectorViewIterator。|  
|[VectorViewIterator::operator\+\+ 运算符](../cppcx/vectorviewiterator-operator-increment-operator.md)|递增当前 VectorViewIterator。|  
|[VectorViewIterator::operator\+\= 运算符](../cppcx/vectorviewiterator-operator-plus-assign-operator.md)|按指定偏移量递增当前 VectorViewIterator。|  
|[VectorViewIterator::operator\< 运算符](../cppcx/vectorviewiterator-operator-less-than-operator.md)|指示当前 VectorViewIterator 是否小于指定 VectorViewIterator。|  
|[VectorViewIterator::operator\<\= 运算符](../cppcx/vectorviewiterator-operator-less-than-or-equals-operator.md)|指示当前 VectorViewIterator 是否小于或等于指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\-\= 运算符](../cppcx/vectorviewiterator-operator-subtract-assign-operator.md)|按指定偏移量递减当前 VectorViewIterator。|  
|[VectorViewIterator::operator\=\= 运算符](../cppcx/vectorviewiterator-operator-equality-operator.md)|指示当前 VectorViewIterator 是否等于指定 VectorViewIterator。|  
|[VectorViewIterator::operator\> 运算符](../cppcx/vectorviewiterator-operator-greater-than-operator.md)|指示当前 VectorViewIterator 是否大于指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\-\> 运算符](../cppcx/vectorviewiterator-operator-arrow-operator.md)|检索当前 VectorViewIterator 引用的元素的地址。|  
|[VectorViewIterator::operator\>\= 运算符](../cppcx/vectorviewiterator-operator-greater-than-or-equals-operator.md)|指示当前 VectorViewIterator 是否大于或等于指定的 VectorViewIterator。|  
  
## 继承层次结构  
 `VectorViewIterator`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)