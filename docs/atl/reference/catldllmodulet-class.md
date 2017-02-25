---
title: "CAtlDllModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlDllModuleT"
  - "ATL::CAtlDllModuleT<T>"
  - "ATL::CAtlDllModuleT"
  - "ATL.CAtlDllModuleT<T>"
  - "CAtlDllModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlDllModuleT class"
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlDllModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示DLL的模块。  
  
## 语法  
  
```  
  
      template <  
   class T   
>  
class ATL_NO_VTABLE CAtlDllModuleT :  
   public CAtlModuleT< T >  
```  
  
#### 参数  
 `T`  
 从 `CAtlDllModuleT`派生的选件类。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlDllModuleT::CAtlDllModuleT](../Topic/CAtlDllModuleT::CAtlDllModuleT.md)|构造函数。|  
|[CAtlDllModuleT::~CAtlDllModuleT](../Topic/CAtlDllModuleT::~CAtlDllModuleT.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlDllModuleT::DllCanUnloadNow](../Topic/CAtlDllModuleT::DllCanUnloadNow.md)|如果DLL，可以在测试。|  
|[CAtlDllModuleT::DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md)|返回选件类工厂。|  
|[CAtlDllModuleT::DllMain](../Topic/CAtlDllModuleT::DllMain.md)|选项的入口点动态链接库\(DLL）。|  
|[CAtlDllModuleT::DllRegisterServer](../Topic/CAtlDllModuleT::DllRegisterServer.md)|将项添加到对象的系统注册表中DLL。|  
|[CAtlDllModuleT::DllUnregisterServer](../Topic/CAtlDllModuleT::DllUnregisterServer.md)|移除在系统注册表项在DLL中的对象的。|  
|[CAtlDllModuleT::GetClassObject](../Topic/CAtlDllModuleT::GetClassObject.md)|返回选件类工厂。  调用 [DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md)。|  
  
## 备注  
 `CAtlDllModuleT` 表示动态链接库的\(DLL\)模块并提供所有DLL项目使用的功能。  [CAtlModuleT](../../atl/reference/catlmodulet-class.md) 选件类的此专用化包括用于注册支持。  
  
 有关ATL的模块的更多信息，请参见 [ATL模块选件类](../../atl/atl-module-classes.md)。  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CAtlModuleT Class](../../atl/reference/catlmodulet-class.md)   
 [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)