---
title: "Platform::Collections::BackInsertIterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator 类"
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Collections::BackInsertIterator 类
表示一个迭代器，它插入而非重写元素到有序集合的后端。  
  
## 语法  
  
```  
template <  
   typename T  
>  
class BackInsertIterator : public ::std::iterator< ::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### 参数  
 `T`  
 当前集合中项目的类型。  
  
## 备注  
 BackInsertIterator 类实现 [back\_insert\_iterator 类](../standard-library/back-insert-iterator-class.md) 所要求的规则。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[BackInsertIterator::BackInsertIterator 构造函数](../cppcx/backinsertiterator-backinsertiterator-constructor.md)|初始化 BackInsertIterator 类的新实例。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[BackInsertIterator::operator\* 运算符](../cppcx/backinsertiterator-operator-dereference-operator.md)|检索对当前 BackInsertIterator 的引用。|  
|[BackInsertIterator::operator\+\+ 运算符](../cppcx/backinsertiterator-operator-increment-operator.md)|返回对当前 BackInsertIterator 的引用。 迭代器未经修改。|  
|[BackInsertIterator::operator\= 运算符](../cppcx/backinsertiterator-operator-assign-operator.md)|将指定对象追加到当前有序集合的末尾。|  
  
## 继承层次结构  
 `BackInsertIterator`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)