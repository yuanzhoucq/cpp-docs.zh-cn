---
title: "ArrayReference::operator() 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::operatorArray^"
dev_langs: 
  - "C++"
ms.assetid: 48726344-82bb-4c1d-b246-ed74b895f99b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::operator() 运算符
将当前 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 对象转换回 [Platform::Array](../cppcx/platform-array-class.md) 类。  
  
## 语法  
  
```cpp  
  
Array<__TArg>^ operator ();  
  
```  
  
## 返回值  
 `Array<__TArg>^` 类型的句柄到对象  
  
## 备注  
 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 和 [Platform::Array](../cppcx/platform-array-class.md) 是标准 C\+\+ 类模板，而不是 ref 类。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::ArrayReference 类](../cppcx/platform-arrayreference-class.md)