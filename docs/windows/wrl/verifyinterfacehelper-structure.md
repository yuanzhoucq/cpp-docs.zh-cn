---
title: VerifyInterfaceHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: cdd0272953b2399cd71efe207eb1c56e5de154e6
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335771"
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

**命名空间：** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInterfaceHelper::Verify

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>备注

验证当前的模板参数指定的接口满足某些要求。
