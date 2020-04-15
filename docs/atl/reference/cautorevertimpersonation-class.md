---
title: CAutoRevertImpersonation 类
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: 813b6f0dd33bdfa85476b816086217a7892f4476
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318794"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 类

此类将[CAccessToken](../../atl/reference/caccesstoken-class.md)对象还原为非模拟状态，当它超出范围时。

## <a name="syntax"></a>语法

```
class CAutoRevertImpersonation
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 自动还原模拟：：C 自动还原模拟](#cautorevertimpersonation)|构造`CAutoRevertImpersonation`对象|
|[C自动还原模拟：：_C 自动还原模拟](#dtor)|销毁对象并还原访问令牌模拟。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 自动还原模拟：：附加](#attach)|自动模拟访问令牌的重新回归。|
|[C 自动还原模拟：:D](#detach)|取消自动模拟还原。|
|[C 自动还原模拟：：获取访问令牌](#getaccesstoken)|检索与此对象关联的访问令牌电流。|

## <a name="remarks"></a>备注

[访问令牌](/windows/win32/SecAuthZ/access-tokens)是描述进程或线程的安全上下文的对象，并分配给登录到 Windows NT 或 Windows 2000 系统的每个用户。 这些访问令牌可以随`CAccessToken`类一起表示。

有时需要模拟访问令牌。 此类是为方便起见提供的，但它不执行访问令牌的模拟;因此，它无法执行访问令牌的模拟。它仅执行自动还原到非模拟状态。 这是因为令牌访问模拟可以执行几种不同的方式。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>C 自动还原模拟：：附加

自动模拟访问令牌的重新回归。

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>参数

*帕特*<br/>
要自动还原的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象的地址

### <a name="remarks"></a>备注

仅当使用 NULL`CAccessToken`指针创建[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)对象，或者以前调用[Detach](#detach)时，才应使用此方法。 对于简单情况，不需要使用此方法。

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>C 自动还原模拟：：C 自动还原模拟

构造 `CAutoRevertImpersonation` 对象。

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>参数

*帕特*<br/>
要自动还原的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象的地址。

### <a name="remarks"></a>备注

访问令牌的实际模拟应与创建对象分开执行，最好是在创建对象之前执行`CAutoRevertImpersonation`。 当对象超出范围时，`CAutoRevertImpersonation`此模拟将自动还原。

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>C自动还原模拟：：_C 自动还原模拟

销毁对象并还原访问令牌模拟。

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>备注

还原当前在构造或通过[Attach](#attach)方法提供的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象当前有效的任何模拟。 如果未`CAccessToken`关联，则析构函数不起作用。

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>C 自动还原模拟：:D

取消自动模拟还原。

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>返回值

以前关联的[CAccessToken](../../atl/reference/caccesstoken-class.md)的地址 ，如果不存在关联，则为 NULL。

### <a name="remarks"></a>备注

调用**分离**可防止`CAutoRevertImpersonation`对象还原当前与此对象关联的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象生效的任何模拟。 `CAutoRevertImpersonation`然后，可以使用[Attach](#attach)销毁，但不起作用或重新关联到同`CAccessToken`一对象或其他对象。

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>C 自动还原模拟：：获取访问令牌

检索与此对象关联的访问令牌电流。

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>返回值

以前关联的[CAccessToken](../../atl/reference/caccesstoken-class.md)的地址 ，如果不存在关联，则为 NULL。

### <a name="remarks"></a>备注

如果为包含重新还原`CAccessToken`对象模拟的目的调用此方法，则应改用[Detach](#detach)方法。

## <a name="see-also"></a>另请参阅

[ATL 安全示例](../../overview/visual-cpp-samples.md)<br/>
[访问令牌](/windows/win32/SecAuthZ/access-tokens)<br/>
[类概述](../../atl/atl-class-overview.md)
