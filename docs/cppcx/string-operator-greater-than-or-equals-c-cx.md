---
title: "String::operator&gt;= 运算符 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator>="
ms.assetid: 58cc458f-e82c-4024-b0c5-7f66941bc8aa
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator&gt;= 运算符 (C++/CX)
指示一个字符串对象的值是否大于或等于第二个字符串对象的值。  
  
## 语法  
  
```cpp  
  
bool String::operator>=( String^ str1,  
                         String^ str2)  
  
```  
  
#### 参数  
 `str1`  
 第一个字符串对象。  
  
 `str2`  
 第二个字符串对象。  
  
## 返回值  
 如果 `str1` 的值大于或等于 `str2` 的值，则为 `true`；否则为 `false`。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)