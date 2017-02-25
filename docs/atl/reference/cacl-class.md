---
title: "CAcl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAcl"
  - "ATL::CAcl"
  - "ATLSECURITY/CAcl"
  - "ATL.CAcl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAcl class"
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAcl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 `ACL` \(访问控制列表\)机制的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAcl  
  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|[CAcl::CAccessMaskArray](../Topic/CAcl::CAccessMaskArray.md)|数组 `ACCESS_MASK`s。|  
|[CAcl::CAceFlagArray](../Topic/CAcl::CAceFlagArray.md)|数组 `BYTE`s。|  
|[CAcl::CAceTypeArray](../Topic/CAcl::CAceTypeArray.md)|数组 `BYTE`s。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CAcl::CAcl](../Topic/CAcl::CAcl.md)|构造函数。|  
|[CAcl::~CAcl](../Topic/CAcl::~CAcl.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CAcl::GetAceCount](../Topic/CAcl::GetAceCount.md)|返回访问控制项\(ACE\)对象的数目。|  
|[CAcl::GetAclEntries](../Topic/CAcl::GetAclEntries.md)|从 `CAcl` 对象检索访问控制列表\(acl\) \(ACL\)项。|  
|[CAcl::GetAclEntry](../Topic/CAcl::GetAclEntry.md)|检索所有有关项的信息。`CAcl` 对象。|  
|[CAcl::GetLength](../Topic/CAcl::GetLength.md)|返回ACL的长度。|  
|[CAcl::GetPACL](../Topic/CAcl::GetPACL.md)|返回PACL \(为ACL的指针\)。|  
|[CAcl::IsEmpty](../Topic/CAcl::IsEmpty.md)|测试项的 `CAcl` 对象。|  
|[CAcl::IsNull](../Topic/CAcl::IsNull.md)|返回 `CAcl` 对象的状态。|  
|[CAcl::RemoveAce](../Topic/CAcl::RemoveAce.md)|从 `CAcl` 对象中移除特定ACE \(访问控制项\)。|  
|[CAcl::RemoveAces](../Topic/CAcl::RemoveAces.md)|从 `CAcl` 移除应用于特定 `CSid`的任何一点\(访问控制项\)。|  
|[CAcl::SetEmpty](../Topic/CAcl::SetEmpty.md)|标记 `CAcl` 对象标记为null。|  
|[CAcl::SetNull](../Topic/CAcl::SetNull.md)|标记 `CAcl` 对象转换为 `NULL`。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CAcl::operator const ACL \*](../Topic/CAcl::operator%20const%20ACL%20*.md)|转换为 `ACL` framework的一 `CAcl` 对象。|  
|[CAcl::operator \=](../Topic/CAcl::operator%20=.md)|赋值运算符。|  
  
## 备注  
 **ACL** 结构是ACL \(访问控制列表\)的标头。  ACL包括控件续列出零个或多 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868) \(访问控制项\)。  在ACL的各个ACE从0计算到 *n\-1*，其中 *n* 是一点数ACL的。  在编辑ACL时，应用程序按索引来引用在ACL中的访问控制项\(ACE\)。  
  
 有两个ACL类型:  
  
-   任意  
  
-   系统  
  
 任意ACL由对象或用户的所有者控制对对象的访问的 **WRITE\_DAC** enter。  它指定访问特定用户，并且组可以拥有的对象。  例如，文件的所有者可以使用任意ACL控制哪些用户和组且不能具有对文件的访问权限。  
  
 对象还具有系统级安全信息与其关联，以系统管理员控件的系统ACL的形式。  系统ACL允许系统管理员审核所有尝试访问对象的访问权。  
  
 有关详细信息，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872) 讨论。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)