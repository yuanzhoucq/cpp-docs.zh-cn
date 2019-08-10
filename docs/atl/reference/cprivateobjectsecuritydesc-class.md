---
title: CPrivateObjectSecurityDesc 类
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: c1ac15d4d8254107a66e577321edb3c40578f240
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915798"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 类

此类表示私有对象安全描述符对象。

## <a name="syntax"></a>语法

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|构造函数。|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|调用此方法可将安全描述符及其访问控制列表 (Acl) 转换为支持自动传播可继承的访问控制项 (Ace) 的格式。|
|[CPrivateObjectSecurityDesc::Create](#create)|调用此方法为调用资源管理器创建的私有对象分配和初始化自相关安全描述符。|
|[CPrivateObjectSecurityDesc::Get](#get)|调用此方法可从私有对象的安全说明符中检索信息。|
|[CPrivateObjectSecurityDesc::Set](#set)|调用此方法可修改私有对象的安全说明符。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

此类派生自[CSecurityDesc](../../atl/reference/csecuritydesc-class.md), 它提供了用于创建和管理私有对象的安全描述符的方法。

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

调用此方法可将安全描述符及其访问控制列表 (Acl) 转换为支持自动传播可继承的访问控制项 (Ace) 的格式。

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>参数

*pParent*<br/>
指向引用对象父容器的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针。 如果没有父容器, 则此参数为 NULL。

*ObjectType*<br/>
指向`GUID`结构的指针, 该结构标识与当前对象关联的对象的类型。 如果对象不具有 GUID, 请将*ObjectType*设置为 NULL。

*bIsDirectoryObject*<br/>
指定新对象是否可包含其他对象。 如果值为 true, 则指示新对象是一个容器。 如果值为 false, 则表示新的对象不是容器。

*GenericMapping*<br/>
指向[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-generic_mapping)结构的指针, 该结构指定从每个泛型权限到对象的特定权限的映射。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法尝试确定当前安全描述符的自由访问控制列表 (DACL) 和系统访问控制列表 (SACL) 中的 Ace 是否继承自父安全描述符。 它将调用[ConvertToAutoInheritPrivateObjectSecurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)函数。

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

构造函数。

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>备注

初始化 `CPrivateObjectSecurityDesc` 对象。

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

析构函数。

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有已分配的资源, 并删除私有对象的安全说明符。

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

调用此方法为调用资源管理器创建的私有对象分配和初始化自相关安全描述符。

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>参数

*pParent*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针, 该对象引用要在其中创建新对象的父目录。 如果没有父目录, 则设置为 NULL。

*pCreator*<br/>
指向对象创建者提供的安全描述符的指针。 如果对象的创建者未显式传递新对象的安全信息, 请将此参数设置为 NULL。

*bIsDirectoryObject*<br/>
指定新对象是否可包含其他对象。 如果值为 true, 则指示新对象是一个容器。 如果值为 false, 则表示新的对象不是容器。

*令牌*<br/>
对[CAccessToken](../../atl/reference/caccesstoken-class.md)对象的引用, 该对象表示要在其上创建对象的客户端进程。

*GenericMapping*<br/>
指向[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-generic_mapping)结构的指针, 该结构指定从每个泛型权限到对象的特定权限的映射。

*ObjectType*<br/>
指向`GUID`结构的指针, 该结构标识与当前对象关联的对象的类型。 如果对象不具有 GUID, 请将*ObjectType*设置为 NULL。

*bIsContainerObject*<br/>
指定新对象是否可包含其他对象。 如果值为 true, 则指示新对象是一个容器。 如果值为 false, 则表示新的对象不是容器。

*AutoInheritFlags*<br/>
控制访问控制项 (Ace) 如何从*pParent*继承的一组位标志。 有关更多详细信息, 请参阅[CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法调用[CreatePrivateObjectSercurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity)或[CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)。

第二种方法允许指定新对象的对象类型 GUID 或控制 Ace 的继承方式。

> [!NOTE]
>  自相关安全描述符是一种安全描述符, 它将其所有安全信息存储在连续内存块中。

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

调用此方法可从私有对象的安全说明符中检索信息。

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>参数

*si*<br/>
指示要检索的安全描述符部分的一组位标志。 此值可以是[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)位标志的组合。

*pResult*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针, 该对象接收来自指定安全描述符的请求信息的副本。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

安全描述符是包含安全对象的安全信息的结构和关联数据。

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

赋值运算符。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
要`CPrivateObjectSecurityDesc`分配给当前对象的对象。

### <a name="return-value"></a>返回值

返回已更新`CPrivateObjectSecurityDesc`的对象。

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

调用此方法可修改私有对象的安全说明符。

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>参数

*si*<br/>
指示要设置的安全描述符部分的一组位标志。 此值可以是[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)位标志的组合。

*做*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针。 此安全描述符中由*si*参数指示的部分应用于对象的安全描述符。

*GenericMapping*<br/>
指向[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-generic_mapping)结构的指针, 该结构指定从每个泛型权限到对象的特定权限的映射。

*令牌*<br/>
对[CAccessToken](../../atl/reference/caccesstoken-class.md)对象的引用, 该对象表示要在其上创建对象的客户端进程。

*AutoInheritFlags*<br/>
控制访问控制项 (Ace) 如何从*pParent*继承的一组位标志。 有关更多详细信息, 请参阅[CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

第二种方法允许指定对象的对象类型 GUID 或控制 Ace 的继承方式。

## <a name="see-also"></a>请参阅

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 类](../../atl/reference/csecuritydesc-class.md)
