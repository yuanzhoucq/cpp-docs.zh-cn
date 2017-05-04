---
title: "StringReference::StringReference 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::StringReference"
dev_langs: 
  - "C++"
ms.assetid: 87dd9201-e638-4913-b37c-7091ae3f91ea
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# StringReference::StringReference 构造函数
初始化 `StringReference` 类的新实例。  
  
## 语法  
  
```cpp  
  
    StringReference();  
  
   StringReference(const StringReference& __fstrArg)  
  
StringReference(const ::default::char16* __strArg)  
  
StringReference(const ::default::char16* __strArg, size_t __lenArg)  
```  
  
#### 参数  
 `__fstrArg`  
 其数据用于初始化新实例的 `StringReference`。  
  
 `__strArg`  
 指向用于初始化新实例的 char16 值数组的指针。  
  
 `__lenArg`  
 `__strArg` 中的元素数。  
  
## 备注  
 此构造函数的第一个版本是默认构造函数。 第二个版本从 `StringReference` 参数指定的对象初始化新 `__fstrArg` 实例类。 第三和第四个重载从 char16 值数组初始化新 `StringReference` 实例。 char16 表示 16 位 UNICODE 文本字符。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::StringReference 类](../cppcx/platform-stringreference-class.md)