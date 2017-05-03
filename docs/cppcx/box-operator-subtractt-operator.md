---
title: "Box::operator T 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator T"
dev_langs: 
  - "C++"
ms.assetid: 7445ef5b-563c-4ff0-829d-f22aa558b5ec
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::operator T 运算符
实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。  
  
## 语法  
  
```cpp  
operator Box<T>^(T valueType);  
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