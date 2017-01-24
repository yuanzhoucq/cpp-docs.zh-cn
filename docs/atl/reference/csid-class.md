---
title: "CSid Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSid"
  - "ATL::CSid"
  - "ATL.CSid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSid class"
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSid Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 `SID` \(安全标识符\)机制的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CSid  
  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CSid::CSidArray](../Topic/CSid::CSidArray.md)|`CSid` 对象的数组。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSid::CSid](../Topic/CSid::CSid.md)|构造函数。|  
|[CSid::~CSid](../Topic/CSid::~CSid.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSid::AccountName](../Topic/CSid::AccountName.md)|返回该帐户的名称与 `CSid` 对象。|  
|[CSid::Domain](../Topic/CSid::Domain.md)|返回字段的名称与 `CSid` 对象。|  
|[CSid::EqualPrefix](../Topic/CSid::EqualPrefix.md)|测试相等性 `SID` \(安全标识符\)前缀。|  
|[CSid::GetLength](../Topic/CSid::GetLength.md)|返回 `CSid` 对象的长度。|  
|[CSid::GetPSID](../Topic/CSid::GetPSID.md)|返回指向 `SID` 结构。|  
|[CSid::GetPSID\_IDENTIFIER\_AUTHORITY](../Topic/CSid::GetPSID_IDENTIFIER_AUTHORITY.md)|返回指向 **SID\_IDENTIFIER\_AUTHORITY** 结构。|  
|[CSid::GetSubAuthority](../Topic/CSid::GetSubAuthority.md)|返回在 **SID** 结构的指定subauthority。|  
|[CSid::GetSubAuthorityCount](../Topic/CSid::GetSubAuthorityCount.md)|返回subauthority计数。|  
|[CSid::IsValid](../Topic/CSid::IsValid.md)|测试的有效性 `CSid` 对象。|  
|[CSid::LoadAccount](../Topic/CSid::LoadAccount.md)|更新 `CSid` 对象提供的客户名和字段或现有 `SID` 结构。|  
|[CSid::Sid](../Topic/CSid::Sid.md)|返回ID字符串。|  
|[CSid::SidNameUse](../Topic/CSid::SidNameUse.md)|返回 `CSid` 对象的状态说明。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=](../Topic/CSid::operator%20=.md)|赋值运算符。|  
|[运算符const SID \*](../Topic/CSid::operator%20const%20SID%20*.md)|转换为指针的一个 `CSid` 对象。`SID` 结构。|  
  
### 全局运算符  
  
|||  
|-|-|  
|[运算符\=\=](../Topic/CSid::operator%20==.md)|测试相等的两个安全描述符对象|  
|[运算符\! \=](../Topic/CSid::operator%20!=.md)|测试不相等的两个安全描述符对象|  
|[运算符\<](../Topic/CSid::operator%20%3C.md)|比较两个安全描述符对象的相对值。|  
|[运算符\>](../Topic/CSid::operator%20%3E.md)|比较两个安全描述符对象的相对值。|  
|[运算符\<\=](../Topic/CSid::operator%20%3C=.md)|比较两个安全描述符对象的相对值。|  
|[运算符\>\=](../Topic/CSid::operator%20%3E=.md)|比较两个安全描述符对象的相对值。|  
  
## 备注  
 `SID` 结构是一个可变长度结构唯一标识用户或组。  
  
 应用程序选件此包装类不应直接修改 `SID` 结构，而是使用提供的方法。  请参见 [AtlGetOwnerSid](../Topic/AtlGetOwnerSid.md)、 [AtlSetGroupSid](../Topic/AtlSetGroupSid.md)、 [AtlGetGroupSid](../Topic/AtlGetGroupSid.md)和 [AtlSetOwnerSid](../Topic/AtlSetOwnerSid.md)。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [“安全”示例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)   
 [Operators Alphabetical Reference](../../atl/reference/atl-operators.md)