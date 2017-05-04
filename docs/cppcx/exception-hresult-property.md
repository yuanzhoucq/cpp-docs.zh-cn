---
title: "Exception::HResult 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::HResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::HResult 属性"
ms.assetid: 24ef008d-6884-4b8b-9556-41bfa6e1edf1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::HResult 属性
与异常相对应的 HRESULT。  
  
## 语法  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## 属性值  
 HRESULT 值。  
  
## 备注  
 大多数异常都以 COM 错误形式出现，这类错误会返回为 HRESULT 值。 C\+\+\/CX 会将这些值转换为 Platform::Exception^ 对象，此属性则存储原始错误代码的值。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::Exception 类](../cppcx/platform-exception-class.md)