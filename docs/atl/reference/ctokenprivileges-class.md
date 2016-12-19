---
title: "CTokenPrivileges Class | Microsoft Docs"
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
  - "ATL::CTokenPrivileges"
  - "CTokenPrivileges"
  - "ATL.CTokenPrivileges"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTokenPrivileges class"
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTokenPrivileges Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 **TOKEN\_PRIVILEGES** 结构的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CTokenPrivileges  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CTokenPrivileges::CTokenPrivileges](../Topic/CTokenPrivileges::CTokenPrivileges.md)|构造函数。|  
|[CTokenPrivileges::~CTokenPrivileges](../Topic/CTokenPrivileges::~CTokenPrivileges.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTokenPrivileges::Add](../Topic/CTokenPrivileges::Add.md)|添加一个或多个权限。`CTokenPrivileges` 对象。|  
|[CTokenPrivileges::Delete](../Topic/CTokenPrivileges::Delete.md)|从 `CTokenPrivileges` 对象删除权限。|  
|[CTokenPrivileges::DeleteAll](../Topic/CTokenPrivileges::DeleteAll.md)|从 `CTokenPrivileges` 对象删除所有权限。|  
|[CTokenPrivileges::GetCount](../Topic/CTokenPrivileges::GetCount.md)|返回权限项的数目。`CTokenPrivileges` 对象的。|  
|[CTokenPrivileges::GetDisplayNames](../Topic/CTokenPrivileges::GetDisplayNames.md)|检索显示名称在 `CTokenPrivileges` 对象包含的权限。|  
|[CTokenPrivileges::GetLength](../Topic/CTokenPrivileges::GetLength.md)|在需要的字节数组返回缓冲区大小保存 **TOKEN\_PRIVILEGES** 结构由 `CTokenPrivileges` 对象。|  
|[CTokenPrivileges::GetLuidsAndAttributes](../Topic/CTokenPrivileges::GetLuidsAndAttributes.md)|从 `CTokenPrivileges` 对象检索本地唯一标识符\(LUIDs\)和属性标志。|  
|[CTokenPrivileges::GetNamesAndAttributes](../Topic/CTokenPrivileges::GetNamesAndAttributes.md)|从 `CTokenPrivileges` 对象检索权限名称和特性标志。|  
|[CTokenPrivileges::GetPTOKEN\_PRIVILEGES](../Topic/CTokenPrivileges::GetPTOKEN_PRIVILEGES.md)|返回指向 **TOKEN\_PRIVILEGES** 结构。|  
|[CTokenPrivileges::LookupPrivilege](../Topic/CTokenPrivileges::LookupPrivilege.md)|检索特性与给定的权限集的名称。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CTokenPrivileges::operator const TOKEN\_PRIVILEGES \*](../Topic/CTokenPrivileges::operator%20const%20TOKEN_PRIVILEGES%20*.md)|将值转换为指针。**TOKEN\_PRIVILEGES** 结构。|  
|[CTokenPrivileges::operator \=](../Topic/CTokenPrivileges::operator%20=.md)|赋值运算符。|  
  
## 备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述进程或线程的安全性上下文的对象以及分配给每个用户登录到Windows NT或Windows 2000系统上。  
  
 访问令牌用于描述各种安全权限授予每个用户。  权限包括调用局部唯一标识符\([LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)\)和说明符字符串的64位数字。  
  
 `CTokenPrivileges` 选件类是 [TOKEN\_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 结构的包装并包含0个或更多的权限。  使用所提供的选件类方法，权限可以添加，删除或已查询。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [“安全”示例](../../top/visual-cpp-samples.md)   
 [TOKEN\_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID\_AND\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)