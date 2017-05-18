---
title: "CSid 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: f1e731c82892c5622dcb437498d2d318086f66d8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="csid-class"></a>CSid 类
此类是包装器`SID`（安全标识符） 结构。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CSid
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CSid::CSidArray](#csidarray)|一个 `CSid` 对象数组。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSid::CSid](#csid)|构造函数。|  
|[CSid:: ~ CSid](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSid::AccountName](#accountname)|返回与关联的帐户的名称`CSid`对象。|  
|[CSid::Domain](#domain)|返回与关联的域的名称`CSid`对象。|  
|[CSid::EqualPrefix](#equalprefix)|测试`SID`（安全标识符） 前缀是否相等。|  
|[CSid::GetLength](#getlength)|返回的长度`CSid`对象。|  
|[CSid::GetPSID](#getpsid)|返回一个指向`SID`结构。|  
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|返回一个指向**SID_IDENTIFIER_AUTHORITY**结构。|  
|[CSid::GetSubAuthority](#getsubauthority)|返回在指定的授权**SID**结构。|  
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|返回的子计数。|  
|[CSid::IsValid](#isvalid)|测试`CSid`有效性的对象。|  
|[CSid::LoadAccount](#loadaccount)|更新`CSid`给定帐户名称和域或的现有对象`SID`结构。|  
|[CSid::Sid](#sid)|返回的 ID 字符串。|  
|[CSid::SidNameUse](#sidnameuse)|返回的状态的描述`CSid`对象。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|赋值运算符。|  
|[运算符 const SID *](#operator_const_sid__star)|强制转换`CSid`对象的指针到`SID`结构。|  
  
### <a name="global-operators"></a>全局运算符  
  
|||  
|-|-|  
|[运算符 = =](#operator_eq_eq)|测试相等的两个安全描述符对象|  
|[运算符 ！ =](#operator_neq)|测试不相等的两个安全描述符对象|  
|[运算符\<](#operator_lt_)|比较两个安全描述符对象的相对值。|  
|[运算符 1>](#operator_gt_)|比较两个安全描述符对象的相对值。|  
|[运算符\<=](#operator_lt__eq)|比较两个安全描述符对象的相对值。|  
|[运算符 1> =](#operator_gt__eq)|比较两个安全描述符对象的相对值。|  
  
## <a name="remarks"></a>备注  
 `SID`结构是用于唯一标识用户或组的长度可变的结构。  
  
 应用程序不应修改`SID`结构直接，但改为使用此包装类中提供的方法。 另请参阅[AtlGetOwnerSid](security-global-functions.md#atlgetownersid)， [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid)， [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)，和[AtlSetOwnerSid](security-global-functions.md#atlsetownersid)。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="accountname"></a>CSid::AccountName  
 返回与关联的帐户的名称`CSid`对象。  
  
```
LPCTSTR AccountName() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回`LPCTSTR`指向帐户的名称。  
  
### <a name="remarks"></a>备注  
 此方法尝试查找指定的名称`SID`（安全标识符）。 有关完整详细信息，请参阅[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166)。  
  
 如果没有帐户名`SID`可以找到，`AccountName`返回空字符串。 如果是网络超时可防止此方法查找名称便会出现此问题。 没有相应的帐户名称，如登录安全标识符也会出现`SID`标识登录会话。  
  
##  <a name="csid"></a>CSid::CSid  
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
 `rhs`  
 现有`CSid`对象或`SID`（安全标识符） 结构。  
  
 *IdentifierAuthority*  
 颁发机构。  
  
 *nSubAuthorityCount*  
 次级授权计数中。  
  
 `pszAccountName`  
 帐户名称中。  
  
 `pszSystem`  
 系统名称中。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL，则改为使用本地系统。  
  
 `pSid`  
 指向的指针`SID`结构。  
  
### <a name="remarks"></a>备注  
 构造函数初始化`CSid`对象，将内部数据成员设置为*SidTypeInvalid*，或通过从现有复制设置`CSid`， `SID`，或现有的帐户。  
  
 如果初始化失败，构造函数将引发[CAtlException 类](../../atl/reference/catlexception-class.md)。  
  
##  <a name="dtor"></a>CSid:: ~ CSid  
 析构函数。  
  
```
virtual ~CSid() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放由对象获取任何资源。  
  
##  <a name="csidarray"></a>CSid::CSidArray  
 数组[CSid](../../atl/reference/csid-class.md)对象。  
  
```
typedef CAtlArray<CSid> CSidArray;
```  
  
### <a name="remarks"></a>备注  
 此 typedef 指定可以用于从 ACL （访问控制列表） 中检索安全标识符的数组类型。 请参阅[CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries)。  
  
##  <a name="domain"></a>CSid::Domain  
 返回与关联的域的名称`CSid`对象。  
  
```
LPCTSTR Domain() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回`LPCTSTR`指向域。  
  
### <a name="remarks"></a>备注  
 此方法尝试查找指定的名称`SID`（安全标识符）。 有关完整详细信息，请参阅[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166)。  
  
 如果没有帐户名`SID`可以找到，**域**返回为一个空字符串的域。 如果是网络超时可防止此方法查找名称便会出现此问题。 没有相应的帐户名称，如登录安全标识符也会出现`SID`标识登录会话。  
  
##  <a name="equalprefix"></a>CSid::EqualPrefix  
 测试`SID`（安全标识符） 前缀是否相等。  
  
```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `SID` （安全标识符） 结构或`CSid`要比较的对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**成功后， **false**失败。  
  
### <a name="remarks"></a>备注  
 请参阅[EqualPrefixSid](http://msdn.microsoft.com/library/windows/desktop/aa446621)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="getlength"></a>CSid::GetLength  
 返回的长度`CSid`对象。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回以字节为单位的长度`CSid`对象。  
  
### <a name="remarks"></a>备注  
 如果`CSid`结构无效，则返回值不确定。 之前调用`GetLength`，使用[CSid::IsValid](#isvalid)成员函数，以便确认`CSid`有效。  
  
> [!NOTE]
>  在调试版本中，如果该函数将导致断言`CSid`对象无效。  
  
##  <a name="getpsid"></a>CSid::GetPSID  
 返回一个指向`SID`（安全标识符） 结构。  
  
```
const SID* GetPSID() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回的地址`CSid`对象的基本`SID`结构。  
  
##  <a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY  
 返回一个指向**SID_IDENTIFIER_AUTHORITY**结构。  
  
```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回的地址**SID_IDENTIFIER_AUTHORITY**结构。 如果失败，则返回的值不确定。 如果失败可能会出现`CSid`对象不是有效，在这种情况下[CSid::IsValid](#isvalid)方法返回**false**。 该函数`GetLastError`可以调用为扩展的错误信息。  
  
> [!NOTE]
>  在调试版本中，如果该函数将导致断言`CSid`对象无效。  
  
##  <a name="getsubauthority"></a>CSid::GetSubAuthority  
 返回在指定的授权`SID`（安全标识符） 结构。  
  
```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```  
  
### <a name="parameters"></a>参数  
 *nSubAuthority*  
 次级授权。  
  
### <a name="return-value"></a>返回值  
 返回引用的子*nSubAuthority。* 次级授权值是相对标识符 (RID)。  
  
### <a name="remarks"></a>备注  
 *NSubAuthority*参数指定标识该方法将返回的子数组元素的索引值。 方法对此值执行任何验证测试。 应用程序可以调用[CSid::GetSubAuthorityCount](#getsubauthoritycount)要搜索范围的可接受的值。  
  
> [!NOTE]
>  在调试版本中，如果该函数将导致断言`CSid`对象无效。  
  
##  <a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount  
 返回的子计数。  
  
```
UCHAR GetSubAuthorityCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，返回值将是子计数。  
  
 如果此方法失败，返回的值不确定。 如果此方法失败`CSid`对象无效。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
> [!NOTE]
>  在调试版本中，如果该函数将导致断言`CSid`对象无效。  
  
##  <a name="isvalid"></a>CSid::IsValid  
 测试`CSid`有效性的对象。  
  
```
bool IsValid() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果`CSid`对象是否有效， **false**如果不是。 没有为此方法; 扩展的错误信息不要调用`GetLastError`。  
  
### <a name="remarks"></a>备注  
 `IsValid`方法验证`CSid`通过验证修订号处于已知的范围内，以及次级机构数是否小于最大值的对象。  
  
##  <a name="loadaccount"></a>CSid::LoadAccount  
 更新`CSid`给定帐户名称和域或现有的 SID （安全标识符） 结构的对象。  
  
```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszAccountName`  
 帐户名称中。  
  
 `pszSystem`  
 系统名称中。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL，则改为使用本地系统。  
  
 `pSid`  
 指向的指针[SID](http://msdn.microsoft.com/library/windows/desktop/aa379594\(v=vs.85\).aspx)结构。  
  
### <a name="return-value"></a>返回值  
 返回**true**成功后， **false**失败。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
### <a name="remarks"></a>备注  
 `LoadAccount`尝试查找安全标识符指定的名称。 请参阅[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166\(v=vs.85\).aspx)有关详细信息。  
  
##  <a name="operator_eq"></a>CSid::operator =  
 赋值运算符。  
  
```
CSid& operator= (const CSid& rhs) throw(...);  
CSid& operator= (const SID& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `SID` （安全标识符） 或`CSid`要分配给`CSid`对象。  
  
### <a name="return-value"></a>返回值  
 返回对已更新的引用`CSid`对象。  
  
##  <a name="operator_eq_eq"></a>CSid::operator = =  
 测试相等的两个安全描述符对象。  
  
```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`的左侧显示 = = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`的右侧显示 = = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**的安全描述符是否相等，否则如果**false**。  
  
##  <a name="operator_neq"></a>CSid::operator ！ =  
 测试不相等的两个安全描述符对象。  
  
```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`的左侧显示 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`的右侧显示 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果的安全描述符不相等，否则**false**。  
  
##  <a name="operator_lt"></a>CSid::operator&lt;  
 比较两个安全描述符对象的相对值。  
  
```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`的左侧显示 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`的右侧显示 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`是小于`rhs`，否则为**false**。  
  
##  <a name="operator_lt__eq"></a>CSid::operator&lt;=  
 比较两个安全描述符对象的相对值。  
  
```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`的左侧显示 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`的右侧显示 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`小于或等于`rhs`，否则为**false**。  
  
##  <a name="operator_gt"></a>CSid::operator&gt;  
 比较两个安全描述符对象的相对值。  
  
```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`的左侧显示 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`的右侧显示 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`大于`rhs`，否则为**false**。  
  
##  <a name="operator_gt__eq"></a>CSid::operator&gt;=  
 比较两个安全描述符对象的相对值。  
  
```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`的左侧显示 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`的右侧显示 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`大于或等于`rhs`，否则为**false**。  
  
##  <a name="operator_const_sid__star"></a>CSid::operator const SID *  
 强制转换`CSid`对象的指针到`SID`（安全标识符） 结构。  
  
```  
operator const SID *() const throw(...);
```  
  
### <a name="remarks"></a>备注  
 返回的地址`SID`结构。  
  
##  <a name="sid"></a>CSid::Sid  
 返回`SID`（安全标识符） 作为字符串的结构。  
  
```
LPCTSTR Sid() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回`SID`作为适用于显示、 存储或传输的格式字符串的结构。 等效于[ConvertSidToStringSid](http://msdn.microsoft.com/library/windows/desktop/aa376399)，尽管此函数是仅可在 Windows 2000 或更高版本，因此被模拟的早期版本的操作系统。  
  
##  <a name="sidnameuse"></a>CSid::SidNameUse  
 返回的状态的描述`CSid`对象。  
  
```
SID_NAME_USE SidNameUse() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回存储值描述的状态数据成员的值`CSid`对象。  
  
|值|描述|  
|-----------|-----------------|  
|SidTypeUser|指示用户`SID`（安全标识符）。|  
|SidTypeGroup|指示组`SID`。|  
|SidTypeDomain|表示一个域`SID`。|  
|SidTypeAlias|指示别名`SID`。|  
|SidTypeWellKnownGroup|指示`SID`的已知组。|  
|SidTypeDeletedAccount|指示`SID`已删除帐户。|  
|SidTypeInvalid|指示无效`SID`。|  
|SidTypeUnknown|指示为未知`SID`类型。|  
|SidTypeComputer|指示`SID`计算机。|  
  
### <a name="remarks"></a>备注  
 调用[CSid::LoadAccount](#loadaccount)更新`CSid`对象之前调用`SidNameUse`以返回其状态。 `SidNameUse`不会更改对象的状态 (通过调用到**LookupAccountName**或**LookupAccountSid**)，但仅返回的当前状态。  
  
## <a name="see-also"></a>另请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)   
 [运算符](../../atl/reference/atl-operators.md)

