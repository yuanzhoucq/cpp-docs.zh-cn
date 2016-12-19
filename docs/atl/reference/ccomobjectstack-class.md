---
title: "CComObjectStack Class | Microsoft Docs"
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
  - "ATL::CComObjectStack"
  - "ATL.CComObjectStack"
  - "ATL::CComObjectStack<Base>"
  - "ATL.CComObjectStack<Base>"
  - "CComObjectStack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectStack class"
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectStack Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类创建一个临时COM对象并为其提供 **IUnknown**的一个骨骼实现。  
  
## 语法  
  
```  
  
      template<  
   class Base   
>  
class CComObjectStack :  
   public Base  
```  
  
#### 参数  
 `Base`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从其他接口包含在对象若要支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComObjectStack::CComObjectStack](../Topic/CComObjectStack::CComObjectStack.md)|构造函数。|  
|[CComObjectStack::~CComObjectStack](../Topic/CComObjectStack::~CComObjectStack.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComObjectStack::AddRef](../Topic/CComObjectStack::AddRef.md)|返回零。  在调试模式，请调用 `_ASSERTE`。|  
|[CComObjectStack::QueryInterface](../Topic/CComObjectStack::QueryInterface.md)|返回 **E\_NOINTERFACE**。  在调试模式，请调用 `_ASSERTE`。|  
|[CComObjectStack::Release](../Topic/CComObjectStack::Release.md)|返回零。  在调试模式，请调用 `_ASSERTE`。  ~|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComObjectStack::m\_hResFinalConstruct](../Topic/CComObjectStack::m_hResFinalConstruct.md)|包含在 `CComObjectStack` 构造对象时返回的 **HRESULT**。|  
  
## 备注  
 `CComObjectStack` 中创建一个临时COM对象和对象提供 **IUnknown**的一个骨骼实现。  通常，在函数内使用对象，局部变量\(即推入堆栈上）。  因为销毁对象，一旦完成功能，引用计数不执行提高效率。  
  
 下面的示例演示如何创建COM对象在函数内部使用:  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/CPP/ccomobjectstack-class_1.cpp)]  
  
 因此当函数完成，临时对象 `Tempobj` 推入堆栈和自动消失。  
  
## 继承层次结构  
 `Base`  
  
 `CComObjectStack`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComObjectGlobal Class](../../atl/reference/ccomobjectglobal-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)