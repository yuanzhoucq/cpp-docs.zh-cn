---
title: RuntimeClassFlags 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c5bfd9fc6dd87c61149722e8ef7fed79f8f017da
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788833"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 结构

包含的类型的实例[RuntimeClass](../windows/runtimeclass-class.md)。

## <a name="syntax"></a>语法

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>参数

*flags*<br/>
一个[RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)值。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[RuntimeClassFlags::value 常量](#value-constant)|包含[RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)值。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassFlags`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="value-constant"></a>Runtimeclassflags:: Value 常量

包含的字段[RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)值。
  
```cpp
static const unsigned int value = flags;
```
