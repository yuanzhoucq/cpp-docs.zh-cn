---
title: "CComSafeArrayBound Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComSafeArrayBound"
  - "ATL::CComSafeArrayBound"
  - "CComSafeArrayBound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeArrayBound class"
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSafeArrayBound Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 [SAFEARRAYBOUND](http://msdn.microsoft.com/zh-cn/303a9bdb-71d6-4f14-8747-84cf84936c6d) 结构的包装。  
  
## 语法  
  
```  
  
class CComSafeArrayBound : public SAFEARRAYBOUND  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CComSafeArrayBound](../Topic/CComSafeArrayBound::CComSafeArrayBound.md)|构造函数。|  
|[GetCount](../Topic/CComSafeArrayBound::GetCount.md)|调用此方法返回元素的数目。|  
|[GetLowerBound](../Topic/CComSafeArrayBound::GetLowerBound.md)|调用此方法返回下限。|  
|[GetUpperBound](../Topic/CComSafeArrayBound::GetUpperBound.md)|调用此方法返回了上限。|  
|[SetCount](../Topic/CComSafeArrayBound::SetCount.md)|调用此方法设置元素的数目。|  
|[SetLowerBound](../Topic/CComSafeArrayBound::SetLowerBound.md)|调用此方法设置下限。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=](../Topic/CComSafeArrayBound::operator%20=.md)|设置 `CComSafeArrayBound` 为新值。|  
  
## 备注  
 此选件类是 [CComSafeArray](../../atl/reference/ccomsafearray-class.md)使用的 **SAFEARRAYBOUND** 结构的包装。  为查询并将它包含单个维 `CComSafeArray` 对象和元素数的上限和下限的方法。  一个多维 `CComSafeArray` 对象使用数组 `CComSafeArrayBound` 对象，每个维度的。  因此，那么，当使用方法例如 [GetCount](../Topic/CComSafeArrayBound::GetCount.md)时，请注意此方法不会返回元素的总数在多维数组的。  
  
 **Header:** atlsafe.h  
  
## 要求  
 **Header:** atlsafe.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)