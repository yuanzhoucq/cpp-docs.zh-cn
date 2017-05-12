---
title: "Platform::ChangedStateException 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ChangedStateException"
  - "Platform/Platform::ChangedStateException::ChangedStateException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ChangedStateException"
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ChangedStateException 类
当对象的内部状态发生更改进而导致方法的结果失效时引发。  
  
## 语法  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 备注  
 例如，如果在父集合更改后调用集合迭代器或集合视图的方法，即会导致方法的结果失效，这时就会引发此异常。  
  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)