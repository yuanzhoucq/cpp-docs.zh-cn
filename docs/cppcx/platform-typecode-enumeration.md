---
title: "Platform::TypeCode 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::TypeCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::TypeCode 枚举"
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Platform::TypeCode 枚举
指定表示一个内置类型的数字类别。  
  
## 语法  
  
```cpp  
enum class TypeCode {};  
```  
  
## 成员  
  
|类型代码|描述|  
|----------|--------|  
|Boolean|Platform::Boolean 类型。|  
|Char16|default::char16 类型。|  
|DateTime|DateTime 类型。|  
|Decimal|数值类型。|  
|Double|default::float64 类型。|  
|空|Void|  
|Int16|default::int16 类型。|  
|Int32|default::int32 类型。|  
|Int64|default::int64 类型。|  
|Int8|default::int8 类型。|  
|对象|Platform::Object 类型。|  
|Single|default::float32 类型。|  
|String|Platform::String 类型。|  
|UInt16|default::uint16 类型。|  
|UInt32|default::uint32 类型。|  
|UInt64|default::uint64 类型。|  
|UInt8|default::uint8 类型。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd