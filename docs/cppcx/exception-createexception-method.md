---
title: "Exception::CreateException 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::CreateException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::CreateException 方法"
ms.assetid: 70e72bb4-3fec-478d-af3d-9ec8762d2825
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::CreateException 方法
基于指定的 HRESULT 值创建 Platform::Exception^。  
  
## 语法  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
## 参数  
 hr  
 调用 COM 方法时通常获取的 HRESULT 值。 如果该值为 0（等同于 S\_OK），此方法将引发 [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md)，因为成功的 COM 方法不应引发异常。  
  
 消息  
 描述错误的字符串。  
  
## 返回值  
 表示错误 HRESULT 的异常。  
  
## 备注  
 使用此方法可基于返回的 HRESULT（例如，调用 COM 接口方法时返回的 HRESULT）创建异常。 您可以使用带 String^ 参数的重载提供自定义消息。  
  
 强烈建议使用 CreateException 创建强类型的异常，而不是创建仅包含 HRESULT 的 [Platform::COMException](../cppcx/platform-comexception-class.md)。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)