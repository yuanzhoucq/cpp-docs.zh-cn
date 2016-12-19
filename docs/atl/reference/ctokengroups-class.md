---
title: "CTokenGroups Class | Microsoft Docs"
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
  - "ATL::CTokenGroups"
  - "ATL.CTokenGroups"
  - "CTokenGroups"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTokenGroups class"
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTokenGroups Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 **TOKEN\_GROUPS** 结构的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CTokenGroups  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CTokenGroups::CTokenGroups](../Topic/CTokenGroups::CTokenGroups.md)|构造函数。|  
|[CTokenGroups::~CTokenGroups](../Topic/CTokenGroups::~CTokenGroups.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CTokenGroups::Add](../Topic/CTokenGroups::Add.md)|添加一 `CSid` 或现有 **TOKEN\_GROUPS** 结构到 `CTokenGroups` 对象。|  
|[CTokenGroups::Delete](../Topic/CTokenGroups::Delete.md)|从 `CTokenGroups` 对象中删除 `CSid` 及其关联的属性。|  
|[CTokenGroups::DeleteAll](../Topic/CTokenGroups::DeleteAll.md)|从 `CTokenGroups` 对象删除所有 `CSid` 对象及其关联属性。|  
|[CTokenGroups::GetCount](../Topic/CTokenGroups::GetCount.md)|返回数目。**CTokenGroups** 对象及其关联属性的包含的 `CSid` 对象。|  
|[CTokenGroups::GetLength](../Topic/CTokenGroups::GetLength.md)|返回 `CTokenGroups` 对象的大小。|  
|[CTokenGroups::GetPTOKEN\_GROUPS](../Topic/CTokenGroups::GetPTOKEN_GROUPS.md)|检索指向 **TOKEN\_GROUPS** 结构。|  
|[CTokenGroups::GetSidsAndAttributes](../Topic/CTokenGroups::GetSidsAndAttributes.md)|检索属于 `CTokenGroups` 对象的 `CSid` 对象和属性。|  
|[CTokenGroups::LookupSid](../Topic/CTokenGroups::LookupSid.md)|检索属性与 `CSid` 对象。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CTokenGroups::operator const TOKEN\_GROUPS \*](../Topic/CTokenGroups::operator%20const%20TOKEN_GROUPS%20*.md)|转换为指针的 `CTokenGroups` 对象。**TOKEN\_GROUPS** 结构。|  
|[CTokenGroups::operator \=](../Topic/CTokenGroups::operator%20=.md)|赋值运算符。|  
  
## 备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述进程或线程的安全性上下文的对象以及分配给每个用户登录到Windows NT或Windows 2000系统上。  
  
 **CTokenGroups** 选件类是 [TOKEN\_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) 结构的包装，包含有关组安全标识符\(SIDs\)的信息在访问令牌。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [“安全”示例](../../top/visual-cpp-samples.md)   
 [CSid Class](../../atl/reference/csid-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)