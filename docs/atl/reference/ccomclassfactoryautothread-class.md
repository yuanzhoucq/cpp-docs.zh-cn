---
title: "CComClassFactoryAutoThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComClassFactoryAutoThread"
  - "ATL.CComClassFactoryAutoThread"
  - "CComClassFactoryAutoThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactoryAutoThread class"
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComClassFactoryAutoThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类在多个单元 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 实现接口，并允许对象创建的。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      class CComClassFactoryAutoThread : public IClassFactory,   
public CComObjectRootEx< CComGlobalsThreadModel >  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComClassFactoryAutoThread::CreateInstance](../Topic/CComClassFactoryAutoThread::CreateInstance.md)|创建指定的CLSID的对象。|  
|[CComClassFactoryAutoThread::LockServer](../Topic/CComClassFactoryAutoThread::LockServer.md)|锁定内存的选件类工厂。|  
  
## 备注  
 `CComClassFactoryAutoThread` 类似于 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但是，允许对象是在多个单元。  若要利用此从 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)支持，派生自己的EXE模块。  
  
 ATL对象通过派生通常获取选件类工厂从 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  此选件类包括宏 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，声明 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，在默认选件类工厂。  若要使用 `CComClassFactoryAutoThread`，请指定 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 宏在对象类定义。  例如：  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/CPP/ccomclassfactoryautothread-class_1.h)]  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 Class](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton Class](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)