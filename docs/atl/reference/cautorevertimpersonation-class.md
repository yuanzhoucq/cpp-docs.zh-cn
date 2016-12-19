---
title: "CAutoRevertImpersonation Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoRevertImpersonation"
  - "CAutoRevertImpersonation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoRevertImpersonation class"
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoRevertImpersonation Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在其超出范围时，此选件类还原到一个nonimpersonating状态的 [CAccessToken](../../atl/reference/caccesstoken-class.md) 对象。  
  
## 语法  
  
```  
  
class CAutoRevertImpersonation  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](../Topic/CAutoRevertImpersonation::CAutoRevertImpersonation.md)|构造 `CAutoRevertImpersonation` 对象|  
|[CAutoRevertImpersonation::~CAutoRevertImpersonation](../Topic/CAutoRevertImpersonation::~CAutoRevertImpersonation.md)|销毁对象并还原访问令牌模拟。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAutoRevertImpersonation::Attach](../Topic/CAutoRevertImpersonation::Attach.md)|自动访问令牌的模拟下。|  
|[CAutoRevertImpersonation::Detach](../Topic/CAutoRevertImpersonation::Detach.md)|取消自动模拟下。|  
|[CAutoRevertImpersonation::GetAccessToken](../Topic/CAutoRevertImpersonation::GetAccessToken.md)|检索访问标记当前与此对象关联的。|  
  
## 备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述进程或线程的安全性上下文的对象以及分配给每个用户登录到Windows NT或Windows 2000系统上。  这些访问令牌只需 `CAccessToken` 选件类表示。  
  
 模拟访问令牌有时需要的。  此选件类提供方便，但是，它不执行访问令牌的模拟;它仅执行自动到下一个nonimpersonated状态。  这是因为，标记访问模拟可以执行几种不同的方式。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [ATLSecurity示例](../../top/visual-cpp-samples.md)   
 [Access Tokens](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Class Overview](../../atl/atl-class-overview.md)