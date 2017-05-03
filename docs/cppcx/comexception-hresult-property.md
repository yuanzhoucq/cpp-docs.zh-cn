---
title: "COMException::HResult 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::COMException::HResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMException::HResult 属性"
ms.assetid: 53762ab5-ce71-4397-b7b4-8175741c838f
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# COMException::HResult 属性
与异常相对应的 HRESULT。  
  
## 语法  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## 属性值  
 一个指定错误的 HRESULT 值。  
  
## 备注  
 有关如何解释 HRESULT 值的更多信息，请参见 [COM 错误代码结构](http://go.microsoft.com/fwlink/p/?LinkId=262045)。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 小节标题  
  
## 请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)