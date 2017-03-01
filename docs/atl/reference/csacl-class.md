---
title: "CSacl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CSacl
- ATL::CSacl
- CSacl
dev_langs:
- C++
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
caps.latest.revision: 22
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
ms.openlocfilehash: 50f10ab765648d4b587a941ccf24726b53f14c88
ms.lasthandoff: 02/24/2017

---
# <a name="csacl-class"></a>CSacl 类
此类是一个 SACL （系统访问控制列表） 结构的包装器。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|构造函数。|  
|[CSacl:: ~ CSacl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|将审核访问控制项 (ACE) 添加到`CSacl`对象。|  
|[CSacl::GetAceCount](#getacecount)|在返回的访问控制项 (Ace) 数`CSacl`对象。|  
|[CSacl::RemoveAce](#removeace)|从中删除特定的 ACE （访问控制项） **CSacl**对象。|  
|[CSacl::RemoveAllAces](#removeallaces)|删除所有中包含的 Ace`CSacl`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 SACL 包含指定的域控制器的安全事件日志中生成审核记录的访问尝试类型的访问控制项 (Ace)。 请注意 SACL 生成日志项仅在访问尝试的发生位置的域控制器上，而不包含对象的副本的每个域控制器。  
  
 若要设置或检索对象的安全描述符中的 SACL，必须在请求线程的访问令牌中启用 SE_SECURITY_NAME 特权掌握。 管理员组具有默认情况下，授予此特权，可以将授予其他用户或组。 具有特权授予功能并非仅限于所需︰ 安全访问令牌中才能生效可以执行特权所定义的操作之前，必须启用特权。 该模型允许将仅用于特定的系统操作、 启用并禁用不再需要它们时的特权。 请参阅[AtlGetSacl](http://msdn.microsoft.com/library/1d69611f-d8a7-467b-9d57-cbe2f1610bf8)和[AtlSetSacl](http://msdn.microsoft.com/library/54daab9a-8c69-45fd-86c4-18eb30d59547)有关启用 SE_SECURITY_NAME 的示例。  
  
 使用类方法提供，用于添加、 删除、 创建和删除 Ace 从**SACL**对象。 另请参阅[AtlGetSacl](http://msdn.microsoft.com/library/1d69611f-d8a7-467b-9d57-cbe2f1610bf8)和[AtlSetSacl](http://msdn.microsoft.com/library/54daab9a-8c69-45fd-86c4-18eb30d59547)。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="a-nameaddauditacea--csacladdauditace"></a><a name="addauditace"></a>CSacl::AddAuditAce  
 将审核访问控制项 (ACE) 添加到`CSacl`对象。  
  
```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 [CSid](../../atl/reference/csid-class.md)对象。  
  
 `AccessMask`  
 指定要审核的访问权限的掩码指定`CSid`对象。  
  
 `bSuccess`  
 指定是否允许的访问尝试将被审核。 设置此标志设置为 true 将启用审核。否则，将其设置为 false。  
  
 *bFailure*  
 指定是否要审核被拒绝的访问尝试。 设置此标志设置为 true 将启用审核。否则，将其设置为 false。  
  
 `AceFlags`  
 一组位标志，用于控制 ACE 继承。  
  
 `pObjectType`  
 对象类型。  
  
 `pInheritedObjectType`  
 继承的对象类型。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果 ACE 添加到`CSacl`对象， **false**失败。  
  
### <a name="remarks"></a>备注  
 一个`CSacl`对象包含指定的安全事件日志中生成审核记录的访问尝试类型的访问控制项 (Ace)。 此方法将添加到此类的 ACE`CSacl`对象。 第二种形式的`AddAuditAce`才可用于 Windows 2000 以及更高版本。  
  
 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)有关可以在中设置的各种标志的说明`AceFlags`参数。  
  
##  <a name="a-namecsacla--csaclcsacl"></a><a name="csacl"></a>CSacl::CSacl  
 构造函数。  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 现有**ACL** （访问控制列表） 结构。  
  
### <a name="remarks"></a>备注  
 `CSacl`对象可以根据需要使用创建的现有**ACL**结构。 确保此参数是系统访问控制列表 (SACL) 并不是自由访问控制列表 (DACL)。 在调试版本，如果提供 DACL 中会出现一个断言。 在发布版本中将忽略 DACL 中的任何条目。  
  
##  <a name="a-namedtora--csaclcsacl"></a><a name="dtor"></a>CSacl:: ~ CSacl  
 析构函数。  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放任何资源获取的对象，其中包括所有访问控制项 (Ace)。  
  
##  <a name="a-namegetacecounta--csaclgetacecount"></a><a name="getacecount"></a>CSacl::GetAceCount  
 在返回的访问控制项 (Ace) 数`CSacl`对象。  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回包含在的 Ace 的数量`CSacl`对象。  
  
##  <a name="a-nameoperatoreqa--csacloperator-"></a><a name="operator_eq"></a>CSacl::operator =  
 赋值运算符。  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 **ACL** （访问控制列表），将分配给现有的对象。  
  
### <a name="return-value"></a>返回值  
 返回对已更新的引用`CSacl`对象。 确保**ACL**参数是实际系统访问控制列表 (SACL) 和不是自由访问控制列表 (DACL)。 在调试版本中将出现一个断言，并在发布生成**ACL**参数将被忽略。  
  
##  <a name="a-nameremoveacea--csaclremoveace"></a><a name="removeace"></a>CSacl::RemoveAce  
 从中删除特定的 ACE （访问控制项） **CSacl**对象。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要移除的 ACE 项的索引。  
  
### <a name="remarks"></a>备注  
 此方法从派生[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="a-nameremoveallacesa--csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::RemoveAllAces  
 删除访问控制项 (Ace) 中包含的所有`CSacl`对象。  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>备注  
 移除每个**ACE**结构 （如果有） 中`CSacl`对象。  
  
## <a name="see-also"></a>另请参阅  
 [CAcl 类](../../atl/reference/cacl-class.md)   
 [Acl](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)

