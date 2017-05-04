---
title: "Exception::Message 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::Message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::Message 属性"
ms.assetid: ad1199cd-0889-4803-ad0d-a3a7b3c51891
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::Message 属性
描述错误的消息。  
  
## 语法  
  
```cpp  
public:property String^ Message;  
```  
  
## 属性值  
 对于 Windows 运行时中出现的异常，这是系统提供的错误描述。  
  
## 备注  
 在 [!INCLUDE[win8](../cppcx/includes/win8-md.md)] 中，此属性是只读的，因为该 Windows 运行时版本中的异常仅作为 HRESULTS 跨 ABI 传输。 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，可跨 ABI 传输更加丰富的异常信息，你可以提供自定义消息，供其他组件以编程方式进行访问。 有关更多信息，请参见[异常 \(C\+\+\/CX\)](../cppcx/exceptions-c-cx.md)。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::Exception 类](../cppcx/platform-exception-class.md)