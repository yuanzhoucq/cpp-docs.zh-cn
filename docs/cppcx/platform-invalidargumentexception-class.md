---
title: "Platform::InvalidArgumentException 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::InvalidArgumentException"
  - "Platform/Platform::InvalidArgumentException::InvalidArgumentException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::InvalidArgumentException"
ms.assetid: 1a8d860b-3bcb-41a9-9346-6610616a0b46
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Platform::InvalidArgumentException 类
当提供给方法的参数之一无效时引发。  
  
## 语法  
  
```cpp  
public ref class InvalidArgumentException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 备注  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)