---
title: "CCommandLineInfo Class | Microsoft Docs"
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
  - "CCommandLineInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "application flags [C++]"
  - "argv argument"
  - "CCommandLineInfo class"
  - "命令行, 分析"
  - "分析, 命令行参数"
  - "启动代码, parsing command-line arguments"
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommandLineInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在分析命令行的帮助在应用程序启动。  
  
## 语法  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCommandLineInfo::CCommandLineInfo](../Topic/CCommandLineInfo::CCommandLineInfo.md)|默认构造 `CCommandLineInfo` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCommandLineInfo::ParseParam](../Topic/CCommandLineInfo::ParseParam.md)|重写此回调分析各个参数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCommandLineInfo::m\_bRunAutomated](../Topic/CCommandLineInfo::m_bRunAutomated.md)|指示找到命令行 **\/Automation** 选项。|  
|[CCommandLineInfo::m\_bRunEmbedded](../Topic/CCommandLineInfo::m_bRunEmbedded.md)|指示找到命令行 **\/Embedding** 选项。|  
|[CCommandLineInfo::m\_bShowSplash](../Topic/CCommandLineInfo::m_bShowSplash.md)|指示初始屏幕是否应显示。|  
|[CCommandLineInfo::m\_nShellCommand](../Topic/CCommandLineInfo::m_nShellCommand.md)|指示shell命令处理。|  
|[CCommandLineInfo::m\_strDriverName](../Topic/CCommandLineInfo::m_strDriverName.md)|如果shell命令是打印，指示驱动器名称;否则为null。|  
|[CCommandLineInfo::m\_strFileName](../Topic/CCommandLineInfo::m_strFileName.md)|指示要打开或打印的文件名;，如果shell命令是新的或DDE，则为。|  
|[CCommandLineInfo::m\_strPortName](../Topic/CCommandLineInfo::m_strPortName.md)|如果shell命令是打印，指示该端口名;否则为null。|  
|[CCommandLineInfo::m\_strPrinterName](../Topic/CCommandLineInfo::m_strPrinterName.md)|如果shell命令是打印，指示打印机名称;否则为null。|  
|[CCommandLineInfo::m\_strRestartIdentifier](../Topic/CCommandLineInfo::m_strRestartIdentifier.md)|则重新启动管理器已经重新启动应用程序，指示重新启动管理器的唯一重新启动标识符。|  
  
## 备注  
 MFC应用程序在其应用程序对象的 [InitInstance](../Topic/CWinApp::InitInstance.md) 功能通常需要创建此选件类的本地实例。  此对象随后传递给 [CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)，重复调用 [ParseParam](../Topic/CCommandLineInfo::ParseParam.md) 加载 `CCommandLineInfo` 对象。  `CCommandLineInfo` 对象随后传递给 [CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md) 处理命令行参数和标志。  
  
 您可以使用此对象封装以下命令行选项和参数:  
  
|命令行参数|已执行的命令|  
|-----------|------------|  
|*app*|新文件。|  
|*app* 文件名|打开文件。|  
|*app* **\/p** 文件名|到默认打印机的打印文件。|  
|*app* **\/pt** 文件名打印机驱动程序端口|到指定的打印机上打印文件。|  
|*app* **\/dde**|启动并等待DDE命令。|  
|*app* **\/Automation**|以OLE自动化服务器。|  
|*app* **\/Embedding**|开始编辑嵌入式OLE项。|  
|*app* **\/Register**<br /><br /> *app* **\/Regserver**|通知应用程序执行所有注册任务。|  
|*app* **\/Unregister**<br /><br /> *app* **\/Unregserver**|通知应用程序执行任何非注册任务。|  
  
 从 `CCommandLineInfo` 派生新选件类来处理其他标志和参数值。  要处理的重写 [ParseParam](../Topic/CCommandLineInfo::ParseParam.md) 新的标志。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)   
 [CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md)