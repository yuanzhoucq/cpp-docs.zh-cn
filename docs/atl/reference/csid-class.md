---
title: CSid 类
ms.date: 03/27/2019
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: ed19ed3cdeb77612e20d826480ab73b9361366e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496453"
---
# <a name="csid-class"></a>CSid 类

此类是`SID` (安全标识符) 结构的包装。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CSid
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|一个 `CSid` 对象数组。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSid::CSid](#csid)|构造函数。|
|[CSid::~CSid](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSid::AccountName](#accountname)|返回与`CSid`对象关联的帐户的名称。|
|[CSid::Domain](#domain)|返回与`CSid`对象关联的域的名称。|
|[CSid::EqualPrefix](#equalprefix)|测试`SID` (安全标识符) 前缀的相等性。|
|[CSid::GetLength](#getlength)|返回`CSid`对象的长度。|
|[CSid::GetPSID](#getpsid)|返回指向`SID`结构的指针。|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|返回指向`SID_IDENTIFIER_AUTHORITY`结构的指针。|
|[CSid::GetSubAuthority](#getsubauthority)|返回`SID`结构中指定的 subauthority。|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|返回 subauthority 计数。|
|[CSid::IsValid](#isvalid)|`CSid`测试对象的有效性。|
|[CSid::LoadAccount](#loadaccount)|根据给定的帐户名和域或现有`SID`结构来更新对象。`CSid`|
|[CSid::Sid](#sid)|返回 ID 字符串。|
|[CSid::SidNameUse](#sidnameuse)|返回`CSid`对象状态的说明。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#operator_eq)|赋值运算符。|
|[operator const SID *](#operator_const_sid__star)|将对象强制转换为指向`SID`结构的指针。 `CSid`|

### <a name="global-operators"></a>全局运算符

|||
|-|-|
|[operator ==](#operator_eq_eq)|测试两个安全描述符对象是否相等|
|[operator !=](#operator_neq)|测试两个安全描述符对象是否不相等|
|[操作员\<](#operator_lt)|比较两个安全描述符对象的相对值。|
|[operator >](#operator_gt)|比较两个安全描述符对象的相对值。|
|[操作员\<=](#operator_lt__eq)|比较两个安全描述符对象的相对值。|
|[operator >=](#operator_gt__eq)|比较两个安全描述符对象的相对值。|

## <a name="remarks"></a>备注

`SID`结构是用于唯一标识用户或组的可变长度结构。

应用程序不应直接`SID`修改结构, 而是使用此包装类中提供的方法。 另请参阅[AtlGetOwnerSid](security-global-functions.md#atlgetownersid)、 [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid)、 [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)和[AtlSetOwnerSid](security-global-functions.md#atlsetownersid)。

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="accountname"></a>  CSid::AccountName

返回与`CSid`对象关联的帐户的名称。

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向帐户名称的 LPCTSTR。

### <a name="remarks"></a>备注

此方法尝试查找指定`SID`的 (安全标识符) 的名称。 有关完整详细信息, 请参阅[LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到的帐户`SID`名称, `AccountName`则返回一个空字符串。 如果网络超时使此方法无法找到该名称, 则会发生这种情况。 对于没有对应帐户名称的安全标识符 (如`SID`标识登录会话的), 也会发生此错误。

##  <a name="csid"></a>  CSid::CSid

构造函数。

```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
现有`CSid`的对象或`SID` (安全标识符) 结构。

*IdentifierAuthority*<br/>
颁发机构。

*nSubAuthorityCount*<br/>
Subauthority 计数。

*pszAccountName*<br/>
帐户名称。

*pszSystem*<br/>
系统名称。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL, 则改为使用本地系统。

*pSid*<br/>
指向`SID`结构的指针。

### <a name="remarks"></a>备注

构造函数初始化`CSid`对象, 将内部数据成员设置为*SidTypeInvalid*, 或者从现有`CSid`的、 `SID`或现有帐户复制设置。

如果初始化失败, 则构造函数将引发[CAtlException 类](../../atl/reference/catlexception-class.md)。

##  <a name="dtor"></a>  CSid::~CSid

析构函数。

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>备注

析构函数释放由该对象获取的任何资源。

##  <a name="csidarray"></a>  CSid::CSidArray

[CSid](../../atl/reference/csid-class.md)对象的数组。

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>备注

此 typedef 指定可用于从 ACL (访问控制列表) 检索安全标识符的数组类型。 请参阅[CAcl:: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries)。

##  <a name="domain"></a>CSid::D omain

返回与`CSid`对象关联的域的名称。

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向`LPCTSTR`域的。

### <a name="remarks"></a>备注

此方法尝试查找指定`SID`的 (安全标识符) 的名称。 有关完整详细信息, 请参阅[LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到的`SID`帐户名称, `Domain`则会将该域作为空字符串返回。 如果网络超时使此方法无法找到该名称, 则会发生这种情况。 对于没有对应帐户名称的安全标识符 (如`SID`标识登录会话的), 也会发生此错误。

##  <a name="equalprefix"></a>  CSid::EqualPrefix

测试`SID` (安全标识符) 前缀的相等性。

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>参数

rhs<br/>
要`SID`比较的 (安全标识符) `CSid`结构或对象。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

有关更多详细信息, 请参阅 Windows SDK 中的[EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) 。

##  <a name="getlength"></a>  CSid::GetLength

返回`CSid`对象的长度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>返回值

返回`CSid`对象的长度 (以字节为单位)。

### <a name="remarks"></a>备注

`CSid`如果结构无效, 则返回值不确定。 在调用`GetLength`之前, 请使用[CSid:: IsValid](#isvalid)成员`CSid`函数验证是否有效。

> [!NOTE]
>  在调试版本中, 如果`CSid`对象无效, 则该函数将导致断言。

##  <a name="getpsid"></a>  CSid::GetPSID

返回一个指向`SID` (安全标识符) 结构的指针。

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>返回值

返回`CSid`对象的基础`SID`结构的地址。

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

返回指向`SID_IDENTIFIER_AUTHORITY`结构的指针。

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>返回值

如果该方法成功, 它将返回`SID_IDENTIFIER_AUTHORITY`结构的地址。 如果失败, 则返回值为 undefined。 如果`CSid`对象无效, 则可能会发生故障, 在这种情况下, [CSid:: IsValid](#isvalid)方法返回 FALSE。 可为`GetLastError`扩展错误信息调用函数。

> [!NOTE]
>  在调试版本中, 如果`CSid`对象无效, 则该函数将导致断言。

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

返回`SID` (安全标识符) 结构中指定的 subauthority。

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>参数

*nSubAuthority*<br/>
Subauthority。

### <a name="return-value"></a>返回值

返回由 NSubAuthority 引用的 subauthority *。* Subauthority 值是一个相对标识符 (RID)。

### <a name="remarks"></a>备注

*NSubAuthority*参数指定一个索引值, 用于标识该方法将返回的 subauthority 数组元素。 方法不对此值执行验证测试。 应用程序可以调用[CSid:: GetSubAuthorityCount](#getsubauthoritycount)来发现可接受值的范围。

> [!NOTE]
>  在调试版本中, 如果`CSid`对象无效, 则该函数将导致断言。

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

返回 subauthority 计数。

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 subauthority 计数。

如果该方法失败, 则返回值为 undefined。 如果`CSid`对象无效, 则方法将失败。 若要获得扩展的错误信息，请调用 `GetLastError`。

> [!NOTE]
>  在调试版本中, 如果`CSid`对象无效, 则该函数将导致断言。

##  <a name="isvalid"></a>  CSid::IsValid

`CSid`测试对象的有效性。

```
bool IsValid() const throw();
```

### <a name="return-value"></a>返回值

如果`CSid`对象有效, 则返回 TRUE, 否则返回 FALSE。 此方法没有扩展的错误信息;不要调用`GetLastError`。

### <a name="remarks"></a>备注

方法通过验证修订`CSid`号是否在已知范围内并且 subauthorities 数小于最大值来验证对象。 `IsValid`

##  <a name="loadaccount"></a>CSid:: LoadAccount

根据给定的帐户名和域或现有 SID (安全标识符) 结构来更新对象。`CSid`

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>参数

*pszAccountName*<br/>
帐户名称。

*pszSystem*<br/>
系统名称。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL, 则改为使用本地系统。

*pSid*<br/>
指向[SID](/windows/win32/api/winnt/ns-winnt-sid)结构的指针。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。 若要获得扩展的错误信息，请调用 `GetLastError`。

### <a name="remarks"></a>备注

`LoadAccount`尝试查找指定名称的安全标识符。 有关更多详细信息, 请参阅[LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) 。

##  <a name="operator_eq"></a>CSid:: operator =

赋值运算符。

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
(安全标识符) 或`CSid`分配`CSid`给对象。 `SID`

### <a name="return-value"></a>返回值

返回对已更新`CSid`的对象的引用。

##  <a name="operator_eq_eq"></a>CSid:: operator = =

测试两个安全描述符对象是否相等。

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
(安全标识符), 或`CSid`出现在 = = 运算符的左侧。 `SID`

rhs<br/>
(安全标识符) 或`CSid`出现在 = = 运算符右侧的。 `SID`

### <a name="return-value"></a>返回值

如果安全描述符相等, 则为 TRUE; 否则为 FALSE。

##  <a name="operator_neq"></a>CSid:: operator! =

测试两个安全描述符对象是否不相等。

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
(安全标识符) 或`CSid`出现在! = 运算符的左侧。 `SID`

rhs<br/>
(安全标识符) 或`CSid`出现在! = 运算符右侧的。 `SID`

### <a name="return-value"></a>返回值

如果安全描述符不相等, 则为 TRUE; 否则为 FALSE。

##  <a name="operator_lt"></a>CSid:: 运算符&lt;

比较两个安全描述符对象的相对值。

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
(安全标识符) 或`CSid`出现在! = 运算符的左侧。 `SID`

rhs<br/>
(安全标识符) 或`CSid`出现在! = 运算符右侧的。 `SID`

### <a name="return-value"></a>返回值

如果*lhs*小于*rhs*, 则为 TRUE; 否则为 FALSE。

##  <a name="operator_lt__eq"></a>CSid:: 运算符&lt;=

比较两个安全描述符对象的相对值。

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
(安全标识符) 或`CSid`出现在! = 运算符的左侧。 `SID`

rhs<br/>
(安全标识符) 或`CSid`出现在! = 运算符右侧的。 `SID`

### <a name="return-value"></a>返回值

如果*lhs*小于或等于*rhs*, 则为 TRUE; 否则为 FALSE。

##  <a name="operator_gt"></a>CSid:: 运算符&gt;

比较两个安全描述符对象的相对值。

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
(安全标识符) 或`CSid`出现在! = 运算符的左侧。 `SID`

rhs<br/>
(安全标识符) 或`CSid`出现在! = 运算符右侧的。 `SID`

### <a name="return-value"></a>返回值

如果*lhs*大于*rhs*, 则为 TRUE; 否则为 FALSE。

##  <a name="operator_gt__eq"></a>CSid:: 运算符&gt;=

比较两个安全描述符对象的相对值。

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>参数

*lhs*<br/>
(安全标识符) 或`CSid`出现在! = 运算符的左侧。 `SID`

rhs<br/>
(安全标识符) 或`CSid`出现在! = 运算符右侧的。 `SID`

### <a name="return-value"></a>返回值

如果*lhs*大于或等于*rhs*, 则为 TRUE; 否则为 FALSE。

##  <a name="operator_const_sid__star"></a>CSid:: operator const SID\*

将对象强制转换为指向`SID` (安全标识符) 结构的指针。 `CSid`

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>备注

返回`SID`结构的地址。

##  <a name="sid"></a>  CSid::Sid

`SID`将 (安全标识符) 结构作为字符串返回。

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>返回值

`SID`将结构返回为适用于显示、存储或传输的格式的字符串。 等效于[ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw)。

##  <a name="sidnameuse"></a>CSid:: SidNameUse

返回`CSid`对象状态的说明。

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>返回值

返回数据成员的值, 该值存储描述`CSid`对象状态的值。

|值|描述|
|-----------|-----------------|
|SidTypeUser|指示用户`SID` (安全标识符)。|
|SidTypeGroup|表示组`SID`。|
|SidTypeDomain|指示域`SID`。|
|SidTypeAlias|指示别名`SID`。|
|SidTypeWellKnownGroup|`SID`指示已知组的。|
|SidTypeDeletedAccount|`SID`指示已删除帐户的。|
|SidTypeInvalid|指示无效`SID`的。|
|SidTypeUnknown|指示未知`SID`类型。|
|SidTypeComputer|`SID`指示计算机的。|

### <a name="remarks"></a>备注

在调用`CSid` 以返回其状态之前,调用[CSid::LoadAccount](#loadaccount)以更新对象。`SidNameUse` `SidNameUse`不会更改对象的状态 (通过调用`LookupAccountName`或`LookupAccountSid`), 而只返回当前状态。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)<br/>
[运算符](../../atl/reference/atl-operators.md)
