---
title: "Platform::Exception 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Exception 类"
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Exception 类
表示在应用程序执行过程中发生的错误。 自定义异常类不能从 `Platform::Exception` 派生。 如果需要自定义异常，可以使用 `Platform::COMException` 并指定应用程序特定的 HRESULT。  
  
## 语法  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
## 成员  
 `Exception` 类继承自 `Object` 类、`IException`、`IPrintable` 和 `IEquatable` 接口。  
  
 `Exception` 还具有以下类型的成员。  
  
### 构造函数  
  
|成员|说明|  
|--------|--------|  
|[Exception::Exception 构造函数](../cppcx/exception-exception-constructor.md)|初始化 `Exception` 类的新实例。|  
  
### 方法  
 `Exception` 类从 `Equals()` 继承 `Finalize()`、`GetHashCode()`、`GetType()`、`MemberwiseClose()`、`ToString()` 和 [Platform::Object 类](../cppcx/platform-object-class.md) 方法。`Exception` 类还具有以下方法。  
  
|成员|描述|  
|--------|--------|  
|[Exception::CreateException 方法](../cppcx/exception-createexception-method.md)|创建表示指定 HRESULT 值的异常。|  
  
### 属性  
 此异常类还具有以下属性。  
  
|成员|描述|  
|--------|--------|  
|[Exception::HResult 属性](../cppcx/exception-hresult-property.md)|与异常相对应的 HRESULT。|  
|[Exception::Message 属性](../cppcx/exception-message-property.md)|描述异常的消息。 此值是只读的，在构造 `Exception` 后不能修改。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)