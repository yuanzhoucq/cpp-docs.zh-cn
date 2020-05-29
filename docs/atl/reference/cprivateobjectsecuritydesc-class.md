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
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331407"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 类

此类表示私有对象安全描述符对象。

## <a name="syntax"></a>语法

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C私有对象安全数据：：C私有对象安全数据](#cprivateobjectsecuritydesc)|构造函数。|
|[C 私有对象安全数据：*C 私有对象安全数据c](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C私有对象安全数据：：转换为自动继承](#converttoautoinherit)|调用此方法可将安全描述符及其访问控制列表 （ACL） 转换为支持自动传播可继承的访问控制条目 （ACEs） 的格式。|
|[C 私有对象安全：：创建](#create)|调用此方法以为调用资源管理器创建的私有对象分配和初始化自我相关安全描述符。|
|[C 私有对象安全：获取](#get)|调用此方法从私有对象的安全描述符中检索信息。|
|[C 私有对象安全：：设置](#set)|调用此方法以修改私有对象的安全描述符。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

此类派生自[CSecurityDesc，](../../atl/reference/csecuritydesc-class.md)它提供了创建和管理私有对象的安全描述符的方法。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>C私有对象安全数据：：转换为自动继承

调用此方法可将安全描述符及其访问控制列表 （ACL） 转换为支持自动传播可继承的访问控制条目 （ACEs） 的格式。

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>参数

*p 父级*<br/>
指向引用该对象的父容器的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针。 如果没有父容器，则此参数为 NULL。

*对象类型*<br/>
指向标识与`GUID`当前对象关联的对象类型的结构的指针。 如果对象没有 GUID，则将*对象类型*设置为 NULL。

*bIsDirectory对象*<br/>
指定新对象是否可以包含其他对象。 值为 true 表示新对象是容器。 false 值表示新对象不是容器。

*通用映射*<br/>
指向[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)结构的指针，该结构指定从每个泛型权限映射到对象的特定权限。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法尝试确定当前安全描述符的可自由访问控制列表 （DACL） 和系统访问控制列表 （SACL） 中的 ACE 是否从父安全描述符继承。 它调用[Convert 到自动继承私有对象安全](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)功能。

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>C私有对象安全数据：：C私有对象安全数据

构造函数。

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>备注

初始化 `CPrivateObjectSecurityDesc` 对象。

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>C 私有对象安全数据：*C 私有对象安全数据c

析构函数。

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有分配的资源，并删除私有对象的安全描述符。

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>C 私有对象安全：：创建

调用此方法以为调用资源管理器创建的私有对象分配和初始化自我相关安全描述符。

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

*p 父级*<br/>
指向引用正在其中创建新对象的父目录的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针。 如果没有父目录，则设置为 NULL。

*pCreator*<br/>
指向对象创建者提供的安全描述符的指针。 如果对象的创建者未显式传递新对象的安全信息，则将此参数设置为 NULL。

*bIsDirectory对象*<br/>
指定新对象是否可以包含其他对象。 值为 true 表示新对象是容器。 false 值表示新对象不是容器。

令牌 <br/>
引用为其创建该对象的客户端进程的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象。

*通用映射*<br/>
指向[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)结构的指针，该结构指定从每个泛型权限映射到对象的特定权限。

*对象类型*<br/>
指向标识与`GUID`当前对象关联的对象类型的结构的指针。 如果对象没有 GUID，则将*对象类型*设置为 NULL。

*bIs容器对象*<br/>
指定新对象是否可以包含其他对象。 值为 true 表示新对象是容器。 false 值表示新对象不是容器。

*自动继承标志*<br/>
一组位标志，用于控制如何从*pParent*继承访问控制条目 （ACE）。 有关详细信息[，请参阅创建私有对象安全Ex。](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法调用[创建私有对象异常或](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity)[创建私有对象安全Ex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)。

第二种方法允许指定新对象的对象类型 GUID 或控制 AES 的继承方式。

> [!NOTE]
> 自我相对安全描述符是一种安全描述符，用于将其所有安全信息存储在连续内存块中。

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>C 私有对象安全：获取

调用此方法从私有对象的安全描述符中检索信息。

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>参数

*四*<br/>
一组位标志，指示要检索的安全描述符的各个部分。 此值可以是[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位标志的组合。

*pResult*<br/>
指向从指定安全描述符接收请求信息副本的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

安全描述符是一个结构和关联数据，其中包含可保护对象的安全信息。

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>C 私有对象安全数据：：运算符 |

赋值运算符。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要分配给当前对象的 `CPrivateObjectSecurityDesc` 对象。

### <a name="return-value"></a>返回值

返回更新`CPrivateObjectSecurityDesc`的对象。

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>C 私有对象安全：：设置

调用此方法以修改私有对象的安全描述符。

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

*四*<br/>
一组位标志，指示要设置的安全描述符的各个部分。 此值可以是[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位标志的组合。

*修改*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象的指针。 *si*参数指示的安全描述符部分将应用于对象的安全描述符。

*通用映射*<br/>
指向[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)结构的指针，该结构指定从每个泛型权限映射到对象的特定权限。

令牌 <br/>
引用为其创建该对象的客户端进程的[CAccessToken](../../atl/reference/caccesstoken-class.md)对象。

*自动继承标志*<br/>
一组位标志，用于控制如何从*pParent*继承访问控制条目 （ACE）。 有关详细信息[，请参阅创建私有对象安全Ex。](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

第二种方法允许指定对象的对象类型 GUID 或控制 AES 的继承方式。

## <a name="see-also"></a>另请参阅

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 类](../../atl/reference/csecuritydesc-class.md)
