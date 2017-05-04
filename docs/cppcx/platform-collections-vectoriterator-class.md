---
title: "Platform::Collections::VectorIterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator 类"
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Collections::VectorIterator 类
为从 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] IVector 接口派生的对象提供标准模板库迭代器。  
  
 VectorIterator 是存储类型 VectorProxy\<T\> 的元素的代理迭代器。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 语法  
  
```  
template <  
   typename T  
>  
class VectorIterator;  
```  
  
#### 参数  
 `T`  
 VectorIterator 模板类的类型名称。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|描述|  
|--------|--------|  
|`difference_type`|指针差异 \(ptrdiff\_t\)。|  
|`iterator_category`|随机访问迭代器 \(::std::random\_access\_iterator\_tag\) 的类别。|  
|`pointer`|指向实现 VectorIterator 所需的内部类型 Platform::Collections::Details::VectorProxy\<T\> 的指针。|  
|`reference`|对实现 VectorIterator 所需的内部类型 Platform::Collections::Details::VectorProxy\<T\> 的引用。|  
|`value_type`|`T` 类型名称。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[VectorIterator::VectorIterator 构造函数](../cppcx/vectoriterator-vectoriterator-constructor.md)|初始化 VectorIterator 类的新实例。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[VectorIterator::operator\- 运算符](../cppcx/vectoriterator-operator-minus-operator.md)|从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。|  
|[VectorIterator::operator\-\- 运算符](../cppcx/vectoriterator-operator-decrement-operator.md)|递减当前 VectorIterator。|  
|[VectorIterator::operator\!\= 运算符](../cppcx/vectoriterator-operator-inequality-operator.md)|指示当前 VectorIterator 是否不等于指定的 VectorIterator。|  
|[VectorIterator::operator\* 运算符](../cppcx/vectoriterator-operator-dereference-operator.md)|检索对当前 VectorIterator 指定的元素的引用。|  
|[VectorIterator::operatorOperator](../cppcx/vectoriterator-operatoroperator.md)|检索对属于当前 VectorIterator 的指定偏移量的元素的引用。|  
|[\(DELETE\) VectorIterator::operator\+ 运算符](http://msdn.microsoft.com/zh-cn/b0b1af2c-e2a8-4876-99dc-7351bfc46ce4)|返回引用偏移指定 VectorIterator 指定偏移量处的元素的 VectorIterator。|  
|[VectorIterator::operator\+\+ 运算符](../cppcx/vectoriterator-operator-increment-operator.md)|递增当前 VectorIterator。|  
|[VectorIterator::operator\+\= 运算符](../cppcx/vectoriterator-operator-plus-assign-operator.md)|按指定偏移量递增当前 VectorIterator。|  
|[VectorIterator::operator\< 运算符](../cppcx/vectoriterator-operator-less-than-operator.md)|指示当前 VectorIterator 是否小于指定的 VectorIterator。|  
|[VectorIterator::operator\<\= 运算符](../cppcx/vectoriterator-operator-less-than-or-equals-operator.md)|指示当前 VectorIterator 是否小于或等于指定的 VectorIterator。|  
|[VectorIterator::operator\-\= 运算符](../cppcx/vectoriterator-operator-subtract-assign-operator.md)|按指定偏移量递减当前 VectorIterator。|  
|[VectorIterator::operator\=\= 运算符](../cppcx/vectoriterator-operator-equality-operator.md)|指示当前 VectorIterator 是否等于指定的 VectorIterator。|  
|[VectorIterator::operator\> 运算符](../cppcx/vectoriterator-operator-greater-than-operator.md)|指示当前 VectorIterator 是否大于指定的 VectorIterator。|  
|[VectorIterator::operator\-\> 运算符](../cppcx/vectoriterator-operator-arrow-operator.md)|检索当前 VectorIterator 引用的元素的地址。|  
|[VectorIterator::operator\>\= 运算符](../cppcx/vectoriterator-operator-greater-than-or-equal-operator.md)|指示当前 VectorIterator 是否大于或等于指定的 VectorIterator。|  
  
## 继承层次结构  
 `VectorIterator`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)