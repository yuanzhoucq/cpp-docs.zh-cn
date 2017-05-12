---
title: "Platform::COMException 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::COMException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::COMException 类"
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::COMException 类
表示在应用程序执行过程中发生的 COM 错误。 COMException 是一组预定义的标准异常的基类。  
  
## 语法  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
## 成员  
 COMException 类从对象类以及 IException、IPrintable 和 IEquatable 接口继承。  
  
 COMException 还具有下列类型的成员。  
  
 **构造函数**  
  
|成员|描述|  
|--------|--------|  
|`COMException`|初始化 COMException 类的新实例。|  
  
 **方法**  
  
 COMException 类从 [Platform::Object 类](../cppcx/platform-object-class.md) 继承 Equals\(\)、Finalize\(\), GetHashCode\(\)、GetType\(\)、MemberwiseClose\(\) 和 ToString\(\) 方法。  
  
 **属性**  
  
 COMException 类具有以下属性。  
  
|成员|描述|  
|--------|--------|  
|[Exception::HResult 属性](../cppcx/exception-hresult-property.md)|与异常相对应的 HRESULT。|  
|[Exception::Message 属性](../cppcx/exception-message-property.md)|描述异常的消息。|  
  
## 派生异常  
 下列预定义的异常从 COMException 派生。 它们与 COMException 的区别只在于名称、构造函数的名称和基础 HRESULT 值。  
  
|名称|基础 HRESULT|描述|  
|--------|----------------|--------|  
|COMException|*用户定义的 hresult*|从 COM 方法调用返回无法识别的 HRESULT 时引发。|  
|AccessDeniedException|E\_ACCESSDENIED|被拒绝访问资源或功能时引发。|  
|ChangedStateException|E\_CHANGED\_STATE|在父集合更改后调用集合迭代器或集合视图方法，从而导致方法的结果无效时引发。|  
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|当 COM 类尚未注册时引发。|  
|DisconnectedException|RPC\_E\_DISCONNECTED|当对象与其客户端的连接断开时引发。|  
|FailureException|E\_FAIL|操作失败时引发。|  
|InvalidArgumentException|E\_INVALIDARG|当提供给方法的参数之一无效时引发。|  
|InvalidCastException|E\_NOINTERFACE|当类型无法转换为另一种类型时引发。|  
|NotImplementedException|E\_NOTIMPL|当接口方法尚未在类上实现时引发。|  
|NullReferenceException|E\_POINTER|尝试取消引用空对象引用时引发。|  
|OperationCanceledException|E\_ABORT|操作中止时引发。|  
|OutOfBoundsException|E\_BOUNDS|某个操作尝试在有效范围外访问数据时引发。|  
|OutOfMemoryException|E\_OUTOFMEMORY|没有足够内存来完成操作时引发。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)