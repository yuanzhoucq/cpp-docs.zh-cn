---
title: "ArrayReference::operator= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::operator="
dev_langs: 
  - "C++"
ms.assetid: 131a4612-d66b-48e4-90af-c665ccc0cce4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::operator= 运算符
通过使用移动语义，将指定对象分配给当前 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 对象。  
  
## 语法  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& __otherArg);  
  
```  
  
#### 参数  
 `__ otherArg`  
 移动到当前 `ArrayReference` 对象的对象。  
  
## 返回值  
 对类型为 `ArrayReference` 的对象的引用。  
  
## 备注  
 `Platform::ArrayReference` 是标准 C\+\+ 类模板，而不是 ref 类。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::ArrayReference 类](../cppcx/platform-arrayreference-class.md)