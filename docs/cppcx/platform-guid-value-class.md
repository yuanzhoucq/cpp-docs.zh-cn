---
title: "Platform::Guid 值类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Guid 结构"
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Guid 值类
代表 Windows 运行时类型系统中的 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) 类型。  
  
## 语法  
  
```cpp  
public value struct Guid  
```  
  
## 成员  
 Guid 具有从[Platform::Object 类](../cppcx/platform-object-class.md)派生的 Equals\(\)、GetHashCode\(\) 和 ToString\(\) 方法，以及从[Platform::Type 类](../cppcx/platform-type-class.md)。 Guid 还具有下列成员。  
  
|成员|描述|  
|--------|--------|  
|Guid|初始化 Guid 结构的新实例。|  
|operator\=\=|等于运算符。|  
|operator\!\=|不等于运算符。|  
|operator\(\)|将 Guid 转换为 GUID。|  
  
## 备注  
 有关如何使用 Windows 函数 [CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx) 生成新的 Platform::Guid 的示例，请参阅 [WinRT 组件：如何生成 GUID？](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)