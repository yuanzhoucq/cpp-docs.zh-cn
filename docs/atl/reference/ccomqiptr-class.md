---
title: "CComQIPtr Class | Microsoft Docs"
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
  - "ATL.CComQIPtr"
  - "ATL::CComQIPtr"
  - "CComQIPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComQIPtr class"
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComQIPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

托管COM接口指针的智能指针选件类。  
  
## 语法  
  
```  
  
      template<  
   class T,  
   const IID* piid = &__uuidof(T)  
>  
class CComQIPtr: public CComPtr<T>  
```  
  
#### 参数  
 `T`  
 指定指针类型的COM接口将存储。  
  
 `piid`  
 为 `T`IID的指针。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)|构造函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CComQIPtr::operator \=](../Topic/CComQIPtr::operator%20=.md)|分配指向成员的指针。|  
  
## 备注  
 ATL使用 `CComQIPtr` 和 [CComPtr](../../atl/reference/ccomptr-class.md) 管理COM接口指针，这两个类都是从 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)派生。  两选件类执行自动引用计数通过调用 `AddRef` 和 **Release**。  重载运算符处理指针运算。  
  
## 继承层次结构  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## 要求  
 **Header:** atlcomcli.h  
  
## 请参阅  
 [CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)   
 [CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)   
 [CComPtrBase Class](../../atl/reference/ccomptrbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)