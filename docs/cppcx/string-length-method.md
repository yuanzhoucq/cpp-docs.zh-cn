---
title: "String::Length 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Length"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Length"
ms.assetid: 92376897-1bf2-4b7a-9298-d2d3f05d8d6b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Length 方法
检索当前字符串对象中的字符数。  
  
## 语法  
  
```cpp  
  
unsigned int Length()  
```  
  
## 返回值  
 当前字符串对象中的字符数。  
  
## 备注  
 一个没有字符的字符串的长度为零。 以下字符串的长度为 5：  
  
```  
  
String^ str = "Hello";  
int len = str->Length(); //len = 5  
```  
  
 [String::Data 方法](../cppcx/string-data-method.md) 返回的字符数组具有一个附加字符，是终止 NULL 或“\\0”。 该字符也是两个字节长。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)