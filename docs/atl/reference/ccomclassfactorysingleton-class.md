---
title: "CComClassFactorySingleton Class | Microsoft Docs"
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
  - "ATL.CComClassFactorySingleton"
  - "ATL.CComClassFactorySingleton<T>"
  - "ATL::CComClassFactorySingleton"
  - "ATL::CComClassFactorySingleton<T>"
  - "CComClassFactorySingleton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactorySingleton class"
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactorySingleton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类从 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 派生并使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 构造一个对象。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
class T  
>  
class CComClassFactorySingleton :  
public CComClassFactory  
```  
  
#### 参数  
 `T`  
 您的选件类。  
  
 `CComClassFactorySingleton` 从 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 派生并使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 构造一个对象。  每个调用 `CreateInstance` 方法查询接口指针将此对象。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComClassFactorySingleton::CreateInstance](../Topic/CComClassFactorySingleton::CreateInstance.md)|查询接口指针的 `m_spObj`。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComClassFactorySingleton::m\_spObj](../Topic/CComClassFactorySingleton::m_spObj.md)|`CComClassFactorySingleton`构造的 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 对象。|  
  
## 备注  
 ATL对象通过派生通常获取选件类工厂从 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  此选件类包括宏 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，声明 `CComClassFactory`，在默认选件类工厂。  若要使用 `CComClassFactorySingleton`，请指定 [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md) 宏在对象类定义。  例如：  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/CPP/ccomclassfactorysingleton-class_1.h)]  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 Class](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread Class](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)