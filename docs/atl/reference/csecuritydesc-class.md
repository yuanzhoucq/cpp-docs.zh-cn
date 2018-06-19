---
title: CSecurityDesc 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6963c04e3bd0ba06f8cc2beb9cb77447e2acd81
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366164"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 类
此类是包装器**SECURITY_DESCRIPTOR**结构。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CSecurityDesc
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|构造函数。|  
|[CSecurityDesc::~CSecurityDesc](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSecurityDesc::FromString](#fromstring)|将有效、 功能安全描述符转换为字符串格式的安全描述符。|  
|[CSecurityDesc::GetControl](#getcontrol)|检索控制的安全描述符中的信息。|  
|[CSecurityDesc::GetDacl](#getdacl)|从安全描述符检索自由访问控制列表 (DACL) 信息。|  
|[CSecurityDesc::GetGroup](#getgroup)|从安全描述符中检索的主要组信息。|  
|[CSecurityDesc::GetOwner](#getowner)|从安全描述符中检索所有者信息。|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|返回一个指向**SECURITY_DESCRIPTOR**结构。|  
|[CSecurityDesc::GetSacl](#getsacl)|从安全描述符中检索系统访问控制列表 (SACL) 信息。|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|确定是否 DACL 配置为支持自动传播。|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|确定是否默认的 DACL 进行配置的安全描述符。|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|确定的安全描述符是否包含 DACL。|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|确定是否 DACL 被配置为阻止修改。|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|确定默认已设置的安全描述符的组安全标识符 (SID)。|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|确定默认已设置的安全描述符的所有者 SID。|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|确定是否 SACL 配置为支持自动传播。|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|确定是否默认 SACL 进行配置的安全描述符。|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|确定的安全描述符是否包含 SACL。|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|确定是否 SACL 被配置为阻止修改。|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|确定的安全描述符是否是自相关格式。|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|调用此方法以将安全描述符转换为绝对格式。|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|调用此方法以将安全描述符转换为自相关格式。|  
|[CSecurityDesc::SetControl](#setcontrol)|设置安全说明符的控制位。|  
|[CSecurityDesc::SetDacl](#setdacl)|DACL 中设置的信息。 如果 DACL 中已存在的安全描述符，则替换它。|  
|[CSecurityDesc::SetGroup](#setgroup)|设置并替换任何已存在的主要组信息的绝对格式安全描述符的主要组信息。|  
|[CSecurityDesc::SetOwner](#setowner)|设置并替换已存在任何所有者信息的绝对格式安全描述符的所有者信息。|  
|[CSecurityDesc::SetSacl](#setsacl)|SACL 中设置的信息。 如果 SACL 中已存在的安全描述符，则替换它。|  
|[CSecurityDesc::ToString](#tostring)|将安全描述符转换为字符串格式。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|返回一个指向**SECURITY_DESCRIPTOR**结构。|  
|[CSecurityDesc::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 **SECURITY_DESCRIPTOR**结构包含与对象关联的安全信息。 应用程序使用此结构来设置和查询对象的安全状态。 另请参阅[AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)。  
  
 应用程序不应修改**SECURITY_DESCRIPTOR**结构直接，，而不是应会使用提供的类方法。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="requirements"></a>要求  
 **标头：** atlsecurity.h  
  
##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc  
 构造函数。  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CSecurityDesc`对象或**SECURITY_DESCRIPTOR**结构以将分配到新`CSecurityDesc`对象。  
  
### <a name="remarks"></a>备注  
 `CSecurityDesc` （可选） 可以使用创建对象**SECURITY_DESCRIPTOR**结构或以前定义`CSecurityDesc`对象。  
  
##  <a name="dtor"></a>  CSecurityDesc::~CSecurityDesc  
 析构函数。  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源。  
  
##  <a name="fromstring"></a>  CSecurityDesc::FromString  
 将有效、 功能安全描述符转换为字符串格式的安全描述符。  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pstr`  
 指向以 null 结尾的字符串，包含[字符串格式安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379570)要转换。  
  
### <a name="return-value"></a>返回值  
 如果成功则返回 true。 失败时引发异常。  
  
### <a name="remarks"></a>备注  
 可以通过使用创建字符串[CSecurityDesc::ToString](#tostring)。 将转换为字符串的安全描述符便于存储和传输。  
  
 此方法调用[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
##  <a name="getcontrol"></a>  CSecurityDesc::GetControl  
 检索控制的安全描述符中的信息。  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>参数  
 *psdc*  
 指向**SECURITY_DESCRIPTOR_CONTROL**接收的安全描述符控制信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
### <a name="remarks"></a>备注  
 此方法调用[GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647)。  
  
##  <a name="getdacl"></a>  CSecurityDesc::GetDacl  
 从安全描述符检索自由访问控制列表 (DACL) 信息。  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pDacl`  
 指向`CDacl`要在其中存储一份安全描述符的 DACL 的结构。 如果任意**ACL**存在方法设置`pDacl`到的地址的安全描述符的任意**ACL**。 如果任意**ACL**不存在，不存储任何值。  
  
 `pbPresent`  
 指向一个值，该值指示是否存在任意**ACL**中指定的安全描述符。 如果安全描述符包含任意**ACL**，此参数设置为 true。 如果安全描述符不包含任意**ACL**，此参数设置为 false。  
  
 `pbDefaulted`  
 指向一个标志设置为中的 SE_DACL_DEFAULTED 标志的值**SECURITY_DESCRIPTOR_CONTROL**结构如果自由**ACL**存在的安全描述符。 如果此标志为 true，任意**ACL**检索由默认的机制; 如果为 false，任意**ACL**由用户显式指定。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getgroup"></a>  CSecurityDesc::GetGroup  
 从安全描述符中检索的主要组信息。  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid](../../atl/reference/csid-class.md) （安全标识符） 接收存储在 CDacl 组的副本。  
  
 `pbDefaulted`  
 指向一个标志设置为中的 SE_GROUP_DEFAULTED 标志的值**SECURITY_DESCRIPTOR_CONTROL**结构，该方法返回时。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getowner"></a>  CSecurityDesc::GetOwner  
 从安全描述符中检索所有者信息。  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid](../../atl/reference/csid-class.md) （安全标识符） 接收存储在 CDacl 组的副本。  
  
 `pbDefaulted`  
 指向一个标志设置为中的 SE_OWNER_DEFAULTED 标志的值**SECURITY_DESCRIPTOR_CONTROL**结构，该方法返回时。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 返回一个指向**SECURITY_DESCRIPTOR**结构。  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)结构。  
  
##  <a name="getsacl"></a>  CSecurityDesc::GetSacl  
 从安全描述符中检索系统访问控制列表 (SACL) 信息。  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSacl`  
 指向`CSacl`要在其中存储一份的安全描述符 SACL 的结构。 如果系统**ACL**存在方法设置`pSacl`到的安全描述符的系统地址**ACL**。 如果系统**ACL**不存在，不存储任何值。  
  
 `pbPresent`  
 指向该方法将设置为指示系统的状态的标志**ACL**中指定的安全描述符。 如果安全描述符包含的系统**ACL**，此参数设置为 true。 如果安全描述符不包含系统**ACL**，此参数设置为 false。  
  
 `pbDefaulted`  
 指向一个标志设置为中的 SE_SACL_DEFAULTED 标志的值**SECURITY_DESCRIPTOR_CONTROL**结构如果系统**ACL**存在的安全描述符。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited  
 确定是否自由访问控制列表 (DACL) 是否配置为支持自动传播。  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含该设置以支持对现有的子对象的可继承的访问控制项 (Ace) 的自动传播的 DACL，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 对象和其现有的子对象执行自动继承算法时，系统将设置此位。  
  
##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted  
 确定是否默认自由访问控制列表 (DACL) 进行配置的安全描述符。  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含默认的 DACL，则返回 false 否则，返回 true。  
  
### <a name="remarks"></a>备注  
 此标志可能会影响系统如何处理 DACL，与访问控制项 (ACE) 继承。 例如，如果对象的创建者未指定的 DACL，则对象将从创建者的访问令牌接收默认 DACL。 如果未设置 SE_DACL_PRESENT 标志，系统将忽略此标志。  
  
 此标志用于确定如何在对象上的最终 DACL，则将计算，但不在的安全对象的安全描述符控制以物理方式存储。  
  
 若要设置此标志，使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent  
 确定的安全描述符是否包含的自由访问控制列表 (DACL)。  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 DACL，则返回 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 如果未设置此标志，或者如果设置此标志和 DACL，则为 NULL，安全描述符将允许对每个人都完全访问权限。  
  
 此标志用于保存与安全对象相关联的安全描述符之前由调用方指定的安全信息。 与安全对象相关联的安全描述符后，始终在安全描述符控制设置 SE_DACL_PRESENT 标志。  
  
 若要设置此标志，使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected  
 确定是否自由访问控制列表 (DACL) 是否配置为防止进行修改。  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果 DACL 被配置为阻止从正在修改可继承的访问控制项 (Ace) 的安全描述符，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
 此方法支持可继承的 Ace 的自动的传播。  
  
##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted  
 确定默认已设置的安全描述符的组安全标识符 (SID)。  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果默认的机制，而不是原始的提供程序的安全描述符，提供的安全描述符的，组 SID，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，使用[csecuritydesc:: Setgroup](#setgroup)方法。  
  
##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted  
 确定默认已设置的安全描述符的所有者安全标识符 (SID)。  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果默认的机制，而不是原始的提供程序的安全描述符，提供的安全描述符的所有者 SID，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，使用[csecuritydesc:: Setowner](#setowner)方法。  
  
##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited  
 确定系统访问控制列表 (SACL) 是否被配置为支持自动传播。  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含该设置以支持对现有的子对象的可继承的访问控制项 (Ace) 的自动传播 SACL，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 对象和其现有的子对象执行自动继承算法时，系统将设置此位。  
  
##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted  
 确定是否使用默认系统访问控制列表 (SACL) 配置的安全描述符。  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含默认 SACL，则返回 false 否则，返回 true。  
  
### <a name="remarks"></a>备注  
 此标志可能会影响系统如何处理 SACL，与访问控制项 (ACE) 继承。 如果未设置 SE_SACL_PRESENT 标志，系统将忽略此标志。  
  
 若要设置此标志，使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent  
 确定的安全描述符是否包含系统访问控制列表 (SACL)。  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 SACL，则返回 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected  
 确定系统访问控制列表 (SACL) 是否被配置为防止进行修改。  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果 SACL 被配置为阻止从正在修改可继承的访问控制项 (Ace) 的安全描述符，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
 此方法支持可继承的 Ace 的自动的传播。  
  
##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative  
 确定的安全描述符是否是自相关格式。  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符为自相关格式与连续的内存块中的所有安全信息，则返回 true。 如果安全描述符为绝对格式，则返回 false。 有关详细信息，请参阅[绝对和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute  
 调用此方法以将安全描述符转换为绝对格式。  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 绝对格式的安全描述符包含指向其所含的信息，而不是本身的信息。 采用自相关格式的安全描述符包含连续的内存块中的信息。 在自相关的安全描述符， **SECURITY_DESCRIPTOR**结构始终启动信息，但安全描述符的其他组件可以按照任何顺序中的结构。 而不是使用内存地址，通过从安全描述符的开头的偏移量进行标识的自相关的安全描述符的组件。 必须存储在磁盘上或通过一种通信协议传输的安全描述符时，此格式很有用。 有关详细信息，请参阅[绝对和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative  
 调用此方法以将安全描述符转换为自相关格式。  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 绝对格式的安全描述符包含指向它包含的信息，而不是包含本身的信息。 采用自相关格式的安全描述符包含连续的内存块中的信息。 在自相关的安全描述符， **SECURITY_DESCRIPTOR**结构始终启动信息，但安全描述符的其他组件可以按照任何顺序中的结构。 而不是使用内存地址，通过从安全描述符的开头的偏移量进行标识的安全描述符的组件。 必须存储在磁盘上或通过一种通信协议传输的安全描述符时，此格式很有用。 有关详细信息，请参阅[绝对和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="operator_eq"></a>  CSecurityDesc::operator =  
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
  
##  <a name="operator_const_security_descriptor__star"></a>  CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 将强制转换为指向的值**SECURITY_DESCRIPTOR**结构。  
  
```  
operator const SECURITY_DESCRIPTOR *() const throw();
```  
  
##  <a name="setcontrol"></a>  CSecurityDesc::SetControl  
 设置安全说明符的控制位。  
  
```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```  
  
### <a name="parameters"></a>参数  
 `ControlBitsOfInterest`  
 A **SECURITY_DESCRIPTOR_CONTROL**掩码，指示要设置的控制位。 可以将其设置的标志的列表，请参阅[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
 `ControlBitsToSet`  
 一个 `SECURITY_DESCRIPTOR_CONTROL` 掩码，指示由 `ControlBitsOfInterest` 掩码指定的控制位的新值。 此参数可以为 `ControlBitsOfInterest` 参数列出的标志的组合。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 此方法调用[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
##  <a name="setdacl"></a>  CSecurityDesc::SetDacl  
 设置中的自由访问控制列表 (DACL) 信息。 如果 DACL 中已存在的安全描述符，则替换它。  
  
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
 引用`CDacl`对象，它指定的安全描述符的 DACL。 此参数不能为 NULL。 若要设置安全描述符中的 NULL DACL，第一种形式的方法应使用与`bPresent`设置为 false。  
  
 `bPresent`  
 指定一个标志，指示存在的安全描述符中的 DACL。 如果此参数为 true，该方法中设置 SE_DACL_PRESENT 标志**SECURITY_DESCRIPTOR_CONTROL**结构和使用中的值*Dacl*和`bDefaulted`参数。 如果为 false，此方法清除 SE_DACL_PRESENT 标志和`bDefaulted`将被忽略。  
  
 `bDefaulted`  
 指定一个标志，指示 DACL 的源。 如果此标志为 true，已被 DACL 检索由某些默认机制。 如果为 false，DACL 显式指定了用户。 该方法将此值存储在的 SE_DACL_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果未指定此参数，将清除 SE_DACL_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 没有空之间不存在的 DACL 一项重大差异。 如果 DACL 为空，它不包含任何访问控制项，并没有访问权限已被显式授予。 因此，对对象的访问被隐式拒绝。 当一个对象不具有任何 DACL 时，另一方面，无保护分配给该对象，并且授予的任何访问请求。  
  
##  <a name="setgroup"></a>  CSecurityDesc::SetGroup  
 设置并替换任何已存在的主要组信息的绝对格式安全描述符的主要组信息。  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `Sid`  
 引用[CSid](../../atl/reference/csid-class.md)安全描述符的新主要组的对象。 此参数不能为 NULL。 安全描述符可以标记为不具有 DACL 或 SACL，但是它必须具有一组和一个所有者，即使这些是 NULL SID （这是具有特殊含义的内置 SID）。  
  
 `bDefaulted`  
 指示是否从默认的机制派生的主要组信息。 如果此值为 true，它是默认的信息，并且该方法将此值存储为中的 SE_GROUP_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果此参数为零，将清除 SE_GROUP_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="setowner"></a>  CSecurityDesc::SetOwner  
 设置绝对格式安全描述符的所有者信息。 它将替换已存在的任何所有者信息。  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `Sid`  
 [CSid](../../atl/reference/csid-class.md)安全描述符的新主要所有者的对象。 此参数不能为 NULL。  
  
 `bDefaulted`  
 指示是否从默认的机制派生的所有者信息。 如果此值为 true，则默认信息。 该方法将此值存储为中的 SE_OWNER_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果此参数为零，将清除 SE_OWNER_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="setsacl"></a>  CSecurityDesc::SetSacl  
 系统访问控制列表 (SACL) 中设置的信息。 如果 SACL 中已存在的安全描述符，则替换它。  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *Sacl*  
 指向`CSacl`对象，它指定的安全描述符 SACL。 此参数必须不为 NULL，并且必须 CSacl 对象。 与不同的 Dacl，NULL 和空的 SACL，之间没有差异因为 SACL 对象未指定仅审核信息的访问权限。  
  
 `bDefaulted`  
 指定一个标志，指示 SACL 的源。 如果此标志为 true，已被 SACL 检索由某些默认机制。 如果为 false，SACL 显式指定了用户。 该方法将此值存储在的 SE_SACL_DEFAULTED 标志**SECURITY_DESCRIPTOR_CONTROL**结构。 如果未指定此参数，将清除 SE_SACL_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="tostring"></a>  CSecurityDesc::ToString  
 将安全描述符转换为字符串格式。  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pstr`  
 指向以 null 结尾的字符串将接收[字符串格式安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379570)。  
  
 `si`  
 指定的 SECURITY_INFORMATION 位标志，以指示在输出字符串中包含的安全描述符的组件的组合。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 字符串格式的安全描述符后，它可以更轻松地存储或传输。 使用`CSecurityDesc::FromString`方法将字符串转换回安全描述符。  
  
 `si`参数可以包含以下 SECURITY_INFORMATION 标志：  
  
|值|含义|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|包括的所有者。|  
|GROUP_SECURITY_INFORMATION|包括的主要组。|  
|DACL_SECURITY_INFORMATION|包括 DACL。|  
|SACL_SECURITY_INFORMATION|包括 SACL。|  
  
 如果 DACL，则 NULL 和 SE_DACL_PRESENT 控件位设置输入的安全描述符中，该方法将失败。  
  
 如果 DACL 为 NULL，而输入的安全描述符中未设置 SE_DACL_PRESENT 控件位，生成的安全描述符字符串没有 d： 组件。 请参阅[安全描述符字符串格式](http://msdn.microsoft.com/library/windows/desktop/aa379570)有关详细信息。  
  
 此方法调用[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
## <a name="see-also"></a>请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)
