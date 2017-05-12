---
title: "Platform::WrongThreadException 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::WrongThreadException"
  - "Platform/Platform::WrongThreadException::WrongThreadException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::WrongThreadException"
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::WrongThreadException 类
当线程通过不属于该线程单元的代理对象的接口指针调用时引发。  
  
## 语法  
  
```cpp  
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 备注  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md)。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)