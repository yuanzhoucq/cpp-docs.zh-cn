---
title: "Platform::Collections::InputIterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator 类"
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Collections::InputIterator 类
为从 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 派生的集合提供标准模板库 InputIterator。  
  
## 语法  
  
```  
template <  
   typename X  
>  
class InputIterator;  
```  
  
#### 参数  
 `X`  
 InputIterator 模板类的类型名称。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|描述|  
|--------|--------|  
|`difference_type`|指针差异 \(ptrdiff\_t\)。|  
|`iterator_category`|输入迭代器 \(::std::input\_iterator\_tag\) 的类别。|  
|`pointer`|指向 `const``X` 的指针|  
|`reference`|对 `const` `X` 的引用|  
|`value_type`|`X` 类型名称。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[InputIterator::InputIterator 构造函数](../cppcx/inputiterator-inputiterator-constructor.md)|初始化 InputIterator 类的新实例。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[InputIterator::operator\!\= 运算符](../cppcx/inputiterator-operator-inequality-operator.md)|指示当前 InputIterator 是否不等于指定的 InputIterator。|  
|[InputIterator::operator\* 运算符](../cppcx/inputiterator-operator-decrementoperator.md)|检索对当前 InputIterator 指定的元素的引用。|  
|[InputIterator::operator\+\+ 运算符](../cppcx/inputiterator-operator-increment-operator.md)|递增当前 InputIterator。|  
|[InputIterator::operator\=\= 运算符](../cppcx/inputiterator-operator-equality-operator.md)|指示当前 InputIterator 是否等于指定的 InputIterator。|  
|[InputIterator::operator\-\> 运算符](../cppcx/inputiterator-operator-arrow-operator.md)|检索当前 InputIterator 引用的元素的地址。|  
  
## 继承层次结构  
 `InputIterator`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)