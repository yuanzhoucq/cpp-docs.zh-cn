---
title: "Platform::Collections::VectorView 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView 类"
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Platform::Collections::VectorView 类
表示可按照索引单独访问的对象的顺序集合的只读视图。 集合中每个对象的类型由模板参数指定。  
  
## 语法  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### 参数  
 `T`  
 `VectorView` 对象中包含的元素的类型。  
  
 `E`  
 使用 `T` 类型的值指定测试相等性的二进制谓词。 默认值为 `std::equal_to<T>`。  
  
## 备注  
 该 `VectorView` 类实现 [Windows::Foundation::Collections::IVectorView\<T\>](http://go.microsoft.com/fwlink/p/?LinkId=262411) 接口并支持标准模板库迭代器。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[VectorView::VectorView 构造函数](../cppcx/vectorview-vectorview-constructor.md)|初始化 VectorView 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[VectorView::First 方法](../cppcx/vectorview-first-method.md)|返回指定 VectorView 中的第一个元素的迭代器。|  
|[VectorView::GetAt 方法](../cppcx/vectorview-getat-method.md)|检索由指定的索引表示的当前 VectorView 的元素。|  
|[VectorView::GetMany 方法](../cppcx/vectorview-getmany-method.md)|从当前 VectorView 检索项序列，从指定索引处开始。|  
|[VectorView::IndexOf 方法](../cppcx/vectorview-indexof-method.md)|在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。|  
|[VectorView::Size 方法](../cppcx/vectorview-size-method.md)|返回当前 VectorView 对象中的元素数目。|  
  
## 继承层次结构  
 `VectorView`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [用 C\+\+ 创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)