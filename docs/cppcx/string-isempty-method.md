---
title: "String::IsEmpty 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::IsEmpty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::IsEmpty"
ms.assetid: 4b651706-eace-4055-a694-d9e26a03ce05
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::IsEmpty 方法
指示当前字符串对象是否为空。  
  
## 语法  
  
```cpp  
  
bool IsEmpty()  
```  
  
## 返回值  
 如果当前字符串对象是 `true` 或为空字符串 \(L ""\)，则为 `null`；否则，为 `false`。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)