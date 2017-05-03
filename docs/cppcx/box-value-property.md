---
title: "Box::Value 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::Value"
dev_langs: 
  - "C++"
ms.assetid: f456b105-6c14-4737-8c27-ad47d1eabd32
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::Value 属性
返回在 `Box` 对象中封装的值。  
  
## 语法  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
## 返回值  
 返回具有和其装箱前最初具有的类型相同类型的装箱值。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::Box 类](../cppcx/platform-box-class.md)   
 [装箱](../cppcx/boxing-c-cx.md)