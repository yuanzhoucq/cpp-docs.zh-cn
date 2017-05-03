---
title: "SizeT::SizeT 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::SizeT::SizeT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SizeT::SizeT 构造函数"
ms.assetid: b7e1cc00-3420-4730-a80e-80c33e3ad9e2
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SizeT::SizeT 构造函数
使用指定值初始化 SizeT 的新实例。  
  
## 语法  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
## 参数  
 value1  
 32 位无符号值。  
  
 value2  
 指向 32 位无符号值的指针。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::SizeT 值类](../cppcx/platform-sizet-value-class.md)