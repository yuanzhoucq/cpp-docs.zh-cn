---
title: "begin 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin 函数"
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# begin 函数
返回指向指定接口参数所访问的集合开头的迭代器。  
  
## 语法  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### 参数  
 `T`  
 模板类型参数。  
  
 `v`  
 由 IVector\<T\> 或 IVectorView\<T\> 接口访问的 Vector\<T\> 或 VectorView\<T\> 对象的集合。  
  
 `i`  
 IIterable\<T\> 接口访问的任意 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]对象的集合。  
  
## 返回值  
 指向集合开头的迭代器。  
  
## 备注  
 前两个模板函数返回迭代器，第三个模板函数返回输入迭代器。  
  
 begin 返回的 VectorIterator 对象是存储 VectorProxy\<T\> 类型的元素的代理迭代器。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Windows::Foundation::Collections  
  
## 请参阅  
 [Windows::Foundation::Collections 命名空间](../cppcx/windows-foundation-collections-namespace-c-cx.md)