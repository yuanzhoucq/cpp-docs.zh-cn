---
title: "CSecurityDesc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSecurityDesc"
  - "ATL.CSecurityDesc"
  - "CSecurityDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSecurityDesc class"
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CSecurityDesc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 **SECURITY\_DESCRIPTOR** 结构的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CSecurityDesc  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSecurityDesc::CSecurityDesc](../Topic/CSecurityDesc::CSecurityDesc.md)|构造函数。|  
|[CSecurityDesc::~CSecurityDesc](../Topic/CSecurityDesc::~CSecurityDesc.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSecurityDesc::FromString](../Topic/CSecurityDesc::FromString.md)|将字符串格式安全描述符为有效，函数安全说明符。|  
|[CSecurityDesc::GetControl](../Topic/CSecurityDesc::GetControl.md)|从安全说明符检索控件信息。|  
|[CSecurityDesc::GetDacl](../Topic/CSecurityDesc::GetDacl.md)|从安全说明符检索自由访问控制列表\(acl\) \(DACL\)信息。|  
|[CSecurityDesc::GetGroup](../Topic/CSecurityDesc::GetGroup.md)|从安全说明符检索主要组信息。|  
|[CSecurityDesc::GetOwner](../Topic/CSecurityDesc::GetOwner.md)|从安全说明符检索所有者informaton。|  
|[CSecurityDesc::GetPSECURITY\_DESCRIPTOR](../Topic/CSecurityDesc::GetPSECURITY_DESCRIPTOR.md)|返回指向 **SECURITY\_DESCRIPTOR** 结构。|  
|[CSecurityDesc::GetSacl](../Topic/CSecurityDesc::GetSacl.md)|从安全说明符检索系统访问控制列表\(acl\) \(SACL\)信息。|  
|[CSecurityDesc::IsDaclAutoInherited](../Topic/CSecurityDesc::IsDaclAutoInherited.md)|确定是否配置DACL支持自动传播。|  
|[CSecurityDesc::IsDaclDefaulted](../Topic/CSecurityDesc::IsDaclDefaulted.md)|确定安全说明符是否配置为在默认的DACL。|  
|[CSecurityDesc::IsDaclPresent](../Topic/CSecurityDesc::IsDaclPresent.md)|确定安全说明符是否包含一DACL。|  
|[CSecurityDesc::IsDaclProtected](../Topic/CSecurityDesc::IsDaclProtected.md)|确定是否配置DACL防止修改。|  
|[CSecurityDesc::IsGroupDefaulted](../Topic/CSecurityDesc::IsGroupDefaulted.md)|确定安全描述符的组安全标识符\(SID\)默认情况下是否设置为。|  
|[CSecurityDesc::IsOwnerDefaulted](../Topic/CSecurityDesc::IsOwnerDefaulted.md)|确定安全描述符的所有者应默认情况下是否设置为。|  
|[CSecurityDesc::IsSaclAutoInherited](../Topic/CSecurityDesc::IsSaclAutoInherited.md)|确定是否配置SACL支持自动传播。|  
|[CSecurityDesc::IsSaclDefaulted](../Topic/CSecurityDesc::IsSaclDefaulted.md)|确定安全说明符是否配置为在默认SACL。|  
|[CSecurityDesc::IsSaclPresent](../Topic/CSecurityDesc::IsSaclPresent.md)|确定安全说明符是否包含一SACL。|  
|[CSecurityDesc::IsSaclProtected](../Topic/CSecurityDesc::IsSaclProtected.md)|确定是否配置SACL防止修改。|  
|[CSecurityDesc::IsSelfRelative](../Topic/CSecurityDesc::IsSelfRelative.md)|确定安全说明符是否采用自相对格式。|  
|[CSecurityDesc::MakeAbsolute](../Topic/CSecurityDesc::MakeAbsolute.md)|调用此方法将安全描述符为绝对布局。|  
|[CSecurityDesc::MakeSelfRelative](../Topic/CSecurityDesc::MakeSelfRelative.md)|调用此方法将安全描述符为自相对格式。|  
|[CSecurityDesc::SetControl](../Topic/CSecurityDesc::SetControl.md)|设置安全说明符的控件位。|  
|[CSecurityDesc::SetDacl](../Topic/CSecurityDesc::SetDacl.md)|设置在DACL的信息。  如果DACL已经存在安全说明符，则替换。|  
|[CSecurityDesc::SetGroup](../Topic/CSecurityDesc::SetGroup.md)|设置绝对布局安全说明符的主要操作组信息，已替换所有主要组信息存在。|  
|[CSecurityDesc::SetOwner](../Topic/CSecurityDesc::SetOwner.md)|设置绝对布局安全说明符的所有者信息，已替换所有所有者信息存在。|  
|[CSecurityDesc::SetSacl](../Topic/CSecurityDesc::SetSacl.md)|将SACL的信息。  如果SACL已经存在安全说明符，则替换。|  
|[CSecurityDesc::ToString](../Topic/CSecurityDesc::ToString.md)|转换安全说明符转换为字符串格式。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CSecurityDesc::operator const SECURITY\_DESCRIPTOR \*](../Topic/CSecurityDesc::operator%20const%20SECURITY_DESCRIPTOR%20*.md)|返回指向 **SECURITY\_DESCRIPTOR** 结构。|  
|[CSecurityDesc::operator \=](../Topic/CSecurityDesc::operator%20=.md)|赋值运算符。|  
  
## 备注  
 **SECURITY\_DESCRIPTOR** 结构包含安全信息与对象。  应用程序使用此结构设置和查询对象的安全状态。  [AtlGetSecurityDescriptor](../Topic/AtlGetSecurityDescriptor.md)参见。  
  
 应用程序不应直接修改 **SECURITY\_DESCRIPTOR** 结构和应使用提供的选件类方法。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [“安全”示例](../../top/visual-cpp-samples.md)   
 [SECURITY\_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)