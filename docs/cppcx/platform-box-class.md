---
title: "Platform::Box 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box"
dev_langs: 
  - "C++"
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Box 类
使值类型（例如 `Windows::Foundation::DateTime`）或标量类型（例如 `int`）能够存储在 `Platform::Object` 类型中。 通常没有必要显式使用 `Box`，因为当你将值类型强制转换为 `Object^` 时会发生隐式装箱：  
  
## 语法  
  
```cpp  
ref class Box abstract;  
```  
  
## 备注  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)   
 [装箱](../cppcx/boxing-c-cx.md)