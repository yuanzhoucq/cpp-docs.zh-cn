---
title: "CAtlException Class | Microsoft Docs"
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
  - "CAtlException"
  - "ATL::CAtlException"
  - "ATL.CAtlException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlException class"
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类定义了ATL异常。  
  
## 语法  
  
```  
  
class CAtlException  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlException::CAtlException](../Topic/CAtlException::CAtlException.md)|构造函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAtlException::operator HRESULT](../Topic/CAtlException::operator%20HRESULT.md)|转换为HRESULT值的当前对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlException::m\_hr](../Topic/CAtlException::m_hr.md)|创建由对象和使用的HRESULT类型的变量存储错误状态。|  
  
## 备注  
 `CAtlException` 对象表示异常条件与ATL操作相关。  `CAtlException` 选件类包括存储指示异常和转换运算符的状态代码导致允许您将异常的一个公共数据成员，就好像它是HRESULT。  
  
 通常，将对 `AtlThrow` 而不是直接创建 `CAtlException` 对象。  
  
## 要求  
 **Header:** atlexcept.h  
  
## 请参阅  
 [AtlThrow](../Topic/AtlThrow.md)   
 [Class Overview](../../atl/atl-class-overview.md)