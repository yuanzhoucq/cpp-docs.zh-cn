---
title: "Box::Box 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::Box"
dev_langs: 
  - "C++"
ms.assetid: 3c4777f0-801c-4b24-9426-6d658dfaecf8
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::Box 构造函数
创建可以封装指定类型的值的 `Box`。  
  
## 语法  
  
```cpp  
Box(T valueArg);  
```  
  
#### 参数  
 `valueArg`  
 要进行装箱的值的类型（例如 `int`、`bool`、`float64`、`DateTime`）。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::Box 类](../cppcx/platform-box-class.md)   
 [装箱](../cppcx/boxing-c-cx.md)