---
title: CPrivateObjectSecurityDesc 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f69172986a2f9bd3ca7c0b2373bb815a2f52186b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029008"
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
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|调用此方法将安全描述符和其访问控制列表 (Acl) 转换为支持自动的可继承的访问控制项 (Ace) 传播的格式。|
|[CPrivateObjectSecurityDesc::Create](#create)|调用此方法来分配并初始化由调用资源管理器创建的私有对象的自相关的安全描述符。|
|[CPrivateObjectSecurityDesc::Get](#get)|调用此方法以检索私有对象的安全描述符中的信息。|
|[CPrivateObjectSecurityDesc::Set](#set)|调用此方法来修改私有对象的安全描述符。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

此类派生自[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)，提供用于创建和管理私有对象的安全描述符的方法。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

调用此方法将安全描述符和其访问控制列表 (Acl) 转换为支持自动的可继承的访问控制项 (Ace) 传播的格式。

```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>参数

*pParent*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象，用于引用该对象的父容器。 如果没有父容器，此参数为 NULL。

*对象类型*<br/>
指向`GUID`结构，它标识与当前对象相关联的对象的类型。 设置*ObjectType*到; 如果对象不具有一个 GUID 为 NULL。

*bIsDirectoryObject*<br/>
指定新的对象是否可以包含其他对象。 值为 true 指示新对象是一个容器。 如果值为 false 指示新的对象不是容器。

*GenericMapping*<br/>
指向[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping)结构，它指定从每个通用的权限对象的特定权限的映射。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法会尝试确定是否的 Ace 的自由访问控制列表 (DACL) 和当前的安全描述符的系统访问控制列表 (SACL) 被继承自父安全描述符。 它将调用[ConvertToAutoInheritPrivateObjectSecurity](https://msdn.microsoft.com/library/windows/desktop/aa376403)函数。

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

析构函数释放所有已分配的资源，并删除私有对象的安全描述符。

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

调用此方法来分配并初始化由调用资源管理器创建的私有对象的自相关的安全描述符。

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
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象，用于引用在其中创建新的对象的父目录。 如果没有父目录，则设置为 NULL。

*pCreator*<br/>
指向对象的创建者提供的安全描述符的指针。 如果该对象的创建者显式传递的新对象的安全信息，请设置此参数为 NULL。

*bIsDirectoryObject*<br/>
指定新的对象是否可以包含其他对象。 值为 true 指示新对象是一个容器。 如果值为 false 指示新的对象不是容器。

*令牌*<br/>
引用[CAccessToken](../../atl/reference/caccesstoken-class.md)以其名义创建对象的客户端进程的对象。

*GenericMapping*<br/>
指向[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping)结构，它指定从每个通用的权限对象的特定权限的映射。

*对象类型*<br/>
指向`GUID`结构，它标识与当前对象相关联的对象的类型。 设置*ObjectType*到; 如果对象不具有一个 GUID 为 NULL。

*bIsContainerObject*<br/>
指定新的对象是否可以包含其他对象。 值为 true 指示新对象是一个容器。 如果值为 false 指示新的对象不是容器。

*AutoInheritFlags*<br/>
一组位标志，用于控制如何将访问控制项 (Ace) 继承自*pParent*。 请参阅[CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581)的更多详细信息。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法调用[CreatePrivateObjectSercurity](https://msdn.microsoft.com/library/windows/desktop/aa376405)或[CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581)。

第二种方法允许指定新的对象的对象类型的 GUID 或控制如何继承 Ace。

> [!NOTE]
>  自相关的安全描述符是将所有安全信息存储在连续内存块的安全描述符。

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

调用此方法以检索私有对象的安全描述符中的信息。

```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>参数

*si*<br/>
一组位标志，用于指示要检索的安全描述符的部分。 此值可以为组成[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)位标志。

*pResult*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象，它接收从指定的安全描述符的所需的信息的副本。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

安全描述符是结构和关联的数据包含安全对象的安全信息。

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

赋值运算符。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*<br/>
`CPrivateObjectSecurityDesc`要分配给当前对象的对象。

### <a name="return-value"></a>返回值

返回已更新`CPrivateObjectSecurityDesc`对象。

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

调用此方法来修改私有对象的安全描述符。

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
一组位标志，用于指示要设置的安全描述符的部分。 此值可以为组成[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)位标志。

*修改*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象。 指示此安全说明符的组成部分*si*参数应用于对象的安全描述符。

*GenericMapping*<br/>
指向[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping)结构，它指定从每个通用的权限对象的特定权限的映射。

*令牌*<br/>
引用[CAccessToken](../../atl/reference/caccesstoken-class.md)以其名义创建对象的客户端进程的对象。

*AutoInheritFlags*<br/>
一组位标志，用于控制如何将访问控制项 (Ace) 继承自*pParent*。 请参阅[CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581)的更多详细信息。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

第二种方法允许指定的对象的对象类型的 GUID 或控制如何继承 Ace。

## <a name="see-also"></a>请参阅

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 类](../../atl/reference/csecuritydesc-class.md)
