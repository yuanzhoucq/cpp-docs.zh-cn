---
title: VerifyInterfaceHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b70155566695ade6b6778ade3b4758faebb3ea67
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788860"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 结构

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
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

名称                                            | 描述
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify 方法](#verify) | 验证当前的模板参数指定的接口满足某些要求。

## <a name="inheritance-hierarchy"></a>继承层次结构

`VerifyInterfaceHelper`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="verify"></a>Verifyinterfacehelper:: Verify

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>备注

验证当前的模板参数指定的接口满足某些要求。
