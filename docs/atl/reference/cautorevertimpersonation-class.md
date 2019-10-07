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
ms.openlocfilehash: f1941bfcd7689ab9d22f5094af0eb833a84dab6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497689"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 类

当[CAccessToken](../../atl/reference/caccesstoken-class.md)对象超出范围时, 此类将其还原到 nonimpersonating 状态。

## <a name="syntax"></a>语法

```
class CAutoRevertImpersonation
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|`CAutoRevertImpersonation`构造对象|
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|销毁对象并恢复访问令牌模拟。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|自动执行访问令牌的模拟重新确定。|
|[CAutoRevertImpersonation::Detach](#detach)|取消自动模拟重新确定。|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|检索与此对象关联的访问令牌。|

## <a name="remarks"></a>备注

[访问令牌](/windows/win32/SecAuthZ/access-tokens)是一个对象, 该对象描述进程或线程的安全上下文, 并分配给登录到 windows NT 或 windows 2000 系统的每个用户。 这些访问令牌可使用`CAccessToken`类表示。

有时需要模拟访问令牌。 此类是为方便而提供的, 但它不会执行访问令牌的模拟;它仅执行自动重新确定到 nonimpersonated 状态。 这是因为令牌访问模拟可以通过多种不同的方式来执行。

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="attach"></a>CAutoRevertImpersonation:: Attach

自动执行访问令牌的模拟重新确定。

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>参数

*pAT*<br/>
要自动还原的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象的地址

### <a name="remarks"></a>备注

仅当使用 NULL `CAccessToken`指针创建了[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)对象, 或以前调用了[分离](#detach)时, 才应使用此方法。 对于简单的情况, 无需使用此方法。

##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

构造 `CAutoRevertImpersonation` 对象。

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>参数

*pAT*<br/>
要自动还原的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象的地址。

### <a name="remarks"></a>备注

访问令牌的实际模拟应该与创建`CAutoRevertImpersonation`对象之前, 分别从和中进行。 当对象超出范围时, `CAutoRevertImpersonation`此模拟将自动还原。

##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

销毁对象并恢复访问令牌模拟。

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>备注

对于在构造或通过[Attach](#attach)方法提供的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象, 恢复当前生效的任何模拟。 如果没有`CAccessToken`关联, 析构函数将不起作用。

##  <a name="detach"></a>CAutoRevertImpersonation::D etach

取消自动模拟重新确定。

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>返回值

先前关联的[CAccessToken](../../atl/reference/caccesstoken-class.md)的地址, 如果不存在关联, 则为 NULL。

### <a name="remarks"></a>备注

调用**分离**可防止`CAutoRevertImpersonation`对象恢复当前对与此对象关联的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象有效的任何模拟。 `CAutoRevertImpersonation`然后, 可以使用`CAccessToken` [Attach](#attach)对相同或另一个对象进行不影响或重新关联的销毁。

##  <a name="getaccesstoken"></a>CAutoRevertImpersonation:: GetAccessToken

检索与此对象关联的访问令牌。

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>返回值

先前关联的[CAccessToken](../../atl/reference/caccesstoken-class.md)的地址, 如果不存在关联, 则为 NULL。

### <a name="remarks"></a>备注

如果调用此方法的目的包括`CAccessToken`对象模拟的重新确定, 则应改用[分离](#detach)方法。

## <a name="see-also"></a>请参阅

[Atlsecurity.h 示例](../../overview/visual-cpp-samples.md)<br/>
[访问令牌](/windows/win32/SecAuthZ/access-tokens)<br/>
[类概述](../../atl/atl-class-overview.md)
