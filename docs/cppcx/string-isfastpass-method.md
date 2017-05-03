---
title: "String::IsFastPass 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::IsFastPass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::IsFastPass"
ms.assetid: 0a8c2db7-e44f-45fe-9570-3dc82fbbacdd
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::IsFastPass 方法
指示当前 String 对象是否参与*快速传递* 操作。 在快速传递操作中，将挂起引用计数。  
  
## 语法  
  
```cpp  
  
bool IsFastPass();  
```  
  
## 返回值  
 如果当前 String 对象已快速传递，则为 `true`；否则为 `false`。  
  
## 备注  
 在引用计数对象作为参数并且被调用的函数只读取该对象的函数调用中，编译器可以安全地挂起引用计数并改进调用性能。 没有可供您的代码对此属性执行的任何操作。 系统处理所有详细信息。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)