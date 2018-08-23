---
title: 'Platform:: typecode 枚举 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::TypeCode
dev_langs:
- C++
helpviewer_keywords:
- Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e874b3dc479755f688128b3e6690eee89929c1c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606177"
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode 枚举
指定表示一个内置类型的数字类别。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum class TypeCode {};  
```  
  
### <a name="members"></a>成员  
  
|类型代码|描述|  
|---------------|-----------------|  
|Boolean|Platform::Boolean 类型。|  
|Char16|default::char16 类型。|  
|DateTime|DateTime 类型。|  
|十进制|数值类型。|  
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
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd