---
title: "CSid 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ceb0ab95d18e1336584eab45bc00ce769efd7384
ms.lasthandoff: 02/24/2017

---
# <a name="csid-class"></a>CSid 类
此类是包装器`SID`（安全标识符） 结构。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CSid
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CSid::CSidArray](#csidarray)|一个 `CSid` 对象数组。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSid::CSid](#csid)|构造函数。|  
|[CSid:: ~ CSid](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSid::AccountName](#accountname)|返回与关联的帐户的名称`CSid`对象。|  
|[CSid::Domain](#domain)|返回与关联的域的名称`CSid`对象。|  
|[CSid::EqualPrefix](#equalprefix)|测试`SID`（安全标识符） 前缀的相等性。|  
|[CSid::GetLength](#getlength)|返回的长度`CSid`对象。|  
|[CSid::GetPSID](#getpsid)|返回一个指向`SID`结构。|  
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|返回一个指向**SID_IDENTIFIER_AUTHORITY**结构。|  
|[CSid::GetSubAuthority](#getsubauthority)|返回在指定个子颁发机构**SID**结构。|  
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|返回个子颁发机构计数。|  
|[CSid::IsValid](#isvalid)|测试`CSid`对象的有效性。|  
|[CSid::LoadAccount](#loadaccount)|更新`CSid`给定帐户名和域，或将现有对象`SID`结构。|  
|[CSid::Sid](#sid)|返回 ID 字符串。|  
|[CSid::SidNameUse](#sidnameuse)|返回的状态的说明`CSid`对象。|  
  
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
|[运算符\<](#operator_lt_)|将两个安全描述符对象的相关值进行比较。|  
|[运算符&1;>](#operator_gt_)|将两个安全描述符对象的相关值进行比较。|  
|[运算符\<=](#operator_lt__eq)|将两个安全描述符对象的相关值进行比较。|  
|[运算符&1;> =](#operator_gt__eq)|将两个安全描述符对象的相关值进行比较。|  
  
## <a name="remarks"></a>备注  
 `SID`结构是一种长度可变的结构，用来唯一标识用户或组。  
  
 应用程序不应修改`SID`结构直接，但改为使用此包装类中提供的方法。 另请参阅[AtlGetOwnerSid](http://msdn.microsoft.com/library/0e3a2606-74b8-4412-9803-bb437e22da85)， [AtlSetGroupSid](http://msdn.microsoft.com/library/83531d32-11ab-4a68-a3c6-1bfa54ab8dfa)， [AtlGetGroupSid](http://msdn.microsoft.com/library/8e7ec6b9-15c8-4a8a-977e-1e4c853d0be7)，和[AtlSetOwnerSid](http://msdn.microsoft.com/library/3a8abb76-1d2c-465d-a5e8-62a12a3c37f3)。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="accountname"></a>CSid::AccountName  
 返回与关联的帐户的名称`CSid`对象。  
  
```
LPCTSTR AccountName() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回`LPCTSTR`指向该帐户的名称。  
  
### <a name="remarks"></a>备注  
 此方法尝试找不到名称为指定`SID`（安全标识符）。 有关完整详细信息，请参阅[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166)。  
  
 如果没有帐户名`SID`可以找到，`AccountName`返回一个空字符串。 如果网络超时可防止此方法查找名称便会出现此问题。 它也会发生与没有相应的帐户名称，如一次登录安全标识符`SID`标识登录会话。  
  
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
 证书颁发机构。  
  
 *nSubAuthorityCount*  
 次级授权计数中。  
  
 `pszAccountName`  
 帐户名称。  
  
 `pszSystem`  
 系统名称中。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL，则改为使用本地系统。  
  
 `pSid`  
 一个指向`SID`结构。  
  
### <a name="remarks"></a>备注  
 构造函数初始化`CSid`对象，内部数据成员设置为*SidTypeInvalid*，或通过从现有复制设置`CSid`， `SID`，或现有的帐户。  
  
 如果初始化失败，构造函数将引发[CAtlException 类](../../atl/reference/catlexception-class.md)。  
  
##  <a name="dtor"></a>CSid:: ~ CSid  
 析构函数。  
  
```
virtual ~CSid() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放由对象中获取所有资源。  
  
##  <a name="csidarray"></a>CSid::CSidArray  
 一个数组[CSid](../../atl/reference/csid-class.md)对象。  
  
```
typedef CAtlArray<CSid> CSidArray;
```  
  
### <a name="remarks"></a>备注  
 此 typedef 指定可用来从一个 ACL （访问控制列表） 中检索的安全标识符的数组类型。 请参阅[CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries)。  
  
##  <a name="domain"></a>CSid::Domain  
 返回与关联的域的名称`CSid`对象。  
  
```
LPCTSTR Domain() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回`LPCTSTR`指向域。  
  
### <a name="remarks"></a>备注  
 此方法尝试找不到名称为指定`SID`（安全标识符）。 有关完整详细信息，请参阅[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166)。  
  
 如果没有帐户名`SID`找，**域**返回为空字符串的域。 如果网络超时可防止此方法查找名称便会出现此问题。 它也会发生与没有相应的帐户名称，如一次登录安全标识符`SID`标识登录会话。  
  
##  <a name="equalprefix"></a>CSid::EqualPrefix  
 测试`SID`（安全标识符） 前缀的相等性。  
  
```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `SID` （安全标识符） 结构或`CSid`对象进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**成功时， **false**失败。  
  
### <a name="remarks"></a>备注  
 请参阅[EqualPrefixSid](http://msdn.microsoft.com/library/windows/desktop/aa446621)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的更多详细信息。  
  
##  <a name="getlength"></a>CSid::GetLength  
 返回的长度`CSid`对象。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的长度以字节为单位的`CSid`对象。  
  
### <a name="remarks"></a>备注  
 如果`CSid`结构无效，则返回值是不确定。 之前，先调用`GetLength`，使用[CSid::IsValid](#isvalid)成员函数，以验证`CSid`是否有效。  
  
> [!NOTE]
>  在下，如果该函数将导致断言的调试版本`CSid`对象无效。  
  
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
 如果该方法成功，则返回的地址**SID_IDENTIFIER_AUTHORITY**结构。 如果失败，则返回值是不确定。 如果故障可能会发生`CSid`对象不是有效的在这种情况下[CSid::IsValid](#isvalid)方法将返回**false**。 该函数`GetLastError`可以调用扩展的错误的信息。  
  
> [!NOTE]
>  在下，如果该函数将导致断言的调试版本`CSid`对象无效。  
  
##  <a name="getsubauthority"></a>CSid::GetSubAuthority  
 返回在指定个子颁发机构`SID`（安全标识符） 结构。  
  
```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```  
  
### <a name="parameters"></a>参数  
 *nSubAuthority*  
 个子颁发机构。  
  
### <a name="return-value"></a>返回值  
 返回由引用次级授权*nSubAuthority。* 次级授权值是相对标识符 (RID)。  
  
### <a name="remarks"></a>备注  
 *NSubAuthority*参数指定用于标识该方法将返回的子数组元素的索引值。 该方法对该值执行不进行任何验证测试。 应用程序可以调用[CSid::GetSubAuthorityCount](#getsubauthoritycount)要搜索范围的可接受的值。  
  
> [!NOTE]
>  在下，如果该函数将导致断言的调试版本`CSid`对象无效。  
  
##  <a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount  
 返回个子颁发机构计数。  
  
```
UCHAR GetSubAuthorityCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值将是个子颁发机构计数。  
  
 如果此方法失败，则返回值不确定。 如果此方法失败`CSid`对象无效。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
> [!NOTE]
>  在下，如果该函数将导致断言的调试版本`CSid`对象无效。  
  
##  <a name="isvalid"></a>CSid::IsValid  
 测试`CSid`对象的有效性。  
  
```
bool IsValid() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果`CSid`对象是否有效， **false**如果不是。 此方法; 没有更多的错误信息不要调用`GetLastError`。  
  
### <a name="remarks"></a>备注  
 `IsValid`方法验证`CSid`通过验证的修订号是已知的范围内，且次级机构数小于最大值的对象。  
  
##  <a name="loadaccount"></a>CSid::LoadAccount  
 更新`CSid`对象的具有给定的帐户名和域或现有的 SID （安全标识符） 结构。  
  
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
 帐户名称。  
  
 `pszSystem`  
 系统名称中。 此字符串可以是远程计算机的名称。 如果此字符串为 NULL，则改为使用本地系统。  
  
 `pSid`  
 一个指向[SID](http://msdn.microsoft.com/library/windows/desktop/aa379594\(v=vs.85\).aspx)结构。  
  
### <a name="return-value"></a>返回值  
 返回**true**成功时， **false**失败。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
### <a name="remarks"></a>备注  
 `LoadAccount`尝试查找指定名称的安全标识符。 请参阅[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166\(v=vs.85\).aspx)的更多详细信息。  
  
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
 测试两个安全描述符对象相等。  
  
```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`出现在左侧的 = = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`右侧显示 = = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果安全描述符是否相等，否则**false**。  
  
##  <a name="operator_neq"></a>CSid::operator ！ =  
 测试不相等的两个安全描述符对象。  
  
```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`出现在左侧的内容 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`右侧上出现 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果安全描述符不相等，否则**false**。  
  
##  <a name="operator_lt"></a>CSid::operator&lt;  
 将两个安全描述符对象的相关值进行比较。  
  
```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`出现在左侧的内容 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`右侧上出现 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`是小于`rhs`，否则为**false**。  
  
##  <a name="operator_lt__eq"></a>CSid::operator&lt;=  
 将两个安全描述符对象的相关值进行比较。  
  
```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`出现在左侧的内容 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`右侧上出现 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`是否小于或等于`rhs`，否则为**false**。  
  
##  <a name="operator_gt"></a>CSid::operator&gt;  
 将两个安全描述符对象的相关值进行比较。  
  
```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`出现在左侧的内容 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`右侧上出现 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`大于`rhs`，否则为**false**。  
  
##  <a name="operator_gt__eq"></a>CSid::operator&gt;=  
 将两个安全描述符对象的相关值进行比较。  
  
```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 `SID` （安全标识符） 或`CSid`出现在左侧的内容 ！ = 运算符。  
  
 `rhs`  
 `SID` （安全标识符） 或`CSid`右侧上出现 ！ = 运算符。  
  
### <a name="return-value"></a>返回值  
 **true**如果`lhs`是否大于或等于`rhs`，否则为**false**。  
  
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
 返回`SID`以适合显示、 存储或传输的格式的字符串的结构。 等效于[ConvertSidToStringSid](http://msdn.microsoft.com/library/windows/desktop/aa376399)，尽管此函数才位于 Windows 2000 或更高版本，因此模拟早期版本操作系统。  
  
##  <a name="sidnameuse"></a>CSid::SidNameUse  
 返回的状态的说明`CSid`对象。  
  
```
SID_NAME_USE SidNameUse() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回存储所描述的状态的值的数据成员的值`CSid`对象。  
  
|值|描述|  
|-----------|-----------------|  
|SidTypeUser|指示用户`SID`（安全标识符）。|  
|SidTypeGroup|表示一组`SID`。|  
|SidTypeDomain|表示一个域`SID`。|  
|SidTypeAlias|指示别名`SID`。|  
|SidTypeWellKnownGroup|指示`SID`为人所熟知的组。|  
|SidTypeDeletedAccount|指示`SID`已删除帐户。|  
|SidTypeInvalid|指示无效`SID`。|  
|SidTypeUnknown|指示未知`SID`类型。|  
|SidTypeComputer|指示`SID`计算机。|  
  
### <a name="remarks"></a>备注  
 调用[CSid::LoadAccount](#loadaccount)更新`CSid`对象之前调用`SidNameUse`以返回其状态。 `SidNameUse`不会更改对象的状态 (通过调用到**LookupAccountName**或**LookupAccountSid**)，但仅返回当前状态。  
  
## <a name="see-also"></a>另请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)   
 [运算符](../../atl/reference/atl-operators.md)

