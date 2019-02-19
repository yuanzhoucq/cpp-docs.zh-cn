---
title: RuntimeClassFlags 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335776"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 结构

包含的类型的实例[RuntimeClass](runtimeclass-class.md)。

## <a name="syntax"></a>语法

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>参数

*flags*<br/>
一个[RuntimeClassType 枚举](runtimeclasstype-enumeration.md)值。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[RuntimeClassFlags::value 常量](#value-constant)|包含[RuntimeClassType 枚举](runtimeclasstype-enumeration.md)值。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassFlags`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="value-constant"></a>Runtimeclassflags:: Value 常量

包含的字段[RuntimeClassType 枚举](runtimeclasstype-enumeration.md)值。

```cpp
static const unsigned int value = flags;
```
