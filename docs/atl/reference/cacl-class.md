---
title: "CAcl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAcl
- ATL::CAcl
- ATLSECURITY/CAcl
- ATL.CAcl
dev_langs:
- C++
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
caps.latest.revision: 21
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
ms.openlocfilehash: 52de083664c2e9ca00a140450cb43372aff28428
ms.lasthandoff: 02/24/2017

---
# <a name="cacl-class"></a>CAcl 类
此类是包装器`ACL`（访问控制列表） 结构。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAcl
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CAcl::CAccessMaskArray](#caccessmaskarray)|一个数组`ACCESS_MASK`s。|  
|[CAcl::CAceFlagArray](#caceflagarray)|一个数组`BYTE`s。|  
|[CAcl::CAceTypeArray](#cacetypearray)|一个数组`BYTE`s。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAcl::CAcl](#cacl)|构造函数。|  
|[CAcl:: ~ CAcl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAcl::GetAceCount](#getacecount)|返回数的访问控制项 (ACE) 的对象。|  
|[CAcl::GetAclEntries](#getaclentries)|检索从的访问控制列表 (ACL) 项`CAcl`对象。|  
|[CAcl::GetAclEntry](#getaclentry)|检索所有的信息中的条目`CAcl`对象。|  
|[CAcl::GetLength](#getlength)|返回的 ACL 的长度。|  
|[CAcl::GetPACL](#getpacl)|返回程序包 （指针的 acl）。|  
|[CAcl::IsEmpty](#isempty)|测试`CAcl`条目的对象。|  
|[CAcl::IsNull](#isnull)|返回的状态`CAcl`对象。|  
|[CAcl::RemoveAce](#removeace)|从中删除特定的 ACE （访问控制项）`CAcl`对象。|  
|[CAcl::RemoveAces](#removeaces)|从中移除所有 Ace （访问控制项）`CAcl`适用于给定`CSid`。|  
|[CAcl::SetEmpty](#setempty)|标记`CAcl`对象为空。|  
|[CAcl::SetNull](#setnull)|标记`CAcl`对象作为`NULL`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CAcl::operator const ACL *](#operator_const_acl__star)|强制转换`CAcl`对象传递给`ACL`结构。|  
|[CAcl::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 **ACL**结构是一个 ACL （访问控制列表） 的标头。 ACL 包括零个或多的顺序列表[Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868) （访问控制项）。 在 ACL 中的各个 Ace 编号从 0 到*n-1*，其中*n*是 ACL 中 Ace 的数量。 在编辑 ACL 时，应用程序指的 ACL 中的访问控制项 (ACE) 按照其索引。  
  
 有两个 ACL 类型︰  
  
-   自定义  
  
-   系统  
  
 自由 ACL 控制由对象的所有者或任何人授予**WRITE_DAC**对对象的访问。 它指定访问特定用户和组可以具有的对象。 例如，文件的所有者可以使用任意 ACL 来控制哪些用户和组可以和不能有权访问该文件。  
  
 对象也具有与其关联的系统 ACL 由系统管理员控制窗体中的系统级别的安全信息。 系统 ACL 可以允许系统管理员联系以审核任何尝试获得对象的访问权限。  
  
 有关详细信息，请参阅[ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)中的讨论[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="a-namecaccessmaskarraya--caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray  
 ACCESS_MASK 对象的数组。  
  
```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```  
  
### <a name="remarks"></a>备注  
 此 typedef 指定可用来将使用的访问权限存储在访问控制项 (Ace) 的数组类型。  
  
##  <a name="a-namecaceflagarraya--caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray  
 一个字节数组。  
  
```
typedef CAtlArray<BYTE> CAceFlagArray;
```  
  
### <a name="remarks"></a>备注  
 此 typedef 指定用来定义访问控制项 (ACE) 特定于类型的控制标志的数组类型。 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)的可能的标志的完整列表的定义。  
  
##  <a name="a-namecacetypearraya--caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray  
 一个字节数组。  
  
```
typedef CAtlArray<BYTE> CAceTypeArray;
```  
  
### <a name="remarks"></a>备注  
 此 typedef 指定用来定义访问控制项 (ACE) 对象，如 ACCESS_ALLOWED_ACE_TYPE 或 ACCESS_DENIED_ACE_TYPE 的特性的数组类型。 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)可能的类型定义的完整列表。  
  
##  <a name="a-namecacla--caclcacl"></a><a name="cacl"></a>CAcl::CAcl  
 构造函数。  
  
```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 一个现有的 `CAcl` 对象。  
  
### <a name="remarks"></a>备注  
 `CAcl`对象可以根据需要使用创建的现有`CAcl`对象。  
  
##  <a name="a-namedtora--caclcacl"></a><a name="dtor"></a>CAcl:: ~ CAcl  
 析构函数。  
  
```
virtual ~CAcl() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放由对象中获取所有资源。  
  
##  <a name="a-namegetacecounta--caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount  
 返回数的访问控制项 (ACE) 的对象。  
  
```
virtual UINT GetAceCount() const throw() = 0;
```  
  
### <a name="return-value"></a>返回值  
 返回的 ACE 中的条目数`CAcl`对象。  
  
##  <a name="a-namegetaclentriesa--caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEntries  
 检索从的访问控制列表 (ACL) 项`CAcl`对象。  
  
```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSids`  
 指向数组的指针[CSid](../../atl/reference/csid-class.md)对象。  
  
 *pAccessMasks*  
 访问掩码中。  
  
 *pAceTypes*  
 访问控制项 ( **ACE**) 类型。  
  
 *pAceFlags*  
 **ACE**标志。  
  
### <a name="remarks"></a>备注  
 此方法填充数组参数使用的详细信息的每个**ACE**对象中包含`CAcl`对象。 不需要该特定的数组的详细信息时，请使用空值。  
  
 每个数组的内容彼此对应，即，第一个元素的`CAccessMaskArray`数组与中的第一个元素相对应`CSidArray`数组中，依次类推。  
  
 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)有关的 ACE 类型和标志的详细信息。  
  
##  <a name="a-namegetaclentrya--caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry  
 检索所有访问控制列表 (ACL) 中的项有关的信息。  
  
```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要检索的 ACL 项的索引。  
  
 `pSid`  
 [CSid](../../atl/reference/csid-class.md) ACL 条目应用到对象。  
  
 *pMask*  
 在指定的权限来授予或拒绝访问掩码。  
  
 `pType`  
 ACE 类型中。  
  
 `pFlags`  
 ACE 的标志。  
  
 `pObjectType`  
 对象类型。 这将设置为 GUID_NULL，如果该 ACE 中未指定的对象类型，或如果 ACE 不是对象 ACE。  
  
 `pInheritedObjectType`  
 继承的对象类型。 这将设置为 GUID_NULL，如果该 ACE 中未指定继承的对象类型，或如果 ACE 不是对象 ACE。  
  
### <a name="remarks"></a>备注  
 此方法将检索所有单独的 ACE，提供更多消息有关的信息[CAcl::GetAclEntries](#getaclentries)单独提供。  
  
 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)有关的 ACE 类型和标志的详细信息。  
  
##  <a name="a-namegetlengtha--caclgetlength"></a><a name="getlength"></a>CAcl::GetLength  
 返回的访问控制列表 (ACL) 的长度。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回以字节为单位的所需的长度保存所需**ACL**结构。  
  
##  <a name="a-namegetpacla--caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL  
 返回到访问控制列表 (ACL) 的指针。  
  
```
const ACL* GetPACL() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向**ACL**结构。  
  
##  <a name="a-nameisemptya--caclisempty"></a><a name="isempty"></a>CAcl::IsEmpty  
 测试`CAcl`条目的对象。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="remarks"></a>备注  
 返回**true**如果`CAcl`对象不为 NULL，并且不包含任何条目。 返回**false**如果`CAcl`对象为 NULL，或包含至少一个条目。  
  
##  <a name="a-nameisnulla--caclisnull"></a><a name="isnull"></a>CAcl::IsNull  
 返回的状态`CAcl`对象。  
  
```
bool IsNull() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果`CAcl`对象为 NULL， **false**否则为。  
  
##  <a name="a-nameoperatorconstaclstara--cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl::operator const ACL *  
 强制转换`CAcl`对象传递给**ACL** （访问控制列表） 结构。  
  
```  
operator const ACL *() const throw(...);
```  
  
### <a name="remarks"></a>备注  
 返回的地址**ACL**结构。  
  
##  <a name="a-nameoperatoreqa--cacloperator-"></a><a name="operator_eq"></a>CAcl::operator =  
 赋值运算符。  
  
```
CAcl& operator= (const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CAcl`要分配给现有的对象。  
  
### <a name="return-value"></a>返回值  
 返回对已更新的引用`CAcl`对象。  
  
##  <a name="a-nameremoveacea--caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce  
 从中删除特定的 ACE （访问控制项） **CAcl**对象。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要移除的 ACE 项的索引。  
  
### <a name="remarks"></a>备注  
 此方法从派生[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="a-nameremoveacesa--caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces  
 从中移除 alls Ace （访问控制项）`CAcl`适用于给定`CSid`。  
  
```
bool RemoveAces(const CSid& rSid) throw(...)
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 对 `CSid` 对象的引用。  
  
##  <a name="a-namesetemptya--caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty  
 标记`CAcl`对象为空。  
  
```
void SetEmpty() throw();
```  
  
### <a name="remarks"></a>备注  
 `CAcl`可以设置为空或为 NULL︰ 两个状态并不相同。  
  
##  <a name="a-namesetnulla--caclsetnull"></a><a name="setnull"></a>CAcl::SetNull  
 标记`CAcl`对象为 NULL。  
  
```
void SetNull() throw();
```  
  
### <a name="remarks"></a>备注  
 `CAcl`可以设置为空或为 NULL︰ 两个状态并不相同。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)

