---
title: "Platform::CallbackContext 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::CallbackContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::CallbackContext 枚举"
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Platform::CallbackContext 枚举
指定在其中执行回调函数（事件处理程序）的线程上下文。  
  
## 语法  
  
```cpp  
enum class CallbackContext {};  
```  
  
## 成员  
  
|类型代码|描述|  
|----------|--------|  
|任意|回调函数可以在任何线程上下文上执行。|  
|相同|回调函数只能在启动了异步操作的线程上下文上执行。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd