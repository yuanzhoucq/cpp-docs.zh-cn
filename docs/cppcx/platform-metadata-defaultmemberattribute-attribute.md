---
title: "Platform::Metadata::DefaultMemberAttribute 特性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Metadata::DefaultMemberAttribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Metadata::DefaultMemberAttribute 特性"
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Metadata::DefaultMemberAttribute 特性
指示首选函数以在几个可能的重载函数中调用。  
  
## 语法  
  
```cpp  
  
public ref class DefaultMember abstract : Attribute  
```  
  
## 继承  
 [Platform::Object](../cppcx/object-object-constructor.md)  
  
 [Platform::Metadata::Attribute](../cppcx/platform-metadata-attribute-attribute.md)  
  
## 备注  
 将 DefaultMember 特性应用于将由 JavaScript 应用程序使用的方法。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform::Metadata  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::Metadata 命名空间](../cppcx/platform-metadata-namespace.md)