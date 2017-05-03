---
title: "String::Concat 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Concat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Concat"
ms.assetid: 68052d22-3df0-4777-828d-fc3a8e8a3ab7
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Concat 方法
连接两个字符串对象的值。  
  
## 语法  
  
```cpp  
  
String^ Concat( String ^ str1,   
String ^ str2  
)  
  
```  
  
#### 参数  
 `str1`  
 第一个字符串对象或 `null`。  
  
 `str2`  
 第二个字符串对象或 `null`。  
  
## 返回值  
 其值为 `str1` 与 `str2` 的值相连的新 String^ 对象。  
  
 如果 `str1` 是 `null` 而 `str2` 不是，则返回 `str1` 。 如果 `str2` 是 `null` 而 `str1` 不是，则返回 `str2`。 如果 `str1` 和 `str2` 都是 `null`，则返回空字符串 \(L ""\)。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)