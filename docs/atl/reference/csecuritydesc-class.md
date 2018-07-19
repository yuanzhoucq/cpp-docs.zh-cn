---
title: CSecurityDesc 类 |Microsoft Docs
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
ms.openlocfilehash: 9968a3601e366628b3539343dde34e956387356a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885759"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 类
此类是包装`SECURITY_DESCRIPTOR`结构。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
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
|[CSecurityDesc::FromString](#fromstring)|转换为有效的、 功能安全描述符字符串格式的安全描述符。|  
|[CSecurityDesc::GetControl](#getcontrol)|检索控件的安全描述符中的信息。|  
|[CSecurityDesc::GetDacl](#getdacl)|从安全说明符中检索自由访问控制列表 (DACL) 信息。|  
|[CSecurityDesc::GetGroup](#getgroup)|从安全说明符中检索的主要组信息。|  
|[CSecurityDesc::GetOwner](#getowner)|从安全说明符中检索所有者信息。|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|返回一个指向`SECURITY_DESCRIPTOR`结构。|  
|[CSecurityDesc::GetSacl](#getsacl)|从安全说明符中检索系统访问控制列表 (SACL) 信息。|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|确定是否 DACL 配置为支持自动传播。|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|确定是否使用默认的 DACL 配置的安全描述符。|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|确定是否安全描述符将包含 DACL。|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|确定是否 DACL 配置为防止进行修改。|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|确定是否默认情况下设置的安全描述符的组安全标识符 (SID)。|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|确定是否默认情况下设置的安全描述符的所有者的 SID。|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|确定是否 SACL 配置为支持自动传播。|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|确定是否使用默认 SACL 配置的安全描述符。|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|确定的安全描述符是否包含 SACL。|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|确定是否 SACL 进行配置以防止修改。|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|确定的安全描述符是否采用自相关格式。|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|调用此方法以将安全描述符转换为绝对格式。|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|调用此方法将转换为自相关格式的安全描述符。|  
|[CSecurityDesc::SetControl](#setcontrol)|设置安全说明符的控制位。|  
|[CSecurityDesc::SetDacl](#setdacl)|设置 DACL 中的信息。 如果 DACL 中已存在的安全描述符，则替换它。|  
|[CSecurityDesc::SetGroup](#setgroup)|设置一个绝对格式安全说明符，替换已存在的任何主要组信息的主要组信息。|  
|[CSecurityDesc::SetOwner](#setowner)|设置替换已存在的任何所有者信息是绝对格式安全描述符的所有者信息。|  
|[CSecurityDesc::SetSacl](#setsacl)|SACL 中设置的信息。 如果 SACL 中已存在的安全描述符，则替换它。|  
|[CSecurityDesc::ToString](#tostring)|将安全描述符转换为字符串格式。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|返回一个指向`SECURITY_DESCRIPTOR`结构。|  
|[CSecurityDesc::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 `SECURITY_DESCRIPTOR`结构包含与对象关联的安全信息。 应用程序使用此结构来设置和查询对象的安全状态。 另请参阅[AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)。  
  
 应用程序不应修改`SECURITY_DESCRIPTOR`结构直接，而应会使用提供的类方法。  
  
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
 *rhs*  
 `CSecurityDesc`对象或`SECURITY_DESCRIPTOR`结构，以分配给新`CSecurityDesc`对象。  
  
### <a name="remarks"></a>备注  
 `CSecurityDesc` （可选） 可以使用创建对象`SECURITY_DESCRIPTOR`结构或以前定义`CSecurityDesc`对象。  
  
##  <a name="dtor"></a>  CSecurityDesc::~CSecurityDesc  
 析构函数。  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源。  
  
##  <a name="fromstring"></a>  CSecurityDesc::FromString  
 转换为有效的、 功能安全描述符字符串格式的安全描述符。  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pstr*  
 包含的以 null 结尾的字符串指针[字符串格式安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379570)要转换。  
  
### <a name="return-value"></a>返回值  
 如果成功则返回 true。 在失败时引发异常。  
  
### <a name="remarks"></a>备注  
 可以通过使用创建的字符串[CSecurityDesc::ToString](#tostring)。 将转换为字符串的安全描述符可以更轻松地存储和传输。  
  
 此方法调用[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
##  <a name="getcontrol"></a>  CSecurityDesc::GetControl  
 检索控件的安全描述符中的信息。  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>参数  
 *psdc*  
 指向`SECURITY_DESCRIPTOR_CONTROL`接收的安全描述符控制信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
### <a name="remarks"></a>备注  
 此方法调用[GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647)。  
  
##  <a name="getdacl"></a>  CSecurityDesc::GetDacl  
 从安全说明符中检索自由访问控制列表 (DACL) 信息。  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pDacl*  
 指向`CDacl`要在其中存储一份安全描述符的 DACL 的结构。 如果存在自定义 ACL，该方法将设置*pDacl*到安全描述符的自定义 ACL 的地址。 如果不存在自定义 ACL，不存储任何值。  
  
 *pbPresent*  
 指向一个值，指示存在指定的安全描述符中的自定义 ACL。 如果安全描述符包含自定义 ACL，此参数设置为 true。 如果安全描述符不包含自定义 ACL，此参数设置为 false。  
  
 *pbDefaulted*  
 指向一个标志设置为在 SE_DACL_DEFAULTED 标志的值`SECURITY_DESCRIPTOR_CONTROL`结构，如果自定义 ACL 存在的安全描述符。 由默认的机制; 如果此标志为 true，检索到的自定义 ACL如果为 false，由用户显式指定自定义 ACL。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getgroup"></a>  CSecurityDesc::GetGroup  
 从安全说明符中检索的主要组信息。  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pSid*  
 指向[CSid](../../atl/reference/csid-class.md) （安全标识符），它接收 CDacl 中存储的组的副本。  
  
 *pbDefaulted*  
 指向一个标志设置为在 SE_GROUP_DEFAULTED 标志的值`SECURITY_DESCRIPTOR_CONTROL`结构，该方法返回时。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getowner"></a>  CSecurityDesc::GetOwner  
 从安全说明符中检索所有者信息。  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pSid*  
 指向[CSid](../../atl/reference/csid-class.md) （安全标识符），它接收 CDacl 中存储的组的副本。  
  
 *pbDefaulted*  
 指向一个标志设置为在 SE_OWNER_DEFAULTED 标志的值`SECURITY_DESCRIPTOR_CONTROL`结构，该方法返回时。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 返回一个指向`SECURITY_DESCRIPTOR`结构。  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)结构。  
  
##  <a name="getsacl"></a>  CSecurityDesc::GetSacl  
 从安全说明符中检索系统访问控制列表 (SACL) 信息。  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pSacl*  
 指向`CSacl`要在其中存储一份安全描述符的 SACL 的结构。 如果存在的系统 ACL，该方法将设置*pSacl*到安全描述符的系统 ACL 的地址。 如果不存在的系统 ACL，不存储任何值。  
  
 *pbPresent*  
 指向方法的标志设置为指示中指定的安全描述符的系统 ACL 的状态。 如果安全描述符包含系统 ACL，此参数设置为 true。 如果安全描述符不包含系统 ACL，此参数设置为 false。  
  
 *pbDefaulted*  
 指向一个标志设置为在 SE_SACL_DEFAULTED 标志的值`SECURITY_DESCRIPTOR_CONTROL`结构，如果系统 ACL 存在的安全描述符。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，false 如果失败，则返回 true。  
  
##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited  
 确定是否自由访问控制列表 (DACL) 配置为支持自动传播。  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符将包含 DACL 的设置以支持自动传播到现有的子对象的可继承的访问控制项 (Ace)，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 为该对象及其现有的子对象执行自动继承算法时，系统将设置此位。  
  
##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted  
 确定是否使用默认自由访问控制列表 (DACL) 配置的安全描述符。  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含默认的 DACL，false 否则，返回 true。  
  
### <a name="remarks"></a>备注  
 此标志会影响系统处理的 DACL，对于访问控制项 (ACE) 继承的方式。 例如，如果对象的创建者未指定 DACL，该对象创建者的访问令牌从接收默认的 DACL。 如果未设置 SE_DACL_PRESENT 标志，系统会忽略此标志。  
  
 此标志用于确定对象上的最终 DACL 的计算方式并不安全对象的安全描述符控制中以物理方式存储。  
  
 若要设置此标志，请使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent  
 确定的安全描述符是否包含自由访问控制列表 (DACL)。  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 DACL，false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 如果未设置此标志，或者如果设置此标志，DACL 为 NULL，安全描述符将允许对每个人都完全访问权限。  
  
 此标志用于保存与某个安全对象相关联的安全描述符之前由调用方指定的安全信息。 与安全对象相关联的安全描述符后，SE_DACL_PRESENT 标志始终设置中的安全描述符控制。  
  
 若要设置此标志，请使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected  
 确定是否自由访问控制列表 (DACL) 进行配置以防止修改。  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果将 DACL 配置为以防止被修改的可继承的访问控制项 (Ace) 的安全描述符，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
 此方法支持可继承 Ace 自动的传播。  
  
##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted  
 确定是否默认情况下设置的安全描述符的组安全标识符 (SID)。  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果默认的机制，而不是原始提供程序的安全描述符，提供的安全描述符的，组 SID，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[csecuritydesc:: Setgroup](#setgroup)方法。  
  
##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted  
 确定是否默认情况下设置的安全描述符的所有者安全标识符 (SID)。  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果默认的机制，而不是原始提供程序的安全描述符，提供的安全描述符的所有者的 SID，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[csecuritydesc:: Setowner](#setowner)方法。  
  
##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited  
 确定是否系统访问控制列表 (SACL) 配置为支持自动传播。  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 SACL 的设置以支持自动传播到现有的子对象的可继承的访问控制项 (Ace)，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 为该对象及其现有的子对象执行自动继承算法时，系统将设置此位。  
  
##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted  
 确定是否使用默认系统访问控制列表 (SACL) 配置的安全描述符。  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含默认 SACL，false 否则，返回 true。  
  
### <a name="remarks"></a>备注  
 此标志会影响系统处理的 SACL，对于访问控制项 (ACE) 继承的方式。 如果未设置 SE_SACL_PRESENT 标志，系统会忽略此标志。  
  
 若要设置此标志，请使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent  
 确定的安全描述符是否包含系统访问控制列表 (SACL)。  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符包含 SACL，false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected  
 确定是否系统访问控制列表 (SACL) 是否配置为防止进行修改。  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果 SACL 配置为阻止的安全描述符可继承的访问控制项 (Ace) 被修改，则返回 true。 否则，返回 false。  
  
### <a name="remarks"></a>备注  
 若要设置此标志，请使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
 此方法支持可继承 Ace 自动的传播。  
  
##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative  
 确定的安全描述符是否采用自相关格式。  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果安全描述符的连续内存块中的所有安全信息是自相关格式，则返回 true。 如果安全描述符采用绝对格式，则返回 false。 有关详细信息，请参阅[Absolute 和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute  
 调用此方法以将安全描述符转换为绝对格式。  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 绝对格式中的安全描述符包含它所包含的信息，而不是本身的信息的指针。 自相关格式中的安全描述符包含连续内存块中的信息。 在自相关的安全描述符，`SECURITY_DESCRIPTOR`结构始终启动信息，但安全描述符的其他组件可以按照任意顺序中的结构。 而不是使用的内存地址，从安全描述符的开头的偏移量进行标识的自相关的安全描述符的组件。 必须存储在磁盘上或通过一种通信协议传输的安全描述符时，此格式非常有用。 有关详细信息，请参阅[Absolute 和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative  
 调用此方法将转换为自相关格式的安全描述符。  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 绝对格式中的安全描述符包含它所包含的信息，而不是包含本身的信息的指针。 自相关格式中的安全描述符包含连续内存块中的信息。 在自相关的安全描述符，`SECURITY_DESCRIPTOR`结构始终启动信息，但安全描述符的其他组件可以按照任意顺序中的结构。 而不是使用的内存地址，通过从安全描述符的开头的偏移量进行标识的安全描述符的组件。 必须存储在磁盘上或通过一种通信协议传输的安全描述符时，此格式非常有用。 有关详细信息，请参阅[Absolute 和 Self-Relative 安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="operator_eq"></a>  CSecurityDesc::operator =  
 赋值运算符。  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *rhs*  
 `SECURITY_DESCRIPTOR`结构或`CSecurityDesc`要分配给`CSecurityDesc`对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CSecurityDesc`对象。  
  
##  <a name="operator_const_security_descriptor__star"></a>  CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 将值转换为一个指向`SECURITY_DESCRIPTOR`结构。  
  
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
 *ControlBitsOfInterest*  
 指示要设置的控制位 SECURITY_DESCRIPTOR_CONTROL 掩码。 可以设置的标志的列表，请参阅[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
 *ControlBitsToSet*  
 指示由指定的控制位的新值的 SECURITY_DESCRIPTOR_CONTROL 掩码*ControlBitsOfInterest*掩码。 此参数可以是为列出的标志的组合*ControlBitsOfInterest*参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 此方法调用[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
##  <a name="setdacl"></a>  CSecurityDesc::SetDacl  
 自由访问控制列表 (DACL) 中设置的信息。 如果 DACL 中已存在的安全描述符，则替换它。  
  
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
 引用`CDacl`对象，它指定安全描述符的 DACL。 此参数不能为 NULL。 若要设置安全描述符中的 NULL DACL，应与一起使用的方法的第一个窗体*bPresent*设置为 false。  
  
 *bPresent*  
 指定一个标志，指示存在 DACL 的安全描述符中。 如果此参数为 true，该方法设置 SE_DACL_PRESENT 标志`SECURITY_DESCRIPTOR_CONTROL`结构，并使用中的值*Dacl*并*bDefaulted*参数。 如果为 false，该方法将清除 SE_DACL_PRESENT 标志，并*bDefaulted*将被忽略。  
  
 *bDefaulted*  
 指定一个标志，指示源的 DACL。 如果此标志为 true，DACL 具有已检索到的一些默认的机制。 如果为 false，DACL 显式指定的用户。 该方法将此值存储在的 SE_DACL_DEFAULTED 标志`SECURITY_DESCRIPTOR_CONTROL`结构。 如果未指定此参数，则清除 SE_DACL_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 没有为空并不存在 DACL 之间的一个重要区别。 如果 DACL 为空，它不包含任何访问控制条目，并显式授予访问权限。 因此，隐式拒绝对对象的访问。 如果对象不具有任何 DACL，另一方面，无保护分配给对象，并授予访问权限的任何请求。  
  
##  <a name="setgroup"></a>  CSecurityDesc::SetGroup  
 设置一个绝对格式安全说明符，替换已存在的任何主要组信息的主要组信息。  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *sid*  
 引用[CSid](../../atl/reference/csid-class.md)安全描述符的新的主组的对象。 此参数不能为 NULL。 安全描述符可以标记为不具有 DACL 或 SACL，但是它必须具有一个组和一个所有者，即使这些是空的 SID （这是一个具有特殊意义的内置 SID）。  
  
 *bDefaulted*  
 指示是否从默认机制派生的主要组信息。 如果此值为 true，它是默认的信息，该方法将此值存储为中的 SE_GROUP_DEFAULTED 标志`SECURITY_DESCRIPTOR_CONTROL`结构。 如果此参数为零，清除 SE_GROUP_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="setowner"></a>  CSecurityDesc::SetOwner  
 设置绝对格式安全描述符的所有者信息。 它取代了已存在的任何所有者信息。  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *sid*  
 [CSid](../../atl/reference/csid-class.md)安全描述符的新主要所有者的对象。 此参数不能为 NULL。  
  
 *bDefaulted*  
 指示是否从默认机制派生的所有者信息。 如果此值为 true，则默认的信息。 该方法将此值存储为中的 SE_OWNER_DEFAULTED 标志`SECURITY_DESCRIPTOR_CONTROL`结构。 如果此参数为零，清除 SE_OWNER_DEFAULTED 标志。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="setsacl"></a>  CSecurityDesc::SetSacl  
 系统访问控制列表 (SACL) 中设置的信息。 如果 SACL 中已存在的安全描述符，则替换它。  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *Sacl*  
 指向`CSacl`对象，它指定安全描述符的 SACL。 此参数不能为 NULL，并且必须 CSacl 对象。 与不同的 Dacl，NULL 和空的 SACL 之间没有区别如 SACL 对象未指定访问权限，只审核信息。  
  
 *bDefaulted*  
 指定一个标志，指示 SACL 的源。 如果此标志为 true，SACL 已检索到的一些默认的机制。 如果为 false，SACL 显式指定的用户。 该方法将此值存储在的 SE_SACL_DEFAULTED 标志`SECURITY_DESCRIPTOR_CONTROL`结构。 如果未指定此参数，则清除 SE_SACL_DEFAULTED 标志。  
  
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
 *pstr*  
 指向以 null 结尾的字符串，以接收[字符串格式安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379570)。  
  
 *si*  
 指定 SECURITY_INFORMATION 位标志以指示要包括在输出字符串中的安全描述符的组件的组合。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 字符串格式的安全描述符后，它可以更轻松地进行存储或传输。 使用`CSecurityDesc::FromString`方法将字符串转换回安全描述符。  
  
 *Si*参数可以包含以下 SECURITY_INFORMATION 标志：  
  
|“值”|含义|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|包括的所有者。|  
|GROUP_SECURITY_INFORMATION|包括主要组。|  
|DACL_SECURITY_INFORMATION|包括 DACL。|  
|SACL_SECURITY_INFORMATION|包括 SACL。|  
  
 如果 DACL 为 NULL 且 SE_DACL_PRESENT 控制位中输入的安全描述符设置，该方法失败。  
  
 如果 DACL 为 NULL，且输入的安全描述符中未设置 SE_DACL_PRESENT 控制位，生成的安全描述符字符串没有 d： 组件。 请参阅[安全描述符字符串格式](http://msdn.microsoft.com/library/windows/desktop/aa379570)的更多详细信息。  
  
 此方法调用[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
## <a name="see-also"></a>请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)
