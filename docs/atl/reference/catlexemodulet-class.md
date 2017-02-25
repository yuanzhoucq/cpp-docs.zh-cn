---
title: "CAtlExeModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlExeModuleT<T>"
  - "CAtlExeModuleT"
  - "ATL.CAtlExeModuleT<T>"
  - "ATL::CAtlExeModuleT"
  - "ATL.CAtlExeModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlExeModuleT class"
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAtlExeModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示应用程序的模块。  
  
## 语法  
  
```  
  
      template <  
   class T   
>  
class ATL_NO_VTABLE CAtlExeModuleT :  
   public CAtlModuleT< T >  
```  
  
#### 参数  
 `T`  
 从 `CAtlExeModuleT`派生的选件类。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlExeModuleT::CAtlExeModuleT](../Topic/CAtlExeModuleT::CAtlExeModuleT.md)|构造函数。|  
|[CAtlExeModuleT::~CAtlExeModuleT](../Topic/CAtlExeModuleT::~CAtlExeModuleT.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlExeModuleT::InitializeCom](../Topic/CAtlExeModuleT::InitializeCom.md)|初始化COM。|  
|[CAtlExeModuleT::ParseCommandLine](../Topic/CAtlExeModuleT::ParseCommandLine.md)|分析命令行，并根据需要进行注册。|  
|[CAtlExeModuleT::PostMessageLoop](../Topic/CAtlExeModuleT::PostMessageLoop.md)|在消息循环退出后，调用此方法。|  
|[CAtlExeModuleT::PreMessageLoop](../Topic/CAtlExeModuleT::PreMessageLoop.md)|此方法在输入消息循环之前调用。|  
|[CAtlExeModuleT::RegisterClassObjects](../Topic/CAtlExeModuleT::RegisterClassObjects.md)|注册选件类对象。|  
|[CAtlExeModuleT::RevokeClassObjects](../Topic/CAtlExeModuleT::RevokeClassObjects.md)|取消选件类对象。|  
|[CAtlExeModuleT::Run](../Topic/CAtlExeModuleT::Run.md)|此方法对EXE模块的代码初始化，运行消息循环，并清理。|  
|[CAtlExeModuleT::RunMessageLoop](../Topic/CAtlExeModuleT::RunMessageLoop.md)|此方法实现消息循环。|  
|[CAtlExeModuleT::UninitializeCom](../Topic/CAtlExeModuleT::UninitializeCom.md)|Uninitializes COM。|  
|[CAtlExeModuleT::Unlock](../Topic/CAtlExeModuleT::Unlock.md)|递减模块的锁计数。|  
|[CAtlExeModuleT::WinMain](../Topic/CAtlExeModuleT::WinMain.md)|此方法实现要求的代码运行EXE。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlExeModuleT::m\_bDelayShutdown](../Topic/CAtlExeModuleT::m_bDelayShutdown.md)|指示的标志应具有关闭模块的延迟。|  
|[CAtlExeModuleT::m\_dwPause](../Topic/CAtlExeModuleT::m_dwPause.md)|用于的暂停值确保所有对象在关闭之前释放。|  
|[CAtlExeModuleT::m\_dwTimeOut](../Topic/CAtlExeModuleT::m_dwTimeOut.md)|用于的超时值延迟卸载模块。|  
  
## 备注  
 `CAtlExeModuleT` 表示应用程序的\(exe\)模块并包含支持创建EXE，处理命令行，注册选件类对象，运行消息循环，并且，清理在退出的代码。  
  
 在EXE服务器的COM对象连续创建和销毁时，此选件类旨在提高性能。  在释放后最后一个COM对象，EXE等待 [CAtlExeModuleT::m\_dwTimeOut](../Topic/CAtlExeModuleT::m_dwTimeOut.md) 数据成员指定持续时间。  如果没有事件在\(即COM对象不会创建\)，关闭进程启动。  
  
 [CAtlExeModuleT::m\_bDelayShutdown](../Topic/CAtlExeModuleT::m_bDelayShutdown.md) 数据成员是使用的标志确定EXE是否应使用定义的框架上面。  如果它设置为false，则该模块将立即停止。  
  
 有关ATL的模块的更多信息，请参见 [ATL模块选件类](../../atl/atl-module-classes.md)。  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlExeModuleT`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [ATLDuck示例](../../top/visual-cpp-samples.md)   
 [CAtlModuleT Class](../../atl/reference/catlmodulet-class.md)   
 [CAtlDllModuleT Class](../../atl/reference/catldllmodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)