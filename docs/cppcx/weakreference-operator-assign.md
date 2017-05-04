---
title: "WeakReference::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::operator="
ms.assetid: 20b034d1-8f4f-46ae-81f0-73b76599f86b
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::operator=
给 WeakReference 赋值。  
  
## 语法  
  
```cpp  
WeakReference& operator=(decltype(__nullptr));  
  
WeakReference& operator=(const WeakReference& __otherArg);  
  
WeakReference& operator=(WeakReference&& __otherArg);  
  
WeakReference& operator=(const volatile ::Platform::Object^ const __otherArg);  
  
```  
  
## 备注  
 使用上面列表中的最后一个重载，可以向 WeakReference 变量分配 ref 类。 在此情况下，ref 类向下转换到 [Platform::Object](../cppcx/platform-object-class.md)^。 稍后，可通过将原始类型指定为 [WeakReference::Resolve\<T\>](../cppcx/weakreference-resolve-method-platform-namespace.md) 成员函数中类型形参的实参来还原原始类型。  
  
## 要求  
 Windows 8.0 或更高版本  
  
## 请参阅  
 [Platform::WeakReference 类](../cppcx/platform-weakreference-class.md)