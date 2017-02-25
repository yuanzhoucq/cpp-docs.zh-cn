---
title: "CPrivateObjectSecurityDesc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CPrivateObjectSecurityDesc"
  - "ATL::CPrivateObjectSecurityDesc"
  - "CPrivateObjectSecurityDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrivateObjectSecurityDesc class"
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CPrivateObjectSecurityDesc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示私有对象安全说明符的对象。  
  
## 语法  
  
```  
  
class CPrivateObjectSecurityDesc : public CSecurityDesc  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](../Topic/CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc.md)|构造函数。|  
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](../Topic/CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](../Topic/CPrivateObjectSecurityDesc::ConvertToAutoInherit.md)|调用此方法将安全说明符，并且其访问控制列表\(acl\) \(ACLs\)对于支持可继承的访问控制项\(ACEs\)的自动传播的格式。|  
|[CPrivateObjectSecurityDesc::Create](../Topic/CPrivateObjectSecurityDesc::Create.md)|调用此方法分配和初始化名为的资源管理器创建私有对象的自相对安全说明符。|  
|[CPrivateObjectSecurityDesc::Get](../Topic/CPrivateObjectSecurityDesc::Get.md)|调用此方法从私有对象的安全说明符检索信息。|  
|[CPrivateObjectSecurityDesc::Set](../Topic/CPrivateObjectSecurityDesc::Set.md)|调用此方法修改私有对象的安全说明符。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=](../Topic/CPrivateObjectSecurityDesc::operator%20=.md)|赋值运算符。|  
  
## 备注  
 此选件类，从派生 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)，为创建和管理私有对象的安全说明符的方法。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 继承层次结构  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [SECURITY\_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc Class](../../atl/reference/csecuritydesc-class.md)