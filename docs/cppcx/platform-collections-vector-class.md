---
title: "Platform::Collections::Vector 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector 类 (C++/Cx)"
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# Platform::Collections::Vector 类
表示可按照索引单独访问的对象的有序集合。  
  
## 语法  
  
```  
template <typename T, typename E>  
   ref class Vector sealed;  
```  
  
#### 参数  
 `T`  
 向量对象中包含的元素的类型。  
  
 `E`  
 使用 `T` 类型的值指定测试相等性的二进制谓词。 默认值为 `std::equal_to<T>`。  
  
## 备注  
 允许的类型包括：  
  
1.  整数  
  
2.  接口类 ^  
  
3.  公共 ref 类  
  
4.  value struct  
  
5.  公共枚举类  
  
 Vector 类是 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 接口的 C\+\+ 具体实现。  
  
 如果您尝试在公共返回值或参数中使用 Vector 类型，则将引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 可修复该错误。 有关更多信息，请参见[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[Vector::Vector 构造函数](../cppcx/vector-vector-constructor.md)|初始化 Vector 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[Vector::Append 方法](../cppcx/vector-append-method.md)|在当前向量中的最后一项后插入指定项。|  
|[Vector::Clear 方法](../cppcx/vector-clear-method.md)|删除当前向量中的所有元素。|  
|[Vector::First 方法](../cppcx/vector-first-method.md)|返回指定该向量中第一个元素的迭代器。|  
|[Vector::GetAt 方法](../cppcx/vector-getat-method.md)|检索由指定索引标识的当前向量的元素。|  
|[Vector::GetMany 方法](../cppcx/vector-getmany-method.md)|从指定索引处开始，检索当前向量中的项目序列。|  
|[Vector::GetView 方法](../cppcx/vector-getview-method.md)|返回向量的只读视图，即 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|  
|[Vector::IndexOf 方法](../cppcx/vector-indexof-method.md)|在当前向量中搜索指定项，如果找到，则返回该项的索引。|  
|[Vector::InsertAt 方法](../cppcx/vector-insertat-method.md)|在当前 Vector 中由指定的索引标识的元素后面插入指定的项。|  
|[Vector::ReplaceAll 方法](../cppcx/vector-replaceall-method.md)|删除当前向量中的元素，然后插入来自指定数组的元素。|  
|[Vector::RemoveAt 方法](../cppcx/vector-removeat-method.md)|从当前向量删除指定索引标识的元素。|  
|[Vector::RemoveAtEnd 方法](../cppcx/vector-removeatend-method.md)|删除当前矢量末尾的元素。|  
|[Vector::SetAt 方法](../cppcx/vector-setat-method.md)|将指定值分配给当前向量中指定索引标识的元素。|  
|[Vector::Size 方法](../cppcx/vector-size-method.md)|返回当前向量对象中的元素数目。|  
  
### 事件  
  
|||  
|-|-|  
|名称|说明|  
|事件 [Windows::Foundation::Collection::VectorChangedEventHandler\<T\>^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|当向量更改时发生。|  
  
## 继承层次结构  
 `Vector`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [用 C\+\+ 创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)