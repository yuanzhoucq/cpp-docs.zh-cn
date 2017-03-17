---
title: "CSecurityDesc 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
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
ms.openlocfilehash: 6dbd586ee3ee07d3c567fa0aae46446397dfb62b
ms.lasthandoff: 02/24/2017

---
# <a name="csecuritydesc-class"></a>CSecurityDesc 类
此类是包装器**SECURITY_DESCRIPTOR**结构。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CSecurityDesc
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|构造函数。|  
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSecurityDesc::FromString](#fromstring)|将一个有效的、 功能安全描述符转换为字符串格式的安全描述符。|  
|[CSecurityDesc::GetControl](#getcontrol)|检索控件中的安全描述符的信息。|  
|[CSecurityDesc::GetDacl](#getdacl)|从安全描述符检索自由访问控制列表 (DACL) 信息。|  
|[CSecurityDesc::GetGroup](#getgroup)|从安全描述符中检索的主要组信息。|  
|[CSecurityDesc::GetOwner](#getowner)|从安全描述符中检索所有者信息时。|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|返回一个指向**SECURITY_DESCRIPTOR**结构。|  
|[CSecurityDesc::GetSacl](#getsacl)|从安全描述符中检索系统访问控制列表 (SACL) 信息。|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|确定是否 DACL 配置为支持自动传播。|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|确定是否使用默认的 DACL 配置的安全描述符。|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|确定的安全描述符是否包含 DACL。|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|确定是否 DACL 配置为防止进行修改。|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|确定是否安全描述符的组安全标识符 (SID) 默认设置。|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|确定是否默认情况下设置安全描述符的所有者的 SID。|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|确定是否 SACL 配置为支持自动传播。|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|确定是否使用默认的 SACL 配置的安全描述符。|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|确定的安全描述符是否包含 SACL。|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|确定是否 SACL 配置为防止进行修改。|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|确定的安全描述符是否采用自相关格式。|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|调用此方法将安全描述符转换为绝对格式。|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|调用此方法将安全描述符转换为自相关格式。|  
|[CSecurityDesc::SetControl](#setcontrol)|设置安全说明符的控制位。|  
|[CSecurityDesc::SetDacl](#setdacl)|设置 DACL 中的信息。 如果 DACL 中已存在的安全描述符，则替换它。|  
|[CSecurityDesc::SetGroup](#setgroup)|设置绝对格式的安全描述符，并替换已存在的任何主要组信息的主要组信息。|  
|[CSecurityDesc::SetOwner](#setowner)|设置绝对格式的安全描述符，并替换已存在任何所有者信息的所有者信息。|  
|[CSecurityDesc::SetSacl](#setsacl)|SACL 中设置的信息。 如果 SACL 中已存在的安全描述符，则替换它。|  
|[CSecurityDesc::ToString](#tostring)|将安全描述符转换为字符串格式。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|返回一个指向**SECURITY_DESCRIPTOR**结构。|  
|[CSecurityDesc::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 **SECURITY_DESCRIPTOR**结构包含与对象关联的安全信息。 应用程序使用此结构来设置和查询对象的安全状态。 另请参阅[AtlGetSecurityDescriptor](http://msdn.microsoft.com/library/233578b8-dcc5-4f51-8e62-7cdcc2ff6b11)。  
  
 应用程序不应修改**SECURITY_DESCRIPTOR**结构直接，而不是应该会使用提供的类方法。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc  
 构造函数。  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CSecurityDesc`对象或**SECURITY_DESCRIPTOR**结构以分配给新`CSecurityDesc`对象。  
  
### <a name="remarks"></a>备注  
 `CSecurityDesc` （可选） 可以使用创建对象**SECURITY_DESCRIPTOR**结构或以前定义`CSecurityDesc`对象。  
  
##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc  
 析构函数。  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源。  
  
##  <a name="fromstring"></a>CSecurityDesc::FromString  
 将一个有效的、 功能安全描述符转换为字符串格式的安全描述符。  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pstr`  
 指向以 null 结尾的字符串，其中包含[字符串格式的安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379570)会在待转换。  
  
### <a name="return-value"></a>返回值  
 如果成功则返回 true。 失败时引发异常。  
  
### <a name="remarks"></a>备注  
 可以通过使用创建的字符串[CSecurityDesc::ToString](#tostring)。 将转换为字符串的安全描述符，使得更轻松地存储和传输。  
  
 此方法仅可与 Windows 2000 和更高版本因为它调用[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
##  <a name="getcontrol"></a>CSecurityDesc::GetControl  
 检索控件中的安全描述符的信息。  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>参数  
 *psdc*  
 指向**SECURITY_DESCRIPTOR_CONTROL**结构，它接收的安全描述符控制信息。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
### <a name="remarks"></a>备注  
 此方法才有意义时使用的 Windows 2000 或更高版本，因为它调用[GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647)。  
  
##  <a name="getdacl"></a>CSecurityDesc::GetDacl  
 从安全描述符检索自由访问控制列表 (DACL) 信息。  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pDacl`  
 指向`CDacl`要在其中存储一份安全描述符的 DACL 的结构。 如果任意**ACL**存在方法设置`pDacl`为地址的安全描述符的自由**ACL**。 如果任意**ACL**不存在，未存储任何值。  
  
 `pbPresent`  
 指向的值，该值指示是否存在任意**ACL**中指定的安全描述符。 如果安全描述符包含任意**ACL**，此参数设置为 true。 如果安全描述符不包含任意**ACL**，此参数设置为 false。  
  
 `pbDefaulted`  
 为标志的指针设置为 SE_DACL_DEFAULTED 中的标志值**SECURITY_DESCRIPTOR_CONTROL**结构，如果任意**ACL**存在的安全描述符。 如果此标志为 true，自由**ACL**检索到默认的机制; 如果为 false，自由**ACL**由用户显式指定。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getgroup"></a>CSecurityDesc::GetGroup  
 从安全描述符中检索的主要组信息。  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid](../../atl/reference/csid-class.md) （安全标识符），它接收 CDacl 中存储的组的副本。  
  
 `pbDefaulted`  
 为标志的指针设置为 SE_GROUP_DEFAULTED 中的标志值**SECURITY_DESCRIPTOR_CONTROL**结构，该方法返回时。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getowner"></a>CSecurityDesc::GetOwner  
 从安全描述符中检索所有者信息时。  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid](../../atl/reference/csid-class.md) （安全标识符），它接收 CDacl 中存储的组的副本。  
  
 `pbDefaulted`  
 为标志的指针设置为 SE_OWNER_DEFAULTED 中的标志值**SECURITY_DESCRIPTOR_CONTROL**结构，该方法返回时。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 返回一个指向**SECURITY_DESCRIPTOR**结构。  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)结构。  
  
##  <a name="getsacl"></a>CSecurityDesc::GetSacl  
 从安全描述符中检索系统访问控制列表 (SACL) 信息。  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSacl`  
 指向`CSacl`要在其中存储一份安全描述符 SACL 的结构。 如果系统**ACL**存在方法设置`pSacl`安全描述符的系统地址为**ACL**。 如果系统**ACL**不存在，未存储任何值。  
  
 `pbPresent`  
 为该方法将设置为指示系统的状态标志的指针**ACL**中指定的安全描述符。 如果安全描述符包含系统**ACL**，此参数设置为 true。 如果安全描述符不包含系统**ACL**，此参数设置为 false。  
  
 `pbDefaulted`  
 为标志的指针设置为 SE_SACL_DEFAULTED 中的标志值**SECURITY_DESCRIPTOR_CONTROL**结构，如果一个系统**ACL**存在的安全描述符。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited  
 确定是否自由访问控制列表 (DACL) 配置为支持自动传播。  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符将包含 DACL 的设置以支持自动传播到现有的子对象的可继承的访问控制项 (Ace)，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 系统将为该对象及其现有的子对象执行自动继承算法时设置此位。  
  
##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted  
 确定是否使用默认自由访问控制列表 (DACL) 配置的安全描述符。  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含默认的 DACL，则返回 false 否则，返回 true。  
  
### <a name="remarks"></a>备注  
 此标志可能会影响系统如何处理与访问控制项 (ACE) 继承的 DACL。 例如，如果对象的创建者未指定 DACL，该对象接收默认的 DACL 来自创建者的访问令牌。 如果未设置 SE_DACL_PRESENT 标志，系统将忽略此标志。  
  
 此标志用来确定如何在对象上的最终 DACL 是要计算，并且不在可保护对象的安全描述符控制以物理方式存储。  
  
 若要设置此标志，请使用[CSecurityDesc::SetDacl](#setdacl)方法。  
  
##  <a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent  
 确定的安全描述符是否包含自由访问控制列表 (DACL)。  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 DACL，则返回 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 如果未设置此标志，或者如果设置此标志而 DACL 为 NULL，安全描述符将允许对每个人都完全访问权限。  
  
 此标志用于保存指定由调用方，直到的安全描述符与某个安全对象相关联的安全信息。 一旦与某个安全对象关联的安全描述符，则 SE_DACL_PRESENT 标志始终设置中的安全描述符控制。  
  
 若要设置此标志，请使用[CSecurityDesc::SetDacl](#setdacl)方法。  
  
##  <a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected  
 确定是否自由访问控制列表 (DACL) 配置为防止进行修改。  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果将 DACL 配置为防止安全描述符被修改的可继承的访问控制项 (Ace)，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[CSecurityDesc::SetDacl](#setdacl)方法。  
  
 此方法才有意义的 Windows 2000 或更高版本，因为只有 Windows 2000 支持的可继承 Ace 自动传播。  
  
##  <a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted  
 确定是否安全描述符的组安全标识符 (SID) 默认设置。  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 则返回 true; 如果默认的机制，而不是安全描述符中，原始提供程序提供的安全描述符组 SID。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[CSecurityDesc::SetGroup](#setgroup)方法。  
  
##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted  
 确定是否安全描述符的所有者安全标识符 (SID) 默认设置。  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果默认的机制，而不是安全描述符中，原始提供程序提供的安全描述符的所有者的 SID，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[CSecurityDesc::SetOwner](#setowner)方法。  
  
##  <a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited  
 确定是否系统访问控制列表 (SACL) 配置为支持自动传播。  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 SACL 设置以支持自动传播到现有的子对象的可继承的访问控制项 (Ace)，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 系统将为该对象及其现有的子对象执行自动继承算法时设置此位。  
  
##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted  
 确定是否使用默认系统访问控制列表 (SACL) 配置的安全描述符。  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含默认 SACL，则返回 false 否则，返回 true。  
  
### <a name="remarks"></a>备注  
 此标志可能会影响系统如何处理与访问控制项 (ACE) 继承的 SACL。 如果未设置 SE_SACL_PRESENT 标志，系统将忽略此标志。  
  
 若要设置此标志，请使用[CSecurityDesc::SetSacl](#setsacl)方法。  
  
##  <a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent  
 确定的安全描述符是否包含系统访问控制列表 (SACL)。  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 SACL，则返回 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[CSecurityDesc::SetSacl](#setsacl)方法。  
  
##  <a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected  
 确定系统访问控制列表 (SACL) 是否被配置为防止进行修改。  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果 SACL 配置为防止安全描述符被修改的可继承的访问控制项 (Ace)，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[CSecurityDesc::SetSacl](#setsacl)方法。  
  
 此方法才有意义的 Windows 2000 或更高版本，因为只有 Windows 2000 支持的可继承 Ace 自动传播。  
  
##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative  
 确定的安全描述符是否采用自相关格式。  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符采用自相关格式与在连续内存块中的所有安全信息，则返回 true。 如果安全描述符采用绝对格式，则返回 false。 有关详细信息，请参阅[绝对超链接和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute  
 调用此方法将安全描述符转换为绝对格式。  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 绝对格式的安全描述符包含指向包含，而不是信息本身的信息。 自相关格式的安全描述符包含连续内存块中的信息。 在一个自相关的安全描述符， **SECURITY_DESCRIPTOR**结构始终启动信息，但安全描述符的其他组件可以按照任意顺序中的结构。 而不是使用的内存地址，通过从安全描述符的开头的偏移量进行标识自相关的安全描述符中的组件。 必须存储在磁盘上或通过一种通信协议传输的安全描述符时，此格式非常有用。 有关详细信息，请参阅[绝对超链接和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative  
 调用此方法将安全描述符转换为自相关格式。  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 绝对格式的安全描述符包含它所包含的信息，而不是包含信息本身的指针。 自相关格式的安全描述符包含连续内存块中的信息。 在一个自相关的安全描述符， **SECURITY_DESCRIPTOR**结构始终启动信息，但安全描述符的其他组件可以按照任意顺序中的结构。 而不是使用的内存地址，通过从安全描述符的开头的偏移量进行标识的安全描述符的组件。 必须存储在磁盘上或通过一种通信协议传输的安全描述符时，此格式非常有用。 有关详细信息，请参阅[绝对超链接和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="operator_eq"></a>CSecurityDesc::operator =  
 赋值运算符。  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 **SECURITY_DESCRIPTOR**结构或`CSecurityDesc`要分配给`CSecurityDesc`对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CSecurityDesc`对象。  
  
##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 将为指针值强制转换**SECURITY_DESCRIPTOR**结构。  
  
```  
operator const SECURITY_DESCRIPTOR *() const throw();
```  
  
##  <a name="setcontrol"></a>CSecurityDesc::SetControl  
 设置安全说明符的控制位。  
  
```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```  
  
### <a name="parameters"></a>参数  
 `ControlBitsOfInterest`  
 一个**SECURITY_DESCRIPTOR_CONTROL**掩码，指示要设置的控制位。 可以设置此标志的列表，请参阅[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
 `ControlBitsToSe`t  
 一个 `SECURITY_DESCRIPTOR_CONTROL` 掩码，指示由 `ControlBitsOfInterest` 掩码指定的控制位的新值。 此参数可以为 `ControlBitsOfInterest` 参数列出的标志的组合。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 此方法不可用仅在 Windows 2000 和更高版本，因为它调用[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
##  <a name="setdacl"></a>CSecurityDesc::SetDacl  
 自由访问控制列表 (DACL) 中设置信息。 如果 DACL 中已存在的安全描述符，则替换它。  
  
```
inline void SetDacl(  
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(  
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *Dacl*  
 引用`CDacl`对象，它指定安全描述符的 DACL。 此参数不能为 NULL。 若要设置安全描述符中的 NULL DACL，该方法的第一种形式应使用与`bPresent`设置为 false。  
  
 `bPresent`  
 指定一个标志，指示存在 DACL 的安全描述符中。 如果此参数为 true，该方法中设置 SE_DACL_PRESENT 标志**SECURITY_DESCRIPTOR_CONTROL**结构，并使用中的值*Dacl*和`bDefaulted`参数。 如果为 false，此方法清除 SE_DACL_PRESENT 标志和`bDefaulted`将被忽略。  
  
 `bDefaulted`  
 指定一个标志，指示 DACL 的源。 如果此标志为 true，DACL 已检索的一些默认的机制。 如果为 false，DACL 显式指定的用户。 该方法将此值存储在的 SE_DACL_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果未指定此参数，则清除 SE_DACL_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 没有一个空之间不存在 DACL 一项重大差异。 如果 DACL 为空，它不包含任何访问控制条目，并没有访问权限已被显式授予。 因此，隐式拒绝对对象的访问。 当一个对象不具有任何 DACL 时，另一方面，无保护分配给该对象，并授予的任何访问请求。  
  
##  <a name="setgroup"></a>CSecurityDesc::SetGroup  
 设置绝对格式的安全描述符，并替换已存在的任何主要组信息的主要组信息。  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `Sid`  
 引用[CSid](../../atl/reference/csid-class.md)安全描述符的新主要组的对象。 此参数不能为 NULL。 安全描述符可以标记为不具有 DACL 或 SACL，但是它必须具有一个组和一个所有者，即使这些是 NULL SID （这是一个具有特殊意义的内置 SID）。  
  
 `bDefaulted`  
 指示是否已从默认机制派生的主要组信息。 如果此值为 true，它是默认信息，并且该方法将此值存储为中的 SE_GROUP_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果此参数为零，则清除 SE_GROUP_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="setowner"></a>CSecurityDesc::SetOwner  
 设置绝对格式的安全描述符的所有者信息。 它将替换已存在的任何所有者信息。  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `Sid`  
 [CSid](../../atl/reference/csid-class.md)安全描述符的新主要所有者的对象。 此参数不能为 NULL。  
  
 `bDefaulted`  
 该值指示是否从默认机制派生的所有者信息。 如果此值为 true，则默认的信息。 该方法将此值存储为中的 SE_OWNER_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果此参数为零，则清除 SE_OWNER_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="setsacl"></a>CSecurityDesc::SetSacl  
 设置系统访问控制列表 (SACL) 中的信息。 如果 SACL 中已存在的安全描述符，则替换它。  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *Sacl*  
 指向`CSacl`对象，它指定安全描述符的 SACL。 此参数必须不能为 NULL，并且必须为 CSacl 对象。 与不同的是 Dacl，NULL 和空的 SACL 之间没有区别因为 SACL 对象未指定仅审核信息的访问权限。  
  
 `bDefaulted`  
 指定一个标志，指示 SACL 的源。 如果此标志为 true，SACL 已检索的一些默认的机制。 如果为 false，SACL 明确指定的用户。 该方法将此值存储在的 SE_SACL_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果未指定此参数，则清除 SE_SACL_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="tostring"></a>CSecurityDesc::ToString  
 将安全描述符转换为字符串格式。  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pstr`  
 指向以 null 结尾的字符串，将接收[字符串格式的安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379570)。  
  
 `si`  
 指定 SECURITY_INFORMATION 位标志，用于指示要包括在输出字符串中的安全描述符的组件的组合。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 字符串格式的安全描述符后，它可以更轻松地存储或传输。 使用`CSecurityDesc::FromString`方法将字符串转换回的安全描述符。  
  
 `si`参数可以包含以下 SECURITY_INFORMATION 标志︰  
  
|值|含义|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|包括所有者。|  
|GROUP_SECURITY_INFORMATION|包括主要组。|  
|DACL_SECURITY_INFORMATION|包括 DACL。|  
|SACL_SECURITY_INFORMATION|包括 SACL。|  
  
 如果在输入的安全描述符中设置了 SE_DACL_PRESENT 控制位 DACL 为 NULL，则该方法失败。  
  
 如果 DACL 为 NULL 且 SE_DACL_PRESENT 控件位未设置输入的安全描述符中，生成的安全描述符字符串未安装 d︰ 组件。 请参阅[安全描述符字符串格式](http://msdn.microsoft.com/library/windows/desktop/aa379570)的更多详细信息。  
  
 此方法仅可与 Windows 2000 和更高版本，因为它调用[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
## <a name="see-also"></a>另请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)

