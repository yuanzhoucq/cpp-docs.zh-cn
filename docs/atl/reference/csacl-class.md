---
title: CSacl 类
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: c4bbdfccb2d6d8b167c537b7ae4df57c89438479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496519"
---
# <a name="csacl-class"></a>CSacl 类

此类是 SACL (系统访问控制列表) 结构的包装器。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CSacl : public CAcl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|构造函数。|
|[CSacl::~CSacl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|向`CSacl`对象添加审核访问控制项 (ACE)。|
|[CSacl::GetAceCount](#getacecount)|返回`CSacl`对象中访问控制项 (ace) 的数量。|
|[CSacl::RemoveAce](#removeace)|从`CSacl`对象中移除特定的 ACE (访问控制项)。|
|[CSacl::RemoveAllAces](#removeallaces)|删除`CSacl`对象中包含的所有 ace。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSacl:: operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

SACL 包含访问控制项 (Ace), 用于指定在域控制器的安全事件日志中生成审核记录的访问尝试的类型。 请注意, SACL 仅在发生访问尝试的域控制器上生成日志条目, 而不是在包含对象副本的每个域控制器上生成日志条目。

若要设置或检索对象的安全描述符中的 SACL, 必须在请求线程的访问令牌中启用 SE_SECURITY_NAME 特权。 默认情况下, 管理员组具有此权限, 并且可以被授予其他用户或组。 赋予权限并非全部都是必需的: 在可以执行特权定义的操作之前, 必须在安全访问令牌中启用权限才能使其生效。 该模型只允许为特定系统操作启用权限, 并在不再需要时禁用。 有关启用 SE_SECURITY_NAME 的示例, 请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl) 。

使用提供的类方法可以从`SACL`对象添加、删除、创建和删除 ace。 另请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)。

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="addauditace"></a>CSacl::AddAuditAce

向`CSacl`对象添加审核访问控制项 (ACE)。

```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)对象。

*AccessMask*<br/>
为指定`CSid`的对象指定要审核的访问权限的掩码。

*bSuccess*<br/>
指定是否要审核允许的访问尝试。 将此标志设置为 true 可启用审核;否则, 请将其设置为 false。

*bFailure*<br/>
指定是否要审核拒绝的访问尝试。 将此标志设置为 true 可启用审核;否则, 请将其设置为 false。

*AceFlags*<br/>
控制 ACE 继承的一组位标志。

*pObjectType*<br/>
对象类型。

*pInheritedObjectType*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果将 ACE 添加到`CSacl`对象中, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

`CSacl`对象包含访问控制项 (ace), 用于指定在安全事件日志中生成审核记录的访问尝试的类型。 此方法将此类 ACE 添加到`CSacl`对象。

有关可在*AceFlags*参数中设置的各种标志的说明, 请参阅[ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 。

##  <a name="csacl"></a>  CSacl::CSacl

构造函数。

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
现有`ACL` (访问控制列表) 结构。

### <a name="remarks"></a>备注

可以选择使用现有`ACL`的结构来创建对象。`CSacl` 确保此参数是系统访问控制列表 (SACL), 而不是自由访问控制列表 (DACL)。 在调试版本中, 如果提供了 DACL, 则将发生断言。 在版本中, 将忽略 DACL 中的任何条目。

##  <a name="dtor"></a>  CSacl::~CSacl

析构函数。

```
~CSacl() throw();
```

### <a name="remarks"></a>备注

析构函数释放由该对象获取的所有资源, 包括所有访问控制项 (Ace)。

##  <a name="getacecount"></a>  CSacl::GetAceCount

返回`CSacl`对象中访问控制项 (ace) 的数量。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>返回值

返回`CSacl`对象中包含的 ace 的数量。

##  <a name="operator_eq"></a>CSacl:: operator =

赋值运算符。

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
要`ACL`分配给现有对象的 (访问控制列表)。

### <a name="return-value"></a>返回值

返回对已更新`CSacl`的对象的引用。 确保该`ACL`参数实际上是系统访问控制列表 (SACL), 而不是自由访问控制列表 (DACL)。 在调试版本中, 将发生断言, 在发布`ACL`版本中, 将忽略参数。

##  <a name="removeace"></a>  CSacl::RemoveAce

从`CSacl`对象中移除特定的 ACE (访问控制项)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要移除的 ACE 项的索引。

### <a name="remarks"></a>备注

此方法从[CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)派生。

##  <a name="removeallaces"></a>  CSacl::RemoveAllAces

删除`CSacl`对象中包含的所有访问控制项 (ace)。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>备注

删除对象中的`CSacl`所有结构(如果有)。`ACE`

## <a name="see-also"></a>请参阅

[CAcl 类](../../atl/reference/cacl-class.md)<br/>
[Acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Ace](/windows/win32/SecAuthZ/access-control-entries)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
