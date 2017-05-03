---
title: "Box::operator Box&lt;volatile T&gt;^ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator Box<volatile T>^"
dev_langs: 
  - "C++"
ms.assetid: 90fffbf6-3429-46d0-bfaf-d99b7f48de6f
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::operator Box&lt;volatile T&gt;^ 运算符
启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。  
  
## 语法  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
```  
  
#### 参数  
 `T`  
 任何枚举类型、值类或值结构。 包括[default 命名空间](../cppcx/default-namespace.md)中的内置类型。  
  
## 返回值  
 表示 ref 类原始装箱值的 `Platform::Box<T>``^` 实例。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::Box 类](../cppcx/platform-box-class.md)   
 [Platform::IBox 接口](../cppcx/platform-ibox-interface.md)   
 [装箱](../cppcx/boxing-c-cx.md)