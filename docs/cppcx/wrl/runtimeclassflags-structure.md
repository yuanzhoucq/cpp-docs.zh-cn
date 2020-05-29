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
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367217"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 结构

包含[运行时类](runtimeclass-class.md)实例的类型。

## <a name="syntax"></a>语法

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>参数

*标志*<br/>
[运行时类类型枚举](runtimeclasstype-enumeration.md)值。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[RuntimeClassFlags::value 常量](#value-constant)|包含[运行时类类型枚举](runtimeclasstype-enumeration.md)值。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassFlags`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>运行时类标志：：值常量

包含[运行时类类型枚举值的](runtimeclasstype-enumeration.md)字段。

```cpp
static const unsigned int value = flags;
```
