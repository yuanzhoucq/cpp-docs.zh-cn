---
title: "CDacl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
caps.latest.revision: 23
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
ms.openlocfilehash: 18da3b079cba8bbccba1a5d9655107620fc41eb8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="cdacl-class"></a>CDacl 类
此类是 DACL （自由访问控制列表） 结构的包装器。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|构造函数。|  
|[CDacl:: ~ CDacl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|将允许的 ACE （访问控制项） 添加到`CDacl`对象。|  
|[CDacl::AddDeniedAce](#adddeniedace)|将添加到被拒绝的 ACE`CDacl`对象。|  
|[CDacl::GetAceCount](#getacecount)|返回中的 Ace （访问控制项） 的数量`CDacl`对象。|  
|[CDacl::RemoveAce](#removeace)|从中移除特定 ACE （访问控制项）`CDacl`对象。|  
|[CDacl::RemoveAllAces](#removeallaces)|中删除所有中包含的 Ace`CDacl`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 对象的安全描述符可以包含 DACL。 DACL 包含标识的用户和组可以访问该对象零个或多个 Ace （访问控制项）。 如果 DACL 为空 （即，它包含零个 Ace），显式授予没有访问权限，所以隐式拒绝访问。 但是，如果对象的安全描述符没有 DACL，该对象是未受保护，且每个人拥有完全访问权限。  
  
 若要检索对象的 DACL，你必须是对象的所有者或具有 READ_CONTROL 访问对象。 若要更改对象的 DACL，必须具有对对象的 WRITE_DAC 访问。  
  
 使用类方法用于创建、 添加、 删除和删除从 Ace`CDacl`对象。 另请参阅[AtlGetDacl](security-global-functions.md#atlgetdacl)和[AtlSetDacl](security-global-functions.md#atlsetdacl)。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="addallowedace"></a>CDacl::AddAllowedAce  
 将允许的 ACE （访问控制项） 添加到`CDacl`对象。  
  
```
bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md)对象。  
  
 `AccessMask`  
 指定允许的访问权限的掩码指定`CSid`对象。  
  
 `AceFlags`  
 一组控制 ACE 继承的位标志。  
  
 `pObjectType`  
 对象类型。  
  
 `pInheritedObjectType`  
 继承的对象类型。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果 ACE 添加到`CDacl`对象， **false**失败。  
  
### <a name="remarks"></a>备注  
 A`CDacl`对象包含标识的用户和组可以访问该对象零个或多个 Ace （访问控制项）。 此方法将添加允许访问的 ACE`CDacl`对象。  
  
> [!NOTE]
>  第二种形式的`AddAllowedAce`才可在 Windows 2000 上及更高版本。  
  
 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)有关可以在中设置的各种标志的说明`AceFlags`参数。  
  
##  <a name="adddeniedace"></a>CDacl::AddDeniedAce  
 将被拒绝的 ACE （访问控制项） 添加到`CDacl`对象。  
  
```
bool AddDeniedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 一个 `CSid` 对象。  
  
 `AccessMask`  
 指定被拒绝的访问权限的掩码指定`CSid`对象。  
  
 `AceFlags`  
 一组控制 ACE 继承的位标志。 默认值为 0，在第一种形式的方法。  
  
 `pObjectType`  
 对象类型。  
  
 `pInheritedObjectType`  
 继承的对象类型。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果 ACE 添加到`CDacl`对象， **false**失败。  
  
### <a name="remarks"></a>备注  
 A`CDacl`对象包含标识的用户和组可以访问该对象零个或多个 Ace （访问控制项）。 此方法将添加拒绝访问的 ACE`CDacl`对象。  
  
> [!NOTE]
>  第二种形式的`AddDeniedAce`才可在 Windows 2000 上及更高版本。  
  
 请参阅[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)有关可以在中设置的各种标志的说明`AceFlags`参数。  
  
##  <a name="cdacl"></a>CDacl::CDacl  
 构造函数。  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 现有**ACL** （访问控制列表） 结构。  
  
### <a name="remarks"></a>备注  
 `CDacl`对象可以根据需要使用创建的现有**ACL**结构。 务必要注意，只有的 DACL （自由访问控制列表），并不 SACL （系统访问控制列表），应作为此参数进行传递。 在调试版本中，将传递 SACL 将导致断言。 在发布版本中传递 SACL 将会导致 Ace （访问控制项） 中的 ACL 以被忽略，并不会发生错误。  
  
##  <a name="dtor"></a>CDacl:: ~ CDacl  
 析构函数。  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放使用的对象，包括所有 Ace （访问控制项） 获取任何资源[CDacl::RemoveAllAces](#removeallaces)。  
  
##  <a name="getacecount"></a>CDacl::GetAceCount  
 返回中的 Ace （访问控制项） 的数量`CDacl`对象。  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回包含中的 Ace 的数量`CDacl`对象。  
  
##  <a name="operator_eq"></a>CDacl::operator =  
 赋值运算符。  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 ACL （访问控制列表） 要分配给现有对象。  
  
### <a name="return-value"></a>返回值  
 返回对已更新的引用`CDacl`对象。  
  
### <a name="remarks"></a>备注  
 你应确保你仅向此函数传递的 DACL （自由访问控制列表）。 传递 SACL （系统访问控制列表） 对此函数将导致在调试版本中的断言，但将导致在发布版本中的任何错误。  
  
##  <a name="removeace"></a>CDacl::RemoveAce  
 从中移除特定 ACE （访问控制项）`CDacl`对象。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要移除的 ACE 项的索引。  
  
### <a name="remarks"></a>备注  
 此方法派生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="removeallaces"></a>CDacl::RemoveAllAces  
 中移除的 Ace （访问控制项） 中包含所有`CDacl`对象。  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>备注  
 删除每个**ACE** （访问控制项） 结构 （如果有） 中的`CDacl`对象。  
  
## <a name="see-also"></a>另请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [CAcl 类](../../atl/reference/cacl-class.md)   
 [Acl](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)

