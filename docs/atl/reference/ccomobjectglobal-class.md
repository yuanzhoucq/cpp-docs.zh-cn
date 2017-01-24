---
title: "CComObjectGlobal Class | Microsoft Docs"
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
  - "CComObjectGlobal"
  - "ATL::CComObjectGlobal<Base>"
  - "ATL::CComObjectGlobal"
  - "ATL.CComObjectGlobal"
  - "ATL.CComObjectGlobal<Base>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectGlobal class"
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectGlobal Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类管理在包含您的 `Base` 对象的模块的引用数。  
  
## 语法  
  
```  
  
      template<  
   class Base   
>  
class CComObjectGlobal :  
   public Base  
```  
  
#### 参数  
 `Base`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从其他接口包含在对象若要支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComObjectGlobal::CComObjectGlobal](../Topic/CComObjectGlobal::CComObjectGlobal.md)|构造函数。|  
|[CComObjectGlobal::~CComObjectGlobal](../Topic/CComObjectGlobal::~CComObjectGlobal.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComObjectGlobal::AddRef](../Topic/CComObjectGlobal::AddRef.md)|实现全局 `AddRef`。|  
|[CComObjectGlobal::QueryInterface](../Topic/CComObjectGlobal::QueryInterface.md)|实现全局 `QueryInterface`。|  
|[CComObjectGlobal::Release](../Topic/CComObjectGlobal::Release.md)|实现全局 **Release**。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComObjectGlobal::m\_hResFinalConstruct](../Topic/CComObjectGlobal::m_hResFinalConstruct.md)|包含在 `CComObjectGlobal` 构造对象时返回的 **HRESULT**。|  
  
## 备注  
 `CComObjectGlobal` 管理在包含您的 `Base` 对象的模块的引用数。  `CComObjectGlobal` 确保您的对象不会删除，只要不释放模块。  您的对象，并在整个模块的引用数为零，只会移除。  
  
 例如，使用 `CComObjectGlobal`，选件类工厂可以容纳由其所有客户端共享的通用全局对象。  
  
## 继承层次结构  
 `Base`  
  
 `CComObjectGlobal`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComObjectStack Class](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)