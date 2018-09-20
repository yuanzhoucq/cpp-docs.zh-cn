---
title: VerifyInterfaceHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInterfaceHelper structure
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62914b6e46b1fe98c95fba3ab96821c961888db8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413643"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 结构

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   bool isWinRTInterface,
   typename I
>
struct VerifyInterfaceHelper;

template <
   typename I
>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>参数

*I*<br/>
用于验证的接口。

*isWinRTInterface*

## <a name="remarks"></a>备注

验证模板参数指定的接口满足某些要求。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[VerifyInterfaceHelper::Verify 方法](../windows/verifyinterfacehelper-verify-method.md)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`VerifyInterfaceHelper`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)