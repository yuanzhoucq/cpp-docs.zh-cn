---
title: HANDLENullTraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
dev_langs:
- C++
helpviewer_keywords:
- HANDLENullTraits structure
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3a49a1a1ac4495c7697fc041f8fcf217850f09d8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609419"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 结构

定义未初始化句柄的共同特征。

## <a name="syntax"></a>语法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`Type`|句柄的同义词。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[HANDLENullTraits::Close 方法](../windows/handlenulltraits-close-method.md)|关闭指定的句柄。|
|[HANDLENullTraits::GetInvalidValue 方法](../windows/handlenulltraits-getinvalidvalue-method.md)|表示无效句柄。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)