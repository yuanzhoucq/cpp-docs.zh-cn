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
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330965"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 类

此类是结构的`SECURITY_DESCRIPTOR`包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CSecurityDesc
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSecurityDesc：CSecurityDesc](#csecuritydesc)|构造函数。|
|[CSecurityDesc：*CSecurityDesc](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSecurityDesc：从弦](#fromstring)|将字符串格式的安全描述符转换为有效的功能安全描述符。|
|[CSecurityDesc：获取控制](#getcontrol)|从安全描述符检索控制信息。|
|[CSecurityDesc：getDacl](#getdacl)|从安全描述符检索可自由访问控制列表 （DACL） 信息。|
|[CSecurityDesc：获取组](#getgroup)|从安全描述符检索主组信息。|
|[CSecurityDesc：获取所有者](#getowner)|从安全描述符检索所有者信息。|
|[CSecurityDesc：GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|返回指向结构的`SECURITY_DESCRIPTOR`指针。|
|[CSecurityDesc：获取Sacl](#getsacl)|从安全描述符检索系统访问控制列表 （SACL） 信息。|
|[CSecurityDesc：isDacl自动继承](#isdaclautoinherited)|确定是否将 DACL 配置为支持自动传播。|
|[CSecurityDesc：isdacl已拖欠](#isdacldefaulted)|确定安全描述符是否配置了默认 DACL。|
|[CSecurityDesc：IsDacl存在](#isdaclpresent)|确定安全描述符是否包含 DACL。|
|[CSecurityDesc：IsDacl保护](#isdaclprotected)|确定是否配置了 DACL 以防止修改。|
|[CSecurityDesc：是集团违约](#isgroupdefaulted)|确定默认情况下是否设置了安全描述符的组安全标识符 （SID）。|
|[CSecurityDesc：是所有者违约](#isownerdefaulted)|确定默认情况下是否设置了安全描述符的所有者 SID。|
|[CSecurityDesc：issacl自动继承](#issaclautoinherited)|确定是否将 SACL 配置为支持自动传播。|
|[安全：：已违约](#issacldefaulted)|确定安全描述符是否配置了默认 SACL。|
|[安全：：Issacl存在](#issaclpresent)|确定安全描述符是否包含 SACL。|
|[安全：：Issacl保护](#issaclprotected)|确定是否配置了 SACL 以防止修改。|
|[CSecurityDesc：是自我相对的](#isselfrelative)|确定安全描述符是否采用自相对格式。|
|[CSecurityDesc：使绝对](#makeabsolute)|调用此方法可将安全描述符转换为绝对格式。|
|[CSecurityDesc：使自我相关](#makeselfrelative)|调用此方法可将安全描述符转换为自相关格式。|
|[CSecurityDesc：设置控制](#setcontrol)|设置安全说明符的控制位。|
|[CSecurityDesc：SetDacl](#setdacl)|在 DACL 中设置信息。 如果安全描述符中已存在 DACL，则替换它。|
|[CSecurityDesc：setGroup](#setgroup)|设置绝对格式安全描述符的主组信息，替换已存在的任何主组信息。|
|[CSecurityDesc：：SetOwner](#setowner)|设置绝对格式安全描述符的所有者信息，替换已存在的任何所有者信息。|
|[安全：：SetSacl](#setsacl)|在 SACL 中设置信息。 如果安全描述符中已存在 SACL，则替换它。|
|[安全：：到弦](#tostring)|将安全描述符转换为字符串格式。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CSecurityDesc：：操作员SECURITY_DESCRIPTOR |](#operator_const_security_descriptor__star)|返回指向结构的`SECURITY_DESCRIPTOR`指针。|
|[CSecurityDesc：：操作员 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

结构`SECURITY_DESCRIPTOR`包含与对象关联的安全信息。 应用程序使用此结构来设置和查询对象的安全状态。 另请参阅[AtlGet 安全描述器](security-global-functions.md#atlgetsecuritydescriptor)。

应用程序不应直接修改`SECURITY_DESCRIPTOR`结构，而应使用提供的类方法。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc：CSecurityDesc

构造函数。

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要`CSecurityDesc`分配给新`SECURITY_DESCRIPTOR``CSecurityDesc`对象的对象或结构。

### <a name="remarks"></a>备注

可以选择`CSecurityDesc`使用`SECURITY_DESCRIPTOR`结构或以前定义`CSecurityDesc`的对象创建该对象。

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc：*CSecurityDesc

析构函数。

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有分配的资源。

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc：从弦

将字符串格式的安全描述符转换为有效的功能安全描述符。

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>参数

*普斯特*<br/>
指向包含要转换的[字符串格式安全描述符](/windows/win32/SecAuthZ/security-descriptor-string-format)的 null 终止字符串的指针。

### <a name="return-value"></a>返回值

成功时返回 true。 在发生故障时引发异常。

### <a name="remarks"></a>备注

可以使用[CSecurityDesc：：toString](#tostring)创建字符串。 将安全描述符转换为字符串可以更轻松地存储和传输。

此方法调用[ConvertString 安全描述](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)符。

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc：获取控制

从安全描述符检索控制信息。

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>参数

*psdc*<br/>
指向接收安全`SECURITY_DESCRIPTOR_CONTROL`描述符控制信息的结构的指针。

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，如果失败，则为 false。

### <a name="remarks"></a>备注

此方法调用[获取安全描述器控制](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)。

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc：getDacl

从安全描述符检索可自由访问控制列表 （DACL） 信息。

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pDacl*<br/>
指向用于存储`CDacl`安全描述符 DACL 副本的结构的指针。 如果存在可自由裁量 ACL，该方法将*pDacl*设置到安全描述符的可自由 ACL 地址。 如果不存在可自由裁量 ACL，则不存储任何值。

*pb存在*<br/>
指向指示指定安全描述符中存在可自由裁量 ACL 的值的指针。 如果安全描述符包含可自由定义的 ACL，则此参数设置为 true。 如果安全描述符不包含可自由定义的 ACL，则此参数设置为 false。

*pbdefault*<br/>
如果安全描述符存在可自由 ACL，则指向`SECURITY_DESCRIPTOR_CONTROL`结构中SE_DACL_DEFAULTED标志的值的标志。 如果此标志为 true，则默认机制检索可自由支配的 ACL;如果此标志为 true，则为"可自由支配的 ACL"。"为 true。如果为 false，则用户显式指定可自由支配的 ACL。

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，如果失败，则为 false。

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc：获取组

从安全描述符检索主组信息。

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向接收存储在 CDacl 中的组副本的[CSid（](../../atl/reference/csid-class.md)安全标识符）的指针。

*pbdefault*<br/>
当方法返回时，指向标记的指针设置为`SECURITY_DESCRIPTOR_CONTROL`结构中SE_GROUP_DEFAULTED标志的值。

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，如果失败，则为 false。

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc：获取所有者

从安全描述符检索所有者信息。

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向接收存储在 CDacl 中的组副本的[CSid（](../../atl/reference/csid-class.md)安全标识符）的指针。

*pbdefault*<br/>
当方法返回时，指向标记的指针设置为`SECURITY_DESCRIPTOR_CONTROL`结构中SE_OWNER_DEFAULTED标志的值。

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，如果失败，则为 false。

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc：GetPSECURITY_DESCRIPTOR

返回指向结构的`SECURITY_DESCRIPTOR`指针。

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>返回值

返回指向[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)结构的指针。

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc：获取Sacl

从安全描述符检索系统访问控制列表 （SACL） 信息。

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSacl*<br/>
指向用于存储`CSacl`安全描述符 SACL 副本的结构的指针。 如果存在系统 ACL，该方法将*pSacl*设置到安全描述符的系统 ACL 的地址。 如果系统 ACL 不存在，则不存储任何值。

*pb存在*<br/>
指向方法集的标志的指针，以指示指定安全描述符中是否存在系统 ACL。 如果安全描述符包含系统 ACL，则此参数设置为 true。 如果安全描述符不包含系统 ACL，则此参数设置为 false。

*pbdefault*<br/>
如果安全描述符存在系统 ACL，则指向`SECURITY_DESCRIPTOR_CONTROL`结构中SE_SACL_DEFAULTED标志的值的标志。

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，如果失败，则为 false。

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc：isDacl自动继承

确定是否将任意访问控制列表 （DACL） 配置为支持自动传播。

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含 DACL，则该 DACL 设置为支持将可继承的访问控制条目 （ACE） 自动传播到现有子对象，则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

系统在为对象及其现有子对象执行自动继承算法时设置此位。

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc：isdacl已拖欠

确定安全描述符是否配置了默认的可自由访问控制列表 （DACL）。

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含默认 DACL，则返回 true，否则为 false。

### <a name="remarks"></a>备注

此标志会影响系统对待 DACL 的方式，有关访问控制条目 （ACE） 继承。 例如，如果对象的创建者未指定 DACL，则该对象将从创建者的访问令牌接收默认 DACL。 如果未设置SE_DACL_PRESENT标志，则系统将忽略此标志。

此标志用于确定如何计算对象上的最后 DACL，并且不会物理存储在可保护对象的安全描述符控件中。

要设置此标志，请使用[CSecurityDesc：：setDacl](#setdacl)方法。

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc：IsDacl存在

确定安全描述符是否包含可自由访问控制列表 （DACL）。

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含 DACL，则返回 true，否则为 false。

### <a name="remarks"></a>备注

如果未设置此标志，或者此标志已设置，并且 DACL 为 NULL，则安全描述符允许对所有人进行完全访问。

此标志用于保存调用方指定的安全信息，直到安全描述符与可安全对象关联。 一旦安全描述符与可安全对象关联，SE_DACL_PRESENT标志始终在安全描述符控件中设置。

要设置此标志，请使用[CSecurityDesc：：setDacl](#setdacl)方法。

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc：IsDacl保护

确定是否配置了可自由访问控制列表 （DACL） 以防止修改。

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>返回值

如果 DACL 配置为防止可继承的访问控制条目 （ACE） 修改安全描述符，则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

要设置此标志，请使用[CSecurityDesc：：setDacl](#setdacl)方法。

此方法支持可继承 ACEs 的自动传播。

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc：是集团违约

确定默认情况下是否设置了安全描述符的组安全标识符 （SID）。

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果默认机制（而不是安全描述符的原始提供程序）提供安全描述符的组 SID，则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

要设置此标志，请使用[CSecurityDesc：：SetGroup](#setgroup)方法。

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc：是所有者违约

确定默认情况下是否设置了安全描述符的所有者安全标识符 （SID）。

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果默认机制（而不是安全描述符的原始提供程序）提供安全描述符的所有者 SID，则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

要设置此标志，请使用[CSecurityDesc：：SetOwner](#setowner)方法。

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc：issacl自动继承

确定系统访问控制列表 （SACL） 是否配置为支持自动传播。

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含 SACL，则该 SACL 设置为支持将可继承的访问控制条目 （ACE） 自动传播到现有子对象，则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

系统在为对象及其现有子对象执行自动继承算法时设置此位。

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>安全：：已违约

确定安全描述符是否配置了默认系统访问控制列表 （SACL）。

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含默认 SACL，则返回 true，否则为 false。

### <a name="remarks"></a>备注

此标志会影响系统对待 SACL 的方式，有关访问控制条目 （ACE） 继承。 如果未设置SE_SACL_PRESENT标志，系统将忽略此标志。

要设置此标志，请使用[CSecurityDesc：：setSacl](#setsacl)方法。

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>安全：：Issacl存在

确定安全描述符是否包含系统访问控制列表 （SACL）。

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符包含 SACL，则返回 true，否则为 false。

### <a name="remarks"></a>备注

要设置此标志，请使用[CSecurityDesc：：setSacl](#setsacl)方法。

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>安全：：Issacl保护

确定是否配置了系统访问控制列表 （SACL） 以防止修改。

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>返回值

如果 SACL 配置为防止可继承的访问控制条目 （ACE） 修改安全描述符，则返回 true。 否则，返回 false。

### <a name="remarks"></a>备注

要设置此标志，请使用[CSecurityDesc：：setSacl](#setsacl)方法。

此方法支持可继承 ACEs 的自动传播。

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc：是自我相对的

确定安全描述符是否采用自相对格式。

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>返回值

如果安全描述符采用自相对格式，所有安全信息都位于连续的内存块中，则返回 true。 如果安全描述符为绝对格式，则返回 false。 有关详细信息，请参阅[绝对和自我相对安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc：使绝对

调用此方法可将安全描述符转换为绝对格式。

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，否则为 false。

### <a name="remarks"></a>备注

绝对格式的安全描述符包含指向它包含的信息的指针，而不是信息本身。 自相对格式的安全描述符包含连续内存块中的信息。 在自相对安全描述符中`SECURITY_DESCRIPTOR`，结构始终启动信息，但安全描述符的其他组件可以按任何顺序跟踪结构。 与使用内存地址相比，自相对安全描述符的组件由安全描述符开头的偏移量标识。 当安全描述符必须存储在磁盘上或通过通信协议传输时，此格式非常有用。 有关详细信息，请参阅[绝对和自我相对安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc：使自我相关

调用此方法可将安全描述符转换为自相关格式。

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>返回值

如果方法成功，则返回 true，否则为 false。

### <a name="remarks"></a>备注

绝对格式的安全描述符包含指向它包含的信息的指针，而不是包含信息本身。 自相对格式的安全描述符包含连续内存块中的信息。 在自相对安全描述符中`SECURITY_DESCRIPTOR`，结构始终启动信息，但安全描述符的其他组件可以按任何顺序跟踪结构。 安全描述符的组件不是使用内存地址，而是通过安全描述符开头的偏移量标识。 当安全描述符必须存储在磁盘上或通过通信协议传输时，此格式非常有用。 有关详细信息，请参阅[绝对和自我相对安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc：：操作员 |

赋值运算符。

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要`SECURITY_DESCRIPTOR`分配给`CSecurityDesc`对象`CSecurityDesc`的结构或对象。

### <a name="return-value"></a>返回值

返回更新`CSecurityDesc`的对象。

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc：：操作员SECURITY_DESCRIPTOR |

将值投射到指向结构的`SECURITY_DESCRIPTOR`指针。

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc：设置控制

设置安全说明符的控制位。

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>参数

*控制兴趣*<br/>
指示要设置的控制位的 SECURITY_DESCRIPTOR_CONTROL 掩码。 有关可以设置的标志的列表，请参阅[设置安全描述器控制](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

*控件位集*<br/>
SECURITY_DESCRIPTOR_CONTROL掩码，指示*由 ControlBitsOfery*掩码指定的控件位的新值。 此参数可以是*为 ControlBitsOfery 参数*列出的标志的组合。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

此方法调用[SetSecurity 描述器控制](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc：SetDacl

在自由访问控制列表 （DACL） 中设置信息。 如果安全描述符中已存在 DACL，则替换它。

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
引用指定`CDacl`安全描述符的 DACL 的对象。 此参数不能为 NULL。 要在安全描述符中设置 NULL DACL，该方法的第一种形式应与设置为 false 的*b存在*一起使用。

*b目前*<br/>
指定指示安全描述符中存在 DACL 的标志。 如果此参数为 true，则该方法在`SECURITY_DESCRIPTOR_CONTROL`结构中设置SE_DACL_PRESENT标志，并使用*Dacl*和*bDefault 参数*中的值。 如果为 false，则方法清除SE_DACL_PRESENT标志，并忽略*bDefault。*

*b 默认*<br/>
指定指示 DACL 源的标志。 如果此标志为 true，则某些默认机制已检索 DACL。 如果为 false，则用户已显式指定 DACL。 该方法将此值存储在结构SE_DACL_DEFAULTED标志中`SECURITY_DESCRIPTOR_CONTROL`。 如果未指定此参数，则清除SE_DACL_DEFAULTED标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

空和不存在的 DACL 之间存在重要区别。 当 DACL 为空时，它不包含访问控制条目，并且未显式授予访问权限。 因此，隐式拒绝对对象的访问。 另一方面，当对象没有 DACL 时，则不向该对象分配任何保护，并且授予任何访问请求。

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc：setGroup

设置绝对格式安全描述符的主组信息，替换已存在的任何主组信息。

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*希*<br/>
对安全描述符的新主组的[CSid](../../atl/reference/csid-class.md)对象的引用。 此参数不能为 NULL。 安全描述符可以标记为没有 DACL 或 SACL，但它必须有一个组和一个所有者，即使它们是 NULL SID（这是具有特殊含义的内置 SID）。

*b 默认*<br/>
指示主组信息是否派生自默认机制。 如果此值为 true，则它是默认信息，该方法将此值存储为结构中`SECURITY_DESCRIPTOR_CONTROL`SE_GROUP_DEFAULTED标志。 如果此参数为零，则清除SE_GROUP_DEFAULTED标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc：：SetOwner

设置绝对格式安全描述符的所有者信息。 它替换已经存在的任何所有者信息。

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*希*<br/>
安全描述符的新主所有者的[CSid](../../atl/reference/csid-class.md)对象。 此参数不能为 NULL。

*b 默认*<br/>
指示所有者信息是否派生自默认机制。 如果此值为 true，则为默认信息。 该方法将此值存储为`SECURITY_DESCRIPTOR_CONTROL`结构中SE_OWNER_DEFAULTED标志。 如果此参数为零，则清除SE_OWNER_DEFAULTED标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>安全：：SetSacl

在系统访问控制列表 （SACL） 中设置信息。 如果安全描述符中已存在 SACL，则替换它。

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>参数

*萨克拉*<br/>
指向指定安全`CSacl`描述符的 SACL 的对象的指针。 此参数不能为 NULL，并且必须是 CSacl 对象。 与 DSL 不同，NULL 和空 SACL 没有区别，因为 SACL 对象不指定访问权限，只指定审核信息。

*b 默认*<br/>
指定指示 SACL 源的标志。 如果此标志为 true，则某些默认机制已检索 SACL。 如果为 false，则用户已显式指定 SACL。 该方法将此值存储在结构SE_SACL_DEFAULTED标志中`SECURITY_DESCRIPTOR_CONTROL`。 如果未指定此参数，则清除SE_SACL_DEFAULTED标志。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

## <a name="csecuritydesctostring"></a><a name="tostring"></a>安全：：到弦

将安全描述符转换为字符串格式。

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>参数

*普斯特*<br/>
指向将接收[字符串格式安全描述符](/windows/win32/SecAuthZ/security-descriptor-string-format)的 null 终止字符串的指针。

*四*<br/>
指定SECURITY_INFORMATION位标志的组合，以指示要包含在输出字符串中的安全描述符的组件。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

一旦安全描述符采用字符串格式，就可以更轻松地存储或传输它。 使用`CSecurityDesc::FromString`方法将字符串转换回安全描述符。

*si*参数可以包含以下SECURITY_INFORMATION标志：

|“值”|含义|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|包括所有者。|
|GROUP_SECURITY_INFORMATION|包括主组。|
|DACL_SECURITY_INFORMATION|包括 DACL。|
|SACL_SECURITY_INFORMATION|包括 SACL。|

如果 DACL 为 NULL，并且SE_DACL_PRESENT控制位在输入安全描述符中设置，则该方法将失败。

如果 DACL 为 NULL，并且SE_DACL_PRESENT控制位未在输入安全描述符中设置，则生成的安全描述符字符串没有 D： 组件。 有关详细信息，请参阅[安全描述符字符串格式](/windows/win32/SecAuthZ/security-descriptor-string-format)。

此方法调用[ConvertString 安全描述](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)符。

## <a name="see-also"></a>另请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
