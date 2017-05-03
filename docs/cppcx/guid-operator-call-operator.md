---
title: "Guid::operator() 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid::operator()"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Guid::operator()"
  - "Platform, Guid::operator()"
ms.assetid: 5df51e6a-11c0-414c-8613-06b45a952828
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Guid::operator() 运算符
将 [GUID 结构](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) GUID 隐式转换为 Platform::Guid。  
  
## 语法  
  
```cpp  
Platform::Guid operator()  
```  
  
## 返回值  
 一个 Guid 结构。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::Guid 值类](../cppcx/platform-guid-value-class.md)