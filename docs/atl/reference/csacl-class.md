---
title: "CSacl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: bd9ef9932938cfe5ec65965b3a40116da7f43b90
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="csacl-class"></a>CSacl 类
此类是 SACL （系统访问控制列表） 结构的包装器。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
|[CSacl::GetAceCount](#getacecount)|返回中访问控制项 (Ace) 数目`CSacl`对象。|  
|[CSacl::RemoveAce](#removeace)|从中移除特定 ACE （访问控制项） **CSacl**对象。|  
|[CSacl::RemoveAllAces](#removeallaces)|中删除所有中包含的 Ace`CSacl`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 SACL 包含指定类型的域控制器的安全事件日志中生成审核记录的访问尝试次数的访问控制项 (Ace)。 请注意 SACL 生成日志项仅在访问尝试发生的域控制器上，而非包含对象的副本的每个域控制器。  
  
 若要设置或检索对象的安全描述符中的 SACL，必须在请求的线程的访问令牌中启用 SE_SECURITY_NAME 特权。 管理员组默认情况下，授予此特权，它可授予其他用户或组。 具有此权限授予不是，只需︰ 可以执行特权所定义的操作之前，特权必须在安全访问令牌中启用才能生效。 此模型，仅为特定系统操作，启用，然后禁用在不再需要时特权。 请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)有关的启用 SE_SECURITY_NAME 示例。  
  
 使用提供要添加、 删除、 创建和删除从 Ace 的类方法**SACL**对象。 另请参阅[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="addauditace"></a>CSacl::AddAuditAce  
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
 指定是否允许的访问尝试将被审核。 设置此标志设为 true 以启用审核;否则，将其设置为 false。  
  
 *bFailure*  
 指定是否需要审核的被拒绝的访问尝试次数。 设置此标志设为 true 以启用审核;否则，将其设置为 false。  
  
 `AceFlags`  
 一组控制 ACE 继承的位标志。  
  
 `pObjectType`  
 对象类型。  
  
 `pInheritedObjectType`  
 继承的对象类型。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果 ACE 添加到`CSacl`对象， **false**失败。  
  
### <a name="remarks"></a>备注  
 A`CSacl`对象包含指定类型的安全事件日志中生成审核记录的访问尝试次数的访问控制项 (Ace)。 此方法将添加到此类的 ACE`CSacl`对象。 第二种形式的`AddAuditAce`才可在 Windows 2000 上及更高版本。  
  
 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)有关可以在中设置的各种标志的说明`AceFlags`参数。  
  
##  <a name="csacl"></a>CSacl::CSacl  
 构造函数。  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 现有**ACL** （访问控制列表） 结构。  
  
### <a name="remarks"></a>备注  
 `CSacl`对象可以根据需要使用创建的现有**ACL**结构。 请确保此参数是一个系统访问控制列表 (SACL) 和不是自由访问控制列表 (DACL)。 在调试版本中，如果提供 DACL，则断言会发生。 在发布版本中 DACL 的任何条目将被忽略。  
  
##  <a name="dtor"></a>CSacl:: ~ CSacl  
 析构函数。  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放由对象，包括所有访问控制项 (Ace) 获取任何资源。  
  
##  <a name="getacecount"></a>CSacl::GetAceCount  
 返回中访问控制项 (Ace) 数目`CSacl`对象。  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回包含中的 Ace 的数量`CSacl`对象。  
  
##  <a name="operator_eq"></a>CSacl::operator =  
 赋值运算符。  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 **ACL** （访问控制列表），要分配给现有对象。  
  
### <a name="return-value"></a>返回值  
 返回对已更新的引用`CSacl`对象。 确保**ACL**参数是实际系统访问控制列表 (SACL) 和不是自由访问控制列表 (DACL)。 在调试版本中将出现一个断言，并在发布版本中**ACL**参数将被忽略。  
  
##  <a name="removeace"></a>CSacl::RemoveAce  
 从中移除特定 ACE （访问控制项） **CSacl**对象。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要移除的 ACE 项的索引。  
  
### <a name="remarks"></a>备注  
 此方法派生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="removeallaces"></a>CSacl::RemoveAllAces  
 删除访问控制项 (Ace) 中包含的所有`CSacl`对象。  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>备注  
 删除每个**ACE**结构 （如果有）`CSacl`对象。  
  
## <a name="see-also"></a>另请参阅  
 [CAcl 类](../../atl/reference/cacl-class.md)   
 [Acl](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)

