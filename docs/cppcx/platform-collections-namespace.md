---
title: "Platform::Collections 命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Collections 命名空间"
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Collections 命名空间
Platform::Collection 命名空间包含 `Map`、`MapView`、`Vector` 和 `VectorView` 类。 这些类是在 [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) 命名空间中定义的对应接口的具体实现。 具体集合类型在 ABI 之间是不可移植的（例如，当 Javascript 或 C\# 程序调用到 C\+\+ 组件时）时，但它们可以隐式转换为其相应的接口类型。 例如，如果你实现了一个填充并返回集合的公共方法，则使用 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 在内部实现该集合并使用 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 作为返回类型。 有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)和[用 C\+\+ 创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)。  
  
 可以从 [std::vector](../Topic/vector%20Class%201.md) 构造 Platform::Collections::Vector，从 [std::map](../cppcx/platform-collections-map-class.md) 构造 [Platform::Collections::Map](../standard-library/map-class.md)。  
  
 此外，Platform::Collection 命名空间提供对于回插和输入迭代器以及 `Vector` 和 `VectorView` 迭代器的支持。  
  
 必须包括 \(`#include`\) collection.h 标头才能使用 Platform::Collection 命名空间中的类型。  
  
## 语法  
  
```cpp  
  
#include <collection.h>  
using namespace Platform::Collection;  
```  
  
## 成员  
 此命名空间包含以下成员。  
  
|名称|说明|  
|--------|--------|  
|[Platform::Collections::BackInsertIterator 类](../cppcx/platform-collections-backinsertiterator-class.md)|表示在集合末尾插入一个元素的迭代器。|  
|[Platform::Collections::InputIterator 类](../cppcx/platform-collections-inputiterator-class.md)|表示在集合开头插入一个元素的迭代器。|  
|[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)|表示键访问的键值对的可修改集合。 类似于 [std::map](../standard-library/map-class.md)。|  
|[Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)|表示键访问的键值对的只读集合。|  
|[Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)|表示元素的可修改序列。 类似于 [std::vector](../Topic/vector%20Class%201.md)。|  
|[Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)|表示遍历 `Vector` 集合的迭代器。|  
|[Platform::Collections::VectorView 类](../cppcx/platform-collections-vectorview-class.md)|表示元素的只读序列。|  
|[Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)|表示遍历 `VectorView` 集合的迭代器。|  
  
## 继承层次结构  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)  
  
## 要求  
 **元数据：**platform.winmd  
  
 **命名空间：**Platform::Collections  
  
 **编译器选项：**\/ZW  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)