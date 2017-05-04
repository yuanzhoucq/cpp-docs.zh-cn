---
title: "String::Data 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Data"
ms.assetid: 9be4e015-dfb8-431e-a252-8498bd833f03
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Data 方法
以 C 样式 `char16` \(`wchar_t`\) 元素数组的形式返回指向对象的数据缓冲区开头的指针。  
  
## 语法  
  
```  
const char16* Data()  
```  
  
## 返回值  
 指向 Unicode 字符的 `const` `char16` 数组的开头的指针（`char16` 是 `wchar_t` 的 typedef）。  
  
## 备注  
 使用此方法可从 `Platform::String^` 转换为 `wchar_t*`。 当 `String` 对象超出范围时，数据指针不再保证有效。 若有存储在原始 `String` 对象的生存期以外的数据，请使用 [wcscpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 数组复制到您为自己分配的内存中。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)   
 [String::Begin 方法](../cppcx/string-begin-method.md)