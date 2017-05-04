---
title: "String::Equals 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Equals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Equals"
ms.assetid: b0c78419-242d-4d38-93e3-ff2818412624
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Equals 方法
指示指定的字符串是否具有和当前对象相同的值。  
  
## 语法  
  
```cpp  
  
bool String::Equals(Object^ str);  
  
bool String::Equals(String^ str);  
  
```  
  
#### 参数  
 `str`  
 要比较的对象。  
  
## 返回值  
 如果 `true` 等于当前对象，则为 `str`，否则为 `false`。  
  
## 备注  
 此方法与 [String::CompareOrdinal 方法](../cppcx/string-compareordinal-method.md)等效。 在第一个重载中，`str` 参数应能够转换为 String^ 对象。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)