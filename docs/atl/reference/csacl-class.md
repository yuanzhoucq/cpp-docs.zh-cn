---
title: "CSacl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CSacl"
  - "ATL::CSacl"
  - "CSacl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSacl class"
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSacl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是SACL \(系统访问控制列表\)结构的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CSacl : public CAcl  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSacl::CSacl](../Topic/CSacl::CSacl.md)|构造函数。|  
|[CSacl::~CSacl](../Topic/CSacl::~CSacl.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSacl::AddAuditAce](../Topic/CSacl::AddAuditAce.md)|添加跟踪访问控制项\(ACE\)到 `CSacl` 对象。|  
|[CSacl::GetAceCount](../Topic/CSacl::GetAceCount.md)|返回访问控制项\(ACEs\)数。`CSacl` 对象的。|  
|[CSacl::RemoveAce](../Topic/CSacl::RemoveAce.md)|从 **CSacl** 对象中移除特定ACE \(访问控制项）。|  
|[CSacl::RemoveAllAces](../Topic/CSacl::RemoveAllAces.md)|移除在 `CSacl` 对象包含的任何一点。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CSacl::operator \=](../Topic/CSacl::operator%20=.md)|赋值运算符。|  
  
## 备注  
 SACL包含指定尝试访问的类型生成在域控制器的安全事件日志的审核记录的访问控制项\(ACEs）。  请注意SACL在访问尝试生成的域控制器只生成日志项，不在包含对象的replicate的每个域控制器。  
  
 若要设置或检索对象中的安全说明符的SACL，在请求的线程访问标记必须启用SE\_SECURITY\_NAME权限。  具有此权限授予默认情况下，管理员组，并且可以被授予其他用户或组。  具有该权限授予不需要的所有:在这种权限定义操作可以继续之前，在安全访问标记必须启用此类权限才能生效。  该模型允许的权限为特定操作系统才启用，则会禁用它们何时不再需要。  请参见 [AtlGetSacl](../Topic/AtlGetSacl.md) 和 [AtlSetSacl](../Topic/AtlSetSacl.md) 以启用SE\_SECURITY\_NAME的示例。  
  
 使用提供的选件类方法从 **SACL** 对象添加，移除，创建和删除一点。  请参见 [AtlGetSacl](../Topic/AtlGetSacl.md) 和 [AtlSetSacl](../Topic/AtlSetSacl.md)。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 继承层次结构  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [CAcl Class](../../atl/reference/cacl-class.md)   
 [ACLs](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACEs](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)