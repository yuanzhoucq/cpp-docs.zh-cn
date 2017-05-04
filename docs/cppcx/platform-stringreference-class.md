---
title: "Platform::StringReference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::StringReference"
dev_langs: 
  - "C++"
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::StringReference 类
可以用于通过最少复制操作将字符串数据从 `Platform::String^` 输入参数传递到其他方法的优化类型。  
  
## 语法  
  
```cpp  
class StringReference  
```  
  
## 备注  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[StringReference::StringReference 构造函数](../cppcx/stringreference-stringreference-constructor.md)|两个用于创建 `StringReference` 实例的构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[StringReference::Data 方法](../cppcx/stringreference-data-method.md)|返回 char16 值数组形式的字符串数据。|  
|[StringReference::Length 方法](../cppcx/stringreference-length-method.md)|返回字符串中的字符数。|  
|[StringReference::GetHSTRING 方法](../cppcx/stringreference-gethstring-method.md)|返回 HSTRING 形式的字符串数据。|  
|[StringReference::GetString 方法](../cppcx/stringreference-getstring-method.md)|返回 `Platform::String^` 形式的字符串数据。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|`StringReference::operator=`|将 `StringReference` 分配给新 `StringReference` 实例。|  
|`StringReference::operator()`|将 `StringReference` 转换为 `Platform::String^`。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::StringReference Class](../cppcx/platform-stringreference-class.md)