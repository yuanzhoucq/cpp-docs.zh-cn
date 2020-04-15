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
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330913"
---
# <a name="csid-class"></a>CSid 类

此类是`SID`（安全标识符）结构的包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CSid
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CSid：CSidArray](#csidarray)|一个 `CSid` 对象数组。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSid：CSid](#csid)|构造函数。|
|[CSid：_CSid](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSid：：帐户名称](#accountname)|返回与`CSid`对象关联的帐户的名称。|
|[CSid：:D奥曼](#domain)|返回与`CSid`对象关联的域的名称。|
|[CSid：等于前缀](#equalprefix)|相等`SID`性测试（安全标识符）前缀。|
|[CSid：获取长度](#getlength)|返回`CSid`对象的长度。|
|[CSid：GetPSID](#getpsid)|返回指向结构的`SID`指针。|
|[CSid：：GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|返回指向结构的`SID_IDENTIFIER_AUTHORITY`指针。|
|[CSid：获取子授权](#getsubauthority)|返回结构中的指定子颁发机构`SID`。|
|[CSid：获取子授权计数](#getsubauthoritycount)|返回子颁发机构计数。|
|[CSid：有效](#isvalid)|测试`CSid`对象的有效性。|
|[CSid：：加载帐户](#loadaccount)|更新给定`CSid`帐户名称和域或现有`SID`结构的对象。|
|[CSid：*Ssid](#sid)|返回 ID 字符串。|
|[CSid：：SidNameUse](#sidnameuse)|返回`CSid`对象状态的说明。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 |](#operator_eq)|赋值运算符。|
|[操作员 CONst SID |](#operator_const_sid__star)|将`CSid`对象转换为指向结构的`SID`指针。|

### <a name="global-operators"></a>全球运营商

|||
|-|-|
|[运算符 |](#operator_eq_eq)|测试两个安全描述符对象是否相等|
|[操作员 ！]](#operator_neq)|测试两个安全描述符对象是否不等式|
|[算子\<](#operator_lt)|比较两个安全描述符对象的相对值。|
|[运算符>](#operator_gt)|比较两个安全描述符对象的相对值。|
|[算子\<=](#operator_lt__eq)|比较两个安全描述符对象的相对值。|
|[操作员>|](#operator_gt__eq)|比较两个安全描述符对象的相对值。|

## <a name="remarks"></a>备注

结构`SID`是一种可变长度结构，用于唯一标识用户或组。

应用程序不应直接修改`SID`结构，而应使用此包装类中提供的方法。 另见[AtlGetOwnerSid](security-global-functions.md#atlgetownersid)AtlGetOwnerSid，AtlSetGroupSid，AtlGetGroupSid，和[AtlSetOwnerSid。](security-global-functions.md#atlsetownersid) [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid) [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid：：帐户名称

返回与`CSid`对象关联的帐户的名称。

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向帐户名称的 LPCTSTR。

### <a name="remarks"></a>备注

此方法尝试查找指定`SID`的名称（安全标识符）。 有关详细信息，请参阅[查找帐户 Sid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到 的`SID`帐户名称，则`AccountName`返回一个空字符串。 如果网络超时阻止此方法查找名称，则可能发生此情况。 对于没有相应帐户名称的安全标识符（如标识登录会话`SID`的安全标识符）也会发生这种情况。

## <a name="csidcsid"></a><a name="csid"></a>CSid：CSid

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

rhs**<br/>
现有`CSid`对象或`SID`（安全标识符）结构。

*标识符颁发机构*<br/>
权威。

*nSubAuthorityCount*<br/>
子颁发机构计数。

*psz帐户名称*<br/>
帐户名称。

*psz系统*<br/>
系统名称。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL，则改为使用本地系统。

*pSid*<br/>
指向结构的`SID`指针。

### <a name="remarks"></a>备注

`CSid`构造函数初始化对象，将内部数据成员设置为*SidTypeInvalid，* 或通过从现有`CSid`、或`SID`现有帐户复制设置。

如果初始化失败，构造函数将引发[CAtlException 类](../../atl/reference/catlexception-class.md)。

## <a name="csidcsid"></a><a name="dtor"></a>CSid：_CSid

析构函数。

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>备注

析构函数释放对象获取的任何资源。

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid：CSidArray

[CSid](../../atl/reference/csid-class.md)对象的数组。

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>备注

此 typedef 指定可用于从 ACL（访问控制列表）检索安全标识符的数组类型。 请参阅[CAcl：获取 Acl 条目](../../atl/reference/cacl-class.md#getaclentries)。

## <a name="csiddomain"></a><a name="domain"></a>CSid：:D奥曼

返回与`CSid`对象关联的域的名称。

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向`LPCTSTR`域的指针。

### <a name="remarks"></a>备注

此方法尝试查找指定`SID`的名称（安全标识符）。 有关详细信息，请参阅[查找帐户 Sid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到 的`SID`帐户名称，`Domain`则将域作为空字符串返回。 如果网络超时阻止此方法查找名称，则可能发生此情况。 对于没有相应帐户名称的安全标识符（如标识登录会话`SID`的安全标识符）也会发生这种情况。

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid：等于前缀

相等`SID`性测试（安全标识符）前缀。

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>参数

rhs**<br/>
要`SID`比较的（安全标识符）`CSid`结构或对象。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EqualPrefixSid。](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid)

## <a name="csidgetlength"></a><a name="getlength"></a>CSid：获取长度

返回`CSid`对象的长度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>返回值

返回`CSid`对象的长度（以字节为单位）。

### <a name="remarks"></a>备注

如果`CSid`结构无效，则返回值未定义。 在调用`GetLength`之前，使用[CSid：：IsValid](#isvalid)成员函数来`CSid`验证该函数是否有效。

> [!NOTE]
> 在调试生成下，如果对象无效，`CSid`该函数将导致 ASSERT。

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid：GetPSID

返回指向（安全标识符`SID`）结构的指针。

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>返回值

返回`CSid`对象的基础`SID`结构的地址。

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid：：GetPSID_IDENTIFIER_AUTHORITY

返回指向结构的`SID_IDENTIFIER_AUTHORITY`指针。

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>返回值

如果该方法成功，它将返回结构的地址`SID_IDENTIFIER_AUTHORITY`。 如果失败，则返回值未定义。 如果对象无效，`CSid`则可能发生失败，在这种情况下[，CSid：：isValid](#isvalid)方法将返回 FALSE。 可以调用`GetLastError`该函数以提供扩展的错误信息。

> [!NOTE]
> 在调试生成下，如果对象无效，`CSid`该函数将导致 ASSERT。

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid：获取子授权

返回`SID`（安全标识符）结构中的指定子颁发机构。

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>参数

*nSubAuthority*<br/>
子颁发机构。

### <a name="return-value"></a>返回值

返回*nSubAuthority*引用的子颁发机构。 子颁发者值是相对标识符 （RID）。

### <a name="remarks"></a>备注

*nSubAuthority*参数指定一个索引值，用于标识方法将返回的子权威数组元素。 该方法不执行此值的验证测试。 应用程序可以调用[CSid：：获取 SubAuthorityCount 以](#getsubauthoritycount)发现可接受的值的范围。

> [!NOTE]
> 在调试生成下，如果对象无效，`CSid`该函数将导致 ASSERT。

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid：获取子授权计数

返回子颁发机构计数。

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>返回值

如果该方法成功，则返回值为子颁发机构计数。

如果方法失败，则返回值未定义。 如果对象无效，`CSid`该方法将失败。 若要获得扩展的错误信息，请调用 `GetLastError`。

> [!NOTE]
> 在调试生成下，如果对象无效，`CSid`该函数将导致 ASSERT。

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid：有效

测试`CSid`对象的有效性。

```
bool IsValid() const throw();
```

### <a name="return-value"></a>返回值

如果对象有效，`CSid`则返回 TRUE，如果无效，则返回 FALSE。 此方法没有扩展的错误信息;因此，此方法没有扩展错误信息。不调用`GetLastError`。

### <a name="remarks"></a>备注

该方法`IsValid`通过验证修订编号`CSid`是否在已知范围内以及子权限数小于最大值来验证对象。

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid：：加载帐户

更新给定`CSid`帐户名称和域或现有 SID（安全标识符）结构的对象。

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>参数

*psz帐户名称*<br/>
帐户名称。

*psz系统*<br/>
系统名称。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL，则改为使用本地系统。

*pSid*<br/>
指向[SID](/windows/win32/api/winnt/ns-winnt-sid)结构的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。 若要获得扩展的错误信息，请调用 `GetLastError`。

### <a name="remarks"></a>备注

`LoadAccount`尝试查找指定名称的安全标识符。 有关详细信息[，请参阅查找帐户Sid。](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid：：运算符 |

赋值运算符。

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
`SID` （安全标识符）或`CSid`要分配给`CSid`对象。

### <a name="return-value"></a>返回值

返回对更新`CSid`对象的引用。

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid：：运算符 |

测试两个安全描述符对象是否相等。

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
或`SID`显示在 _ 运算符`CSid`左侧的（安全标识符）。

rhs**<br/>
（`SID`安全标识符）或`CSid`显示在 _ 运算符右侧的。。

### <a name="return-value"></a>返回值

如果安全描述符相等，则为 TRUE，否则为 FALSE。

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid：：操作员！*

测试两个安全描述符对象是否不平等。

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
（`SID`安全标识符）或`CSid`显示在 ！+ 运算符左侧的。。

rhs**<br/>
（`SID`安全标识符）或`CSid`显示在 ！# 运算符右侧的。。

### <a name="return-value"></a>返回值

如果安全描述符不相等，则为 TRUE，否则为 FALSE。

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid：：运算符&lt;

比较两个安全描述符对象的相对值。

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
（`SID`安全标识符）或`CSid`显示在 ！+ 运算符左侧的。。

rhs**<br/>
（`SID`安全标识符）或`CSid`显示在 ！# 运算符右侧的。。

### <a name="return-value"></a>返回值

如果*lhs*小于*rhs，* 则为 TRUE，否则为 FALSE。

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid：：运算符&lt;=

比较两个安全描述符对象的相对值。

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
（`SID`安全标识符）或`CSid`显示在 ！+ 运算符左侧的。。

rhs**<br/>
（`SID`安全标识符）或`CSid`显示在 ！# 运算符右侧的。。

### <a name="return-value"></a>返回值

如果*lhs*小于或等于*rhs，* 则为 TRUE，否则为 FALSE。

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid：：运算符&gt;

比较两个安全描述符对象的相对值。

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
（`SID`安全标识符）或`CSid`显示在 ！+ 运算符左侧的。。

rhs**<br/>
（`SID`安全标识符）或`CSid`显示在 ！# 运算符右侧的。。

### <a name="return-value"></a>返回值

如果*lhs*大于*rhs，* 则为 TRUE，否则为 FALSE。

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid：：运算符&gt;=

比较两个安全描述符对象的相对值。

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>参数

*lhs*<br/>
（`SID`安全标识符）或`CSid`显示在 ！+ 运算符左侧的。。

rhs**<br/>
（`SID`安全标识符）或`CSid`显示在 ！# 运算符右侧的。。

### <a name="return-value"></a>返回值

如果*lhs*大于或等于*rhs，* 则为 TRUE，否则为 FALSE。

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid：：操作员同心SID\*

将`CSid`对象强制转换为指向（安全标识符）`SID`结构的指针。

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>备注

返回结构的地址`SID`。

## <a name="csidsid"></a><a name="sid"></a>CSid：*Ssid

将`SID`（安全标识符）结构作为字符串返回。

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>返回值

以适合`SID`显示、存储或传输的格式将结构作为字符串返回。 等效于[转换 SidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw)。

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid：：SidNameUse

返回`CSid`对象状态的说明。

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>返回值

返回存储描述`CSid`对象状态的值的数据成员的值。

|“值”|说明|
|-----------|-----------------|
|西德类型用户|指示用户`SID`（安全标识符）。|
|西德类型集团|指示组`SID`。|
|西德域|指示域`SID`。|
|西德里亚斯|指示别名`SID`。|
|西德迪韦尔·韦尔认识集团|指示已知`SID`组的 的 。|
|SidType 删除帐户|指示已`SID`删除帐户的 。|
|SidType 无效|指示无效`SID`。|
|西德类型未知|指示未知`SID`类型。|
|西德类型计算机|指示`SID`计算机的 a。|

### <a name="remarks"></a>备注

调用[CSid：：LoadAccount](#loadaccount)在`CSid`调用`SidNameUse`以返回其状态之前更新对象。 `SidNameUse`不更改对象的状态（通过调用`LookupAccountName`或`LookupAccountSid`），但仅返回当前状态。

## <a name="see-also"></a>另请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)<br/>
[运算符](../../atl/reference/atl-operators.md)
