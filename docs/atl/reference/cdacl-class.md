---
title: "CDacl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDacl"
  - "CDacl"
  - "ATL.CDacl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDacl class"
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CDacl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是DACL \(自由访问控制列表\)结构的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CDacl : public CAcl  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CDacl::CDacl](../Topic/CDacl::CDacl.md)|构造函数。|  
|[CDacl::~CDacl](../Topic/CDacl::~CDacl.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CDacl::AddAllowedAce](../Topic/CDacl::AddAllowedAce.md)|添加一个允许的ACE \(访问控制项\)。`CDacl` 对象。|  
|[CDacl::AddDeniedAce](../Topic/CDacl::AddDeniedAce.md)|添加"拒绝的ACE到 `CDacl` 对象。|  
|[CDacl::GetAceCount](../Topic/CDacl::GetAceCount.md)|返回一个点\(访问控制项\)数。`CDacl` 对象。|  
|[CDacl::RemoveAce](../Topic/CDacl::RemoveAce.md)|从 `CDacl` 对象中移除特定ACE \(访问控制项\)。|  
|[CDacl::RemoveAllAces](../Topic/CDacl::RemoveAllAces.md)|移除在 `CDacl` 对象包含的任何一点。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CDacl::operator \=](../Topic/CDacl::operator%20=.md)|赋值运算符。|  
  
## 备注  
 对象的安全说明符可能包含DACL。  DACL包含标识用户和组均可访问对象的零个或多个点\(访问控制项\)。  如果DACL为空\(即它包含零一条\)，没有显式授予访问权限，因此，访问隐式拒绝。  但是，因此，如果对象的安全说明符没有DACL，对象是不受保护的，并且每个人都具有"完全。  
  
 若要检索对象的DACL，您必须是对象的所有者或者可以访问对象的READ\_CONTROL。  若要更改对象的DACL，您必须有权访问对象的WRITE\_DAC。  
  
 使用提供的选件类方法从 `CDacl` 对象创建，添加，移除和删除一点。  请参见 [AtlGetDacl](../Topic/AtlGetDacl.md) 和 [AtlSetDacl](../Topic/AtlSetDacl.md)。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 继承层次结构  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [“安全”示例](../../top/visual-cpp-samples.md)   
 [CAcl Class](../../atl/reference/cacl-class.md)   
 [ACLs](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACEs](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)