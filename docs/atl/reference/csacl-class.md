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
ms.openlocfilehash: f8820be3073c6ffaffdaa9d04a7338ad584d36ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278015"
---
# <a name="csacl-class"></a>CSacl 类

此类是一个 SACL （系统访问控制列表） 结构的包装器。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
|[CSacl::AddAuditAce](#addauditace)|将审核访问控制项 (ACE) 添加到`CSacl`对象。|
|[CSacl::GetAceCount](#getacecount)|返回中的访问控制项 (Ace)`CSacl`对象。|
|[CSacl::RemoveAce](#removeace)|从删除特定的 ACE （访问控制项）`CSacl`对象。|
|[CSacl::RemoveAllAces](#removeallaces)|移除所有中包含的 Ace`CSacl`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSacl::operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

SACL 包含指定类型的域控制器的安全事件日志中生成审核记录的访问尝试的访问控制项 (Ace)。 请注意 SACL 生成仅在访问尝试的发生位置的域控制器上，而不包含该对象的副本的每个域控制器上的日志条目。

若要设置或检索对象的安全描述符中的 SACL，必须在请求线程的访问令牌中启用 SE_SECURITY_NAME 特权掌握。 管理员组具有默认情况下，授予此特权，它可以授予其他用户或组。 无权限授予不是只需要： 可以执行该操作定义的权限，权限必须先启用然后安全访问令牌中才能生效。 该模型允许仅用于特定的系统操作、 启用，然后禁用时不再需要的特权。 请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)并[AtlSetSacl](security-global-functions.md#atlsetsacl)有关启用 SE_SECURITY_NAME 的示例。

使用提供要添加、 删除、 创建和删除 Ace 中的类方法`SACL`对象。 另请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)并[AtlSetSacl](security-global-functions.md#atlsetsacl)。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="addauditace"></a>  CSacl::AddAuditAce

将审核访问控制项 (ACE) 添加到`CSacl`对象。

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
指定要审核的访问权限的掩码指定`CSid`对象。

*bSuccess*<br/>
指定是否允许的访问尝试将被审核。 此标志设置为 true 以启用审核;否则，将其设置为 false。

*bFailure*<br/>
指定是否要审核的拒绝的访问尝试。 此标志设置为 true 以启用审核;否则，将其设置为 false。

*AceFlags*<br/>
一组位标志，用于控制 ACE 继承。

*pObjectType*<br/>
对象类型。

*pInheritedObjectType*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果 ACE 添加到，则返回 TRUE`CSacl`对象，则返回 FALSE 失败。

### <a name="remarks"></a>备注

一个`CSacl`对象包含指定类型的安全事件日志中生成审核记录的访问尝试的访问控制项 (Ace)。 此方法将添加到此类的 ACE`CSacl`对象。

请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)有关的各种标志可设置中的说明*AceFlags*参数。

##  <a name="csacl"></a>  CSacl::CSacl

构造函数。

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*<br/>
将现有`ACL`（访问控制列表） 结构。

### <a name="remarks"></a>备注

`CSacl`对象可以根据需要使用创建的现有`ACL`结构。 请确保此参数是系统访问控制列表 (SACL) 并不是自由访问控制列表 (DACL)。 在调试版本中，如果提供 DACL 断言会发生。 在发布版本中将忽略 DACL 中的任何条目。

##  <a name="dtor"></a>  CSacl::~CSacl

析构函数。

```
~CSacl() throw();
```

### <a name="remarks"></a>备注

析构函数释放由对象，包括所有访问控制项 (Ace) 获取任何资源。

##  <a name="getacecount"></a>  CSacl::GetAceCount

返回中的访问控制项 (Ace)`CSacl`对象。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>返回值

返回中包含的 Ace 的数量`CSacl`对象。

##  <a name="operator_eq"></a>  CSacl::operator =

赋值运算符。

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*<br/>
`ACL` （访问控制列表），要分配给现有对象。

### <a name="return-value"></a>返回值

返回对已更新的引用`CSacl`对象。 确保`ACL`参数是实际系统访问控制列表 (SACL) 并不是自由访问控制列表 (DACL)。 在调试版本中将出现一个断言，并在发布版本中`ACL`参数将被忽略。

##  <a name="removeace"></a>  CSacl::RemoveAce

从删除特定的 ACE （访问控制项）`CSacl`对象。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要移除的 ACE 项的索引。

### <a name="remarks"></a>备注

此方法派生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeallaces"></a>  CSacl::RemoveAllAces

移除所有访问控制项 (Ace) 中包含`CSacl`对象。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>备注

删除每个`ACE`结构中 （如果有）`CSacl`对象。

## <a name="see-also"></a>请参阅

[CAcl 类](../../atl/reference/cacl-class.md)<br/>
[ACLs](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[ACEs](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
