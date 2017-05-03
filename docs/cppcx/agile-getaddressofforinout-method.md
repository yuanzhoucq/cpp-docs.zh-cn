---
title: "Agile::GetAddressOfForInOut 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::GetAddressOfForInOut"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::GetAddressOfForInOut"
ms.assetid: 8bb27b4c-c325-49ee-91db-9adf87c530c4
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::GetAddressOfForInOut 方法
将句柄的地址返回到用当前敏捷对象表示的对象。  
  
## 语法  
  
```cpp  
  
       T^* GetAddressOfForInOut()   
throw();  
  
```  
  
#### 参数  
 `T`  
 模板类型名称参数指定的类型。  
  
## 返回值  
 返回到用当前敏捷对象表示的对象的句柄的地址。  
  
## 备注  
 此操作获取当前线程上下文，然后将句柄的地址返回到基础对象。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Agile 类](../cppcx/platform-agile-class.md)