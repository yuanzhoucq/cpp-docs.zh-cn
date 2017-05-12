---
title: "Platform::ReCreateException 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ReCreateException"
dev_langs: 
  - "C++"
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ReCreateException 方法
此方法仅供内部使用，不用于用户代码。 请改用 [Exception::CreateException 方法](../cppcx/exception-createexception-method.md)。  
  
## 语法  
  
```vb  
static Exception^ ReCreateException(int hr)  
```  
  
#### 参数  
  
## 属性值\/返回值  
 基于指定的 HRESULT 返回新的 Platform::Exception^。  
  
## .NET Framework 等效项  
  
## 要求