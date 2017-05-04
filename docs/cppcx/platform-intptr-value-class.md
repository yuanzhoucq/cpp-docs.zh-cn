---
title: "Platform::IntPtr 值类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IntPtr 结构"
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::IntPtr 值类
表示一个签名指针或句柄，并且其大小特定于平台（32 位或 64 位）。  
  
## 语法  
  
```cpp  
public value struct IntPtr  
```  
  
## 成员  
 IntPtr 具有下列成员：  
  
|成员|描述|  
|--------|--------|  
|[IntPtr::IntPtr 构造函数](../cppcx/intptr-intptr-constructor.md)|初始化 IntPtr 的一个新实例。|  
|[IntPtr::op\_explicit 运算符](../cppcx/intptr-op-explicit-operator.md)|将指定参数转换为 IntPtr 或指向 IntPtr 值的指针。|  
|[IntPtr::ToInt32 方法](../cppcx/intptr-toint32-method.md)|将当前 IntPtr 转换为 32 位整数。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)