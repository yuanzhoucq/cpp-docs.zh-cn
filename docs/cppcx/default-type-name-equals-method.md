---
title: '默认:: (type_name):: Equals 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::Object::Equals
dev_langs:
- C++
ms.assetid: 4450f835-06fc-4758-8d0a-72cf00007873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 127f5ee876790fa3cfb8a052c2db6c41cc00f332
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109014"
---
# <a name="defaulttypenameequals-method"></a>default::(type_name)::Equals 方法

确定指定的对象是否等于当前对象。

## <a name="syntax"></a>语法

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>参数

*obj*<br/>
要比较的对象。

### <a name="return-value"></a>返回值

如果对象相等，则为`true` ；否则为 `false`。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** 默认

**标头：** vccorlib.h

## <a name="see-also"></a>请参阅

[默认命名空间](../cppcx/default-namespace.md)