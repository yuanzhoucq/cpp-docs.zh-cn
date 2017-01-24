---
title: "CAtlServiceModuleT Class | Microsoft Docs"
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
  - "ATL::CAtlServiceModuleT"
  - "ATL.CAtlServiceModuleT"
  - "CAtlServiceModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlServiceModuleT class"
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlServiceModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一服务。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
UINT nServiceNameID   
>  
class ATL_NO_VTABLE CAtlServiceModuleT :  
public CAtlExeModuleT< T>  
```  
  
#### 参数  
 `T`  
 从 `CAtlServiceModuleT`派生的选件类。  
  
 *nServiceNameID*  
 服务的资源标识符。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlServiceModuleT::CAtlServiceModuleT](../Topic/CAtlServiceModuleT::CAtlServiceModuleT.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlServiceModuleT::Handler](../Topic/CAtlServiceModuleT::Handler.md)|服务的处理程序实例。|  
|[CAtlServiceModuleT::InitializeSecurity](../Topic/CAtlServiceModuleT::InitializeSecurity.md)|为服务提供默认安全设置。|  
|[CAtlServiceModuleT::Install](../Topic/CAtlServiceModuleT::Install.md)|安装并创建服务。|  
|[CAtlServiceModuleT::IsInstalled](../Topic/CAtlServiceModuleT::IsInstalled.md)|确认已安装服务。|  
|[CAtlServiceModuleT::LogEvent](../Topic/CAtlServiceModuleT::LogEvent.md)|在事件日志中写入。|  
|[CAtlServiceModuleT::OnContinue](../Topic/CAtlServiceModuleT::OnContinue.md)|重写此方法继续服务。|  
|[CAtlServiceModuleT::OnInterrogate](../Topic/CAtlServiceModuleT::OnInterrogate.md)|重写此方法询问服务。|  
|[CAtlServiceModuleT::OnPause](../Topic/CAtlServiceModuleT::OnPause.md)|重写此方法暂停服务。|  
|[CAtlServiceModuleT::OnShutdown](../Topic/CAtlServiceModuleT::OnShutdown.md)|重写此方法关闭服务|  
|[CAtlServiceModuleT::OnStop](../Topic/CAtlServiceModuleT::OnStop.md)|重写此方法停止服务|  
|[CAtlServiceModuleT::OnUnknownRequest](../Topic/CAtlServiceModuleT::OnUnknownRequest.md)|重写此方法以处理未知的请求传递给服务|  
|[CAtlServiceModuleT::ParseCommandLine](../Topic/CAtlServiceModuleT::ParseCommandLine.md)|分析命令行，并根据需要进行注册。|  
|[CAtlServiceModuleT::PreMessageLoop](../Topic/CAtlServiceModuleT::PreMessageLoop.md)|此方法在输入消息循环之前调用。|  
|[CAtlServiceModuleT::RegisterAppId](../Topic/CAtlServiceModuleT::RegisterAppId.md)|注册在注册表的服务。|  
|[CAtlServiceModuleT::Run](../Topic/CAtlServiceModuleT::Run.md)|管理服务。|  
|[CAtlServiceModuleT::ServiceMain](../Topic/CAtlServiceModuleT::ServiceMain.md)|服务控制管理器调用的方法。|  
|[CAtlServiceModuleT::SetServiceStatus](../Topic/CAtlServiceModuleT::SetServiceStatus.md)|更新服务状态。|  
|[CAtlServiceModuleT::Start](../Topic/CAtlServiceModuleT::Start.md)|调用 `CAtlServiceModuleT::WinMain`，当服务开始。|  
|[CAtlServiceModuleT::Uninstall](../Topic/CAtlServiceModuleT::Uninstall.md)|停止和取消服务。|  
|[CAtlServiceModuleT::Unlock](../Topic/CAtlServiceModuleT::Unlock.md)|递减服务的锁计数。|  
|[CAtlServiceModuleT::UnregisterAppId](../Topic/CAtlServiceModuleT::UnregisterAppId.md)|从注册表中移除服务。|  
|[CAtlServiceModuleT::WinMain](../Topic/CAtlServiceModuleT::WinMain.md)|此方法实现要求的代码管理服务。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlServiceModuleT::m\_bService](../Topic/CAtlServiceModuleT::m_bService.md)|指示程序的标志作为服务运行。|  
|[CAtlServiceModuleT::m\_dwThreadID](../Topic/CAtlServiceModuleT::m_dwThreadID.md)|存储线程标识符的成员变量。|  
|[CAtlServiceModuleT::m\_hServiceStatus](../Topic/CAtlServiceModuleT::m_hServiceStatus.md)|存储句柄的成员变量设置为当前服务状态信息结构。|  
|[CAtlServiceModuleT::m\_status](../Topic/CAtlServiceModuleT::m_status.md)|存储当前服务的成员变量状态信息结构。|  
|[CAtlServiceModuleT::m\_szServiceName](../Topic/CAtlServiceModuleT::m_szServiceName.md)|注册的服务的名称。|  
  
## 备注  
 `CAtlServiceModuleT`，从派生 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)，实现ATL命令舵。  `CAtlServiceModuleT` 用于命令行过程，安装，注册和删除的方法。  如果需要额外的功能，这些功能及其他方法可被重写。  
  
 此选件类替换为使用ATL的早期版本的过时 [CComModule选件类](../../atl/reference/ccommodule-class.md)。  有关详细信息 [ATL模块选件类](../../atl/atl-module-classes.md) 参见。  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)  
  
 `CAtlServiceModuleT`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)