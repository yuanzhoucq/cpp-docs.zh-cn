---
title: "CComClassFactory Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComClassFactory"
  - "CComClassFactory"
  - "ATL::CComClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactory class"
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComClassFactory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 接口。  
  
## 语法  
  
```  
  
   class CComClassFactory : public IClassFactory,   
public CComObjectRootEx< CComGlobalsThreadModel >  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComClassFactory::CreateInstance](../Topic/CComClassFactory::CreateInstance.md)|创建指定的CLSID的对象。|  
|[CComClassFactory::LockServer](../Topic/CComClassFactory::LockServer.md)|锁定内存的选件类工厂。|  
  
## 备注  
 `CComClassFactory` 实现 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 接口，包含创建的特定CLSID的对象的方法，以及锁定内存的选件类工厂使新的对象快速创建。  必须为您在系统注册表中注册和给的每选件类实现**IClassFactory** 要分配CLSID。  
  
 ATL对象通过派生通常获取选件类工厂从 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  此选件类包括宏 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，声明 `CComClassFactory`，在默认选件类工厂。  若要重写此默认，指定 `DECLARE_CLASSFACTORY`*XXX* 宏之一在类定义中。  例如，[DECLARE\_CLASSFACTORY\_EX](../Topic/DECLARE_CLASSFACTORY_EX.md) 宏来选件类工厂使用指定的选件类:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/CPP/ccomclassfactory-class_1.h)]  
  
 上述类定义指定 **CMyClassFactory** 将用作对象的默认选件类工厂。  **CMyClassFactory** 必须从 `CComClassFactory` 派生并重写 `CreateInstance`。  
  
 ATL提供声明选件类工厂的其他三宏:  
  
-   [DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 使用 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，通过许可证创建的控件。  
  
-   [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 使用 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，在多个单元中创建对象。  
  
-   [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md) 使用 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，构造一个 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 对象。  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)