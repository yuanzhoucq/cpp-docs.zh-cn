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
ms.openlocfilehash: 72b5c9fee3868286f9e4a0917f46aeb732349c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330991"
---
# <a name="csacl-class"></a>CSacl 类

此类是 SACL（系统访问控制列表）结构的包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CSacl : public CAcl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSacl：CSacl](#csacl)|构造函数。|
|[CSacl：*CSacl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSacl：：添加审核](#addauditace)|向`CSacl`对象添加审核访问控制条目 （ACE）。|
|[CSacl：获取服务计数](#getacecount)|返回`CSacl`对象中的访问控制条目 （AES） 数。|
|[CSacl：：删除Ace](#removeace)|从`CSacl`对象中删除特定的 ACE（访问控制条目）。|
|[CSacl：：删除所有Aces](#removeallaces)|删除`CSacl`对象中包含的所有 ACA。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CSacl：：运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

SACL 包含访问控制条目 （ACE），用于指定在域控制器的安全事件日志中生成审核记录的访问尝试类型。 请注意，SACL 仅在发生访问尝试的域控制器上生成日志条目，而不是在包含对象副本的每个域控制器上生成日志条目。

若要在对象的安全描述符中设置或检索 SACL，必须在请求线程的访问令牌中启用SE_SECURITY_NAME权限。 默认情况下，管理员组具有授予此权限的权限，可以授予其他用户或组。 授予权限并非全部必需：在可以执行权限定义的操作之前，必须在安全访问令牌中启用该特权才能生效。 该模型允许仅针对特定的系统操作启用特权，然后在不再需要特权时禁用这些权限。 有关启用SE_SECURITY_NAME的示例，请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl。](security-global-functions.md#atlsetsacl)

使用提供的类方法从`SACL`对象添加、删除、创建和删除 ACA。 另请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl：：添加审核

向`CSacl`对象添加审核访问控制条目 （ACE）。

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

*访问掩码*<br/>
指定要审核指定`CSid`对象的访问权限的掩码。

*b 成功*<br/>
指定是否审核允许的访问尝试。 将此标志设置为 true 以启用审核;否则，将其设置为 false。

*b失败*<br/>
指定是否审核被拒绝的访问尝试。 将此标志设置为 true 以启用审核;否则，将其设置为 false。

*王牌标志*<br/>
控制 ACE 继承的一组位标志。

*pObject类型*<br/>
对象类型。

*p继承对象类型*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果 ACE 添加到对象，`CSacl`则返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

对象`CSacl`包含访问控制条目 （ACE），用于指定在安全事件日志中生成审核记录的访问尝试类型。 此方法向`CSacl`对象添加这样的 ACE。

有关可在*AceFlags*参数中设置的各种标志的说明，请参阅[ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl：CSacl

构造函数。

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
现有`ACL`（访问控制列表）结构。

### <a name="remarks"></a>备注

可以使用`CSacl`现有`ACL`结构选择创建对象。 确保此参数是系统访问控制列表 （SACL），而不是任意访问控制列表 （DACL）。 在调试生成中，如果提供 DACL，将发生断言。 在版本版本中，DACL 中的任何条目都将被忽略。

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl：*CSacl

析构函数。

```
~CSacl() throw();
```

### <a name="remarks"></a>备注

析构函数释放对象获取的任何资源，包括所有访问控制条目 （ACE）。

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl：获取服务计数

返回`CSacl`对象中的访问控制条目 （AES） 数。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>返回值

返回`CSacl`对象中包含的 ACA 数。

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl：：运算符 |

赋值运算符。

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要`ACL`分配给现有对象的（访问控制列表）。

### <a name="return-value"></a>返回值

返回对更新`CSacl`对象的引用。 确保`ACL`参数实际上是一个系统访问控制列表 （SACL），而不是一个可自由的访问控制列表 （DACL）。 在调试生成中，将发生断言，在发布版本中，`ACL`参数将被忽略。

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl：：删除Ace

从`CSacl`对象中删除特定的 ACE（访问控制条目）。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要删除的 ACE 条目的索引。

### <a name="remarks"></a>备注

此方法派生自[CAtlarray：：removeAt。](../../atl/reference/catlarray-class.md#removeat)

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl：：删除所有Aces

删除`CSacl`对象中包含的所有访问控制条目 （AES）。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>备注

删除`CSacl`对象`ACE`中的每个结构（如果有）。

## <a name="see-also"></a>另请参阅

[CAcl 类](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[A](/windows/win32/SecAuthZ/access-control-entries)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
