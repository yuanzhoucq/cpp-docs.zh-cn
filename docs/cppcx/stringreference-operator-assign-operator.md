---
title: "StringReference::operator= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::operator="
dev_langs: 
  - "C++"
ms.assetid: 03a33467-d65f-4508-bcb4-17d7cc99398f
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# StringReference::operator= 运算符
将指定对象分配给当前 `StringReference` 对象。  
  
## 语法  
  
```cpp  
  
   StringReference& operator=(const StringReference& __fstrArg);  
  
StringReference& operator=(const ::default::char16* __strArg);  
  
```  
  
#### 参数  
 `__fstrArg`  
 用于初始化当前 `StringReference` 对象的 `StringReference` 对象的地址。  
  
 `__strArg`  
 指向用于初始化当前 `StringReference` 对象的 char16 值数组的指针。  
  
## 返回值  
 对类型为 `StringReference` 的对象的引用。  
  
## 备注  
 由于 `StringReference` 是标准 C\+\+ 类而不是 ref 类，因此，它不出现在**“对象浏览器”**中。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::StringReference 类](../cppcx/platform-stringreference-class.md)