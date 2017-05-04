---
title: "Object::GetHashCode 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::GetHashCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Object::GetHashCode"
ms.assetid: 403a60e9-be1d-4702-b14d-27fa4b2a043b
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::GetHashCode 方法
返回此实例的 [IUnknown](../atl/iunknown.md)\* 标识值（如果它是 COM 对象）或计算所得的哈希值（如果它不是 COM 对象）。  
  
## 语法  
  
```cpp  
public:int GetHashCode()  
```  
  
## 返回值  
 唯一标识此对象的数值。  
  
## 备注  
 可以在映射中使用 GetHashCode 创建对象的键。 可以使用 [Object::Equals 方法](../cppcx/object-equals-method.md) 比较哈希代码。 如果代码路径极为重要，并且 `GetHashCode` 和 `Equals` 不足够快，则可以下降到基础 COM 层并执行本机 [IUnknown](../atl/iunknown.md) 指针比较。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Object 类](../cppcx/platform-object-class.md)