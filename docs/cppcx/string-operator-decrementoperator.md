---
title: "String::operator+ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator+"
dev_langs: 
  - "C++"
ms.assetid: 919b5ba4-3d3b-47a4-9893-9a9ce51fb9c8
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator+ 运算符
指示指定的 [String](../cppcx/platform-string-class.md) 对象是否具有相同的值。  
  
## 语法  
  
```cpp  
  
bool String::operator+( String^ str1,  
                         String^ str2)  
  
```  
  
#### 参数  
 `str1`  
 第一个 `String` 对象。  
  
 `str2`  
 第二个 `String` 对象，其内容将追加到 `str1`。  
  
## 返回值  
 如果 `true` 等于 `str1`，则为 `str2`；否则为 `false`。  
  
## 备注  
 此运算符创建一个 `String^` 对象，用以包含两个操作数中的数据。 在极端性能并不重要时，使用它只是为了方便。 函数中有些对“`+`”的调用可能不明显，但如果在紧凑循环中操作大对象或文本数据，则使用标准 C\+\+ 机制和类型。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)