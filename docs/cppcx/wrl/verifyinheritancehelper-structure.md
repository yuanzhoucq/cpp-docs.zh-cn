---
title: VerifyInheritanceHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: c37a0eb74fd65b3d349d5b8b7c792fbaf7d1ac9a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783849"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>参数

*I*<br/>
一种类型。

*基本*<br/>
另一种类型。

## <a name="remarks"></a>备注

测试是否有一个接口派生自另一个接口。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                                       | 描述
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Verify](#verify) | 测试当前的模板参数指定的两个接口，并确定是否派生自另一个接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`VerifyInheritanceHelper`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInheritanceHelper::Verify

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>备注

测试当前的模板参数指定的两个接口，并确定是否派生自另一个接口。

如果不派生自另一个接口，则会发出错误。
