---
title: CSecurityDesc 类
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 90f8cfd66fbab88bfa29c39ff27189f02447a7c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496489"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 类

此类是`SECURITY_DESCRIPTOR`结构的包装器。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CSecurityDesc
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|构造函数。|
|[CSecurityDesc::~CSecurityDesc](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|将字符串格式安全描述符转换为有效的功能安全说明符。|
|[CSecurityDesc::GetControl](#getcontrol)|从安全说明符中检索控件信息。|
|[CSecurityDesc::GetDacl](#getdacl)|从安全说明符中检索任意访问控制列表 (DACL) 信息。|
|[CSecurityDesc::GetGroup](#getgroup)|检索安全描述符中的主要组信息。|
|[CSecurityDesc::GetOwner](#getowner)|检索安全描述符中的 owner 信息。|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|返回指向`SECURITY_DESCRIPTOR`结构的指针。|
|[CSecurityDesc::GetSacl](#getsacl)|检索安全描述符中的系统访问控制列表 (SACL) 信息。|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|确定 DACL 是否配置为支持自动传播。|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|确定是否使用默认 DACL 配置安全描述符。|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|确定安全描述符是否包含 DACL。|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|确定是否将 DACL 配置为防止修改。|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|确定是否默认设置了安全描述符的组安全标识符 (SID)。|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|确定默认情况下是否设置安全描述符的所有者 SID。|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|确定是否将 SACL 配置为支持自动传播。|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|确定安全描述符是否配置了默认的 SACL。|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|确定安全描述符是否包含 SACL。|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|确定是否将 SACL 配置为防止修改。|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|确定安全描述符是否为自相关格式。|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|调用此方法可将安全描述符转换为绝对格式。|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|调用此方法可将安全描述符转换为自相关格式。|
|[CSecurityDesc::SetControl](#setcontrol)|设置安全说明符的控制位。|
|[CSecurityDesc::SetDacl](#setdacl)|设置 DACL 中的信息。 如果安全描述符中已经存在 DACL, 则会将其替换。|
|[CSecurityDesc::SetGroup](#setgroup)|设置绝对格式安全描述符的主要组信息, 替换已存在的任何主要组信息。|
|[CSecurityDesc::SetOwner](#setowner)|设置绝对格式安全描述符的所有者信息, 替换已存在的任何所有者信息。|
|[CSecurityDesc::SetSacl](#setsacl)|设置 SACL 中的信息。 如果 SACL 已存在于安全描述符中, 则会将其替换。|
|[CSecurityDesc::ToString](#tostring)|将安全描述符转换为字符串格式。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSecurityDesc:: operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|返回指向`SECURITY_DESCRIPTOR`结构的指针。|
|[CSecurityDesc::operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

`SECURITY_DESCRIPTOR`结构包含与对象关联的安全信息。 应用程序使用此结构来设置和查询对象的安全状态。 另请参阅[AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)。

应用程序不应直接`SECURITY_DESCRIPTOR`修改结构, 而应使用提供的类方法。

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

构造函数。

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
要`CSecurityDesc`分配给`SECURITY_DESCRIPTOR` 新`CSecurityDesc`对象的对象或结构。

### <a name="remarks"></a>备注

可以`CSecurityDesc`选择`SECURITY_DESCRIPTOR`使用结构或以前定义`CSecurityDesc`的对象来创建对象。

##  <a name="dtor"></a>  CSecurityDesc::~CSecurityDesc

析构函数。

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有已分配的资源。

##  <a name="fromstring"></a>  CSecurityDesc::FromString

将字符串格式安全描述符转换为有效的功能安全说明符。

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>参数

*pstr*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要转换的[字符串格式安全说明符](/windows/win32/SecAuthZ/security-descriptor-string-format)。

### <a name="return-value"></a>返回值

如果成功, 则返回 true。 失败时引发异常。

### <a name="remarks"></a>备注

可以使用[CSecurityDesc:: ToString](#tostring)创建字符串。 将安全描述符转换为字符串可以更轻松地进行存储和传输。

此方法调用[ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)。

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

从安全说明符中检索控件信息。

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>参数

*psdc*<br/>
指向一个`SECURITY_DESCRIPTOR_CONTROL`结构的指针, 该结构接收安全说明符的控制信息。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

此方法调用[GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)。

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

从安全说明符中检索任意访问控制列表 (DACL) 信息。

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pDacl*<br/>
指向一个`CDacl`结构的指针, 该结构用于存储安全描述符的 DACL 的副本。 如果存在任意 ACL, 此方法会将*pDacl*设置为安全描述符的任意 acl 的地址。 如果不存在任意 ACL, 则不存储任何值。

*pbPresent*<br/>
指向一个值的指针, 该值指示指定的安全描述符中是否存在任意 ACL。 如果安全描述符包含一个自由 ACL, 此参数设置为 true。 如果安全描述符不包含任意 ACL, 此参数将设置为 false。

*pbDefaulted*<br/>
指向标志的指针, 如果该安全描述符存在任意 ACL, 则`SECURITY_DESCRIPTOR_CONTROL`设置为结构中 SE_DACL_DEFAULTED 标志的值。 如果此标志为 true, 则会通过默认机制检索任意 ACL;如果为 false, 则用户显式指定了自定义 ACL。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

检索安全描述符中的主要组信息。

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向用于接收存储在 CDacl 中的组副本的[CSid](../../atl/reference/csid-class.md) (安全标识符) 的指针。

*pbDefaulted*<br/>
当方法返回时, 指向标志的指针设置为`SECURITY_DESCRIPTOR_CONTROL`结构中 SE_GROUP_DEFAULTED 标志的值。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

检索安全描述符中的 owner 信息。

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向用于接收存储在 CDacl 中的组副本的[CSid](../../atl/reference/csid-class.md) (安全标识符) 的指针。

*pbDefaulted*<br/>
当方法返回时, 指向标志的指针设置为`SECURITY_DESCRIPTOR_CONTROL`结构中 SE_OWNER_DEFAULTED 标志的值。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

返回指向`SECURITY_DESCRIPTOR`结构的指针。

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>返回值

返回一个指向[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)结构的指针。

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

检索安全描述符中的系统访问控制列表 (SACL) 信息。

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSacl*<br/>
一个`CSacl`指针, 指向用于存储安全描述符的 SACL 副本的结构。 如果存在系统 ACL, 则该方法会将*pSacl*设置为安全描述符的系统 acl 的地址。 如果系统 ACL 不存在, 则不存储任何值。

*pbPresent*<br/>
指向标志的指针, 方法设置该标志以指示指定安全描述符中存在系统 ACL。 如果安全描述符包含系统 ACL, 此参数设置为 true。 如果安全描述符不包含系统 ACL, 此参数将设置为 false。

*pbDefaulted*<br/>
如果安全描述符存在系统 ACL, 指向标志的指针将设置为`SECURITY_DESCRIPTOR_CONTROL`结构中 SE_SACL_DEFAULTED 标志的值。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

确定是否将自由访问控制列表 (DACL) 配置为支持自动传播。

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含一个 DACL, 该 DACL 设置为支持将可继承的访问控制项 (Ace) 自动传播到现有子对象, 则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

当系统对对象及其现有子对象执行自动继承算法时, 将设置此位。

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

确定是否使用默认的自由访问控制列表 (DACL) 配置安全描述符。

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含默认 DACL, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

与访问控制项 (ACE) 继承相关, 此标志可能会影响系统对 DACL 的处理方式。 例如, 如果对象的创建者未指定 DACL, 则对象从创建者的访问令牌接收默认的 DACL。 如果未设置 SE_DACL_PRESENT 标志, 系统将忽略此标志。

此标志用于确定如何计算对象上的最终 DACL, 并使其不会以物理方式存储在安全对象的安全描述符控件中。

若要设置此标志, 请使用[CSecurityDesc:: SetDacl](#setdacl)方法。

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

确定安全描述符是否包含随机访问控制列表 (DACL)。

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含 DACL, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

如果未设置此标志, 或者如果设置了此标志并且 DACL 为 NULL, 则安全描述符允许所有人都具有完全访问权限。

此标志用于保存由调用方指定的安全信息, 直到安全描述符与安全对象关联。 安全描述符与某个安全对象关联后, 将始终在安全描述符控件中设置 SE_DACL_PRESENT 标志。

若要设置此标志, 请使用[CSecurityDesc:: SetDacl](#setdacl)方法。

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

确定是否将自由访问控制列表 (DACL) 配置为防止修改。

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>返回值

如果 DACL 配置为禁止继承的访问控制项 (Ace) 修改安全描述符, 则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

若要设置此标志, 请使用[CSecurityDesc:: SetDacl](#setdacl)方法。

此方法支持自动传播可继承的 Ace。

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

确定是否默认设置了安全描述符的组安全标识符 (SID)。

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果默认机制 (而不是安全描述符的原始提供程序) 提供了安全描述符的组 SID, 则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

若要设置此标志, 请使用[CSecurityDesc:: SetGroup](#setgroup)方法。

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

确定是否默认设置了安全描述符的所有者安全标识符 (SID)。

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果默认机制 (而不是安全描述符的原始提供程序) 提供了安全描述符的所有者 SID, 则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

若要设置此标志, 请使用[CSecurityDesc:: SetOwner](#setowner)方法。

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

确定是否将系统访问控制列表 (SACL) 配置为支持自动传播。

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含设置为支持自动将可继承的访问控制项 (Ace) 传播到现有子对象的 SACL, 则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

当系统对对象及其现有子对象执行自动继承算法时, 将设置此位。

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

确定是否使用默认系统访问控制列表 (SACL) 配置安全描述符。

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含默认的 SACL, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

与访问控制项 (ACE) 继承相关, 此标志可能会影响系统如何处理 SACL。 如果未设置 SE_SACL_PRESENT 标志, 系统将忽略此标志。

若要设置此标志, 请使用[CSecurityDesc:: SetSacl](#setsacl)方法。

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

确定安全描述符是否包含系统访问控制列表 (SACL)。

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含 SACL, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

若要设置此标志, 请使用[CSecurityDesc:: SetSacl](#setsacl)方法。

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

确定是否将系统访问控制列表 (SACL) 配置为防止修改。

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>返回值

如果将 SACL 配置为禁止继承的访问控制项 (Ace) 修改安全描述符, 则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

若要设置此标志, 请使用[CSecurityDesc:: SetSacl](#setsacl)方法。

此方法支持自动传播可继承的 Ace。

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

确定安全描述符是否为自相关格式。

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符为自相关格式, 且具有连续内存块中的所有安全信息, 则返回 true。 如果安全描述符为绝对格式, 则返回 false。 有关详细信息, 请参阅[绝对和自相关安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

调用此方法可将安全描述符转换为绝对格式。

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

绝对格式的安全描述符包含指向其所包含的信息的指针, 而不是信息本身。 自相关格式的安全描述符包含连续内存块中的信息。 在自相关安全描述符中, `SECURITY_DESCRIPTOR`结构始终启动信息, 但安全描述符的其他组件可以在结构中以任意顺序跟踪。 自相关安全描述符的组件由安全描述符开头的偏移量标识, 而不是使用内存地址。 当安全描述符必须存储在磁盘上或通过通信协议进行传输时, 此格式很有用。 有关详细信息, 请参阅[绝对和自相关安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

调用此方法可将安全描述符转换为自相关格式。

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

绝对格式的安全描述符包含指向其所包含的信息的指针, 而不是包含信息本身。 自相关格式的安全描述符包含连续内存块中的信息。 在自相关安全描述符中, `SECURITY_DESCRIPTOR`结构始终启动信息, 但安全描述符的其他组件可以在结构中以任意顺序跟踪。 安全描述符的组件会通过安全描述符开头的偏移量来标识, 而不是使用内存地址。 当安全描述符必须存储在磁盘上或通过通信协议进行传输时, 此格式很有用。 有关详细信息, 请参阅[绝对和自相关安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="operator_eq"></a>CSecurityDesc:: operator =

赋值运算符。

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
要分配给`CSecurityDesc` `CSecurityDesc`对象的结构或对象。`SECURITY_DESCRIPTOR`

### <a name="return-value"></a>返回值

返回已更新`CSecurityDesc`的对象。

##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc:: operator const SECURITY_DESCRIPTOR *

将值强制转换为指向`SECURITY_DESCRIPTOR`结构的指针。

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>  CSecurityDesc::SetControl

设置安全说明符的控制位。

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>参数

*ControlBitsOfInterest*<br/>
SECURITY_DESCRIPTOR_CONTROL 掩码, 指示要设置的控件位。 有关可以设置的标志的列表, 请参阅[SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

*ControlBitsToSet*<br/>
SECURITY_DESCRIPTOR_CONTROL 掩码, 指示*ControlBitsOfInterest*掩码指定的控制位的新值。 此参数可以是为*ControlBitsOfInterest*参数列出的标志的组合。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法调用[SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

设置随机访问控制列表 (DACL) 中的信息。 如果安全描述符中已经存在 DACL, 则会将其替换。

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*Dacl*<br/>
对`CDacl`对象的引用, 该对象指定安全描述符的 DACL。 此参数不得为 NULL。 若要在安全描述符中设置空的 DACL, 应使用第一种形式的方法, 将*bPresent*设置为 false。

*bPresent*<br/>
指定一个标志, 该标志指示是否存在安全描述符中的 DACL。 如果此参数为 true, 则此方法将在`SECURITY_DESCRIPTOR_CONTROL`结构中设置 SE_DACL_PRESENT 标志, 并使用*DACL*和*bDefaulted*参数中的值。 如果该参数为 false, 则该方法将清除 SE_DACL_PRESENT 标志, 并且将忽略*bDefaulted* 。

*bDefaulted*<br/>
指定指示 DACL 源的标志。 如果此标志为 true, 则已通过某些默认机制检索 DACL。 如果为 false, 则用户显式指定了 DACL。 方法将此值存储在`SECURITY_DESCRIPTOR_CONTROL`结构的 SE_DACL_DEFAULTED 标志中。 如果未指定此参数, 则清除 SE_DACL_DEFAULTED 标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

空的 DACL 和不存在的 DACL 之间存在重要差异。 当 DACL 为空时, 它不会包含任何访问控制项, 也不会显式授予任何访问权限。 因此, 拒绝对对象的访问。 另一方面, 如果对象没有 DACL, 则不会将任何保护分配给该对象, 并授予任何访问请求。

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

设置绝对格式安全描述符的主要组信息, 替换已存在的任何主要组信息。

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*Sid*<br/>
对安全描述符的新主要组的[CSid](../../atl/reference/csid-class.md)对象的引用。 此参数不得为 NULL。 安全描述符可以标记为没有 DACL 或 SACL, 但它必须具有一个组和一个所有者, 即使这是 NULL SID (这是具有特殊意义的内置 SID)。

*bDefaulted*<br/>
指示是否从默认机制派生了主组信息。 如果此值为 true, 则它是默认信息, 方法将此值存储为`SECURITY_DESCRIPTOR_CONTROL`结构中的 SE_GROUP_DEFAULTED 标志。 如果此参数为零, 则清除 SE_GROUP_DEFAULTED 标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

设置绝对格式安全描述符的所有者信息。 它将替换任何已存在的所有者信息。

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*Sid*<br/>
安全描述符的新主要所有者的[CSid](../../atl/reference/csid-class.md)对象。 此参数不得为 NULL。

*bDefaulted*<br/>
指示所有者信息是否派生自默认机制。 如果此值为 true, 则它为默认信息。 此方法将此值存储为`SECURITY_DESCRIPTOR_CONTROL`结构中的 SE_OWNER_DEFAULTED 标志。 如果此参数为零, 则清除 SE_OWNER_DEFAULTED 标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

在系统访问控制列表 (SACL) 中设置信息。 如果 SACL 已存在于安全描述符中, 则会将其替换。

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*Sacl*<br/>
指向`CSacl`对象的指针, 该对象指定安全描述符的 SACL。 此参数不得为 NULL, 并且必须是 CSacl 对象。 与 Dacl 不同, NULL 和空的 SACL 没有区别, 因为 SACL 对象不指定访问权限, 仅审核信息。

*bDefaulted*<br/>
指定一个指示 SACL 源的标志。 如果此标志为 true, 则已通过某些默认机制检索了 SACL。 如果为 false, 则用户显式指定了 SACL。 方法将此值存储在`SECURITY_DESCRIPTOR_CONTROL`结构的 SE_SACL_DEFAULTED 标志中。 如果未指定此参数, 则清除 SE_SACL_DEFAULTED 标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

##  <a name="tostring"></a>  CSecurityDesc::ToString

将安全描述符转换为字符串格式。

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>参数

*pstr*<br/>
指向以 null 结尾的字符串的指针, 该字符串将接收[字符串格式的安全描述符](/windows/win32/SecAuthZ/security-descriptor-string-format)。

*si*<br/>
指定 SECURITY_INFORMATION 位标志的组合, 以指示要在输出字符串中包含的安全描述符的组成部分。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

安全描述符采用字符串格式后, 可以更轻松地存储或传输。 `CSecurityDesc::FromString`使用方法将字符串转换回安全说明符。

*Si*参数可以包含以下 SECURITY_INFORMATION 标志:

|值|含义|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|包括所有者。|
|GROUP_SECURITY_INFORMATION|包括主要组。|
|DACL_SECURITY_INFORMATION|包括 DACL。|
|SACL_SECURITY_INFORMATION|包括 SACL。|

如果 DACL 为 NULL, 并且在输入安全描述符中设置了 SE_DACL_PRESENT 控件位, 则该方法将失败。

如果 DACL 为 NULL, 并且在输入安全描述符中未设置 SE_DACL_PRESENT 控件位, 则生成的安全描述符字符串没有 D: component。 有关更多详细信息, 请参阅[安全描述符字符串格式](/windows/win32/SecAuthZ/security-descriptor-string-format)。

此方法调用[ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
