---
title: "Platform::DisconnectedException 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::DisconnectedException"
  - "Platform/Platform::DisconnectedException::DisconnectedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::DisconnectedException"
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::DisconnectedException 类
在 COM 代理对象尝试引用不再存在的 COM 服务器时引发  
  
## 语法  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 备注  
 当类 A 引用另一个单独进程中的类（类 B）时，类 A 需要一个代理对象与承载类 B 的进程外 COM 服务器进行通信。有时该服务器可以在类 A 不知情的情况下离开内存。 在该情况下，将引发 RPC\_E\_DISCONNECTED 异常并且它转换为 Platform::DisconnectedException。 它发生的一种情况是，当事件源调用传递到它的委托，但该委托已在订阅该事件后的某个时点被销毁时。 当发生这种情况时，该事件源将移除来自其调用列表的委托。  
  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)