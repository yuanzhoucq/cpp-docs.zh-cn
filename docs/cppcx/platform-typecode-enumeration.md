---
title: Platform::TypeCode 枚举
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::TypeCode
helpviewer_keywords:
- Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
ms.openlocfilehash: 86bc17c45f36a5a72b089340e166df11e9a4334d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214253"
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode 枚举

指定表示一个内置类型的数字类别。

## <a name="syntax"></a>语法

```cpp
enum class TypeCode {};
```

### <a name="members"></a>成员

|类型代码|说明|
|---------------|-----------------|
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
|Object|Platform::Object 类型。|
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
