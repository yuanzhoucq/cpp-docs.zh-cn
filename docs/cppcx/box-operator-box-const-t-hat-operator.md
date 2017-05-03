---
title: "Box::operator Box&lt;const T&gt;^ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator Box<const T>^"
dev_langs: 
  - "C++"
ms.assetid: c43a2e8f-7e9d-4587-960f-1bab48923f82
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::operator Box&lt;const T&gt;^ 运算符
实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。  
  
## 语法  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
#### 参数  
 `T`  
 任何值类、值结构或枚举类型。 包括[default 命名空间](../cppcx/default-namespace.md)中的内置类型。  
  
## 返回值  
 表示 ref 类原始装箱值的 `Platform::Box<T>``^` 实例。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::Box 类](../cppcx/platform-box-class.md)   
 [Platform::IBox 接口](../cppcx/platform-ibox-interface.md)