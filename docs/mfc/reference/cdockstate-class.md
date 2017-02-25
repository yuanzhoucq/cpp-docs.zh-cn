---
title: "CDockState Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockState class"
  - "dock state"
  - "docking control bars"
  - "docking tool windows"
  - "位置, control bar"
  - "大小"
  - "大小, control bar"
  - "states, dockable control bar"
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDockState Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加载的序列化 `CObject` 选件类，卸载或清除一个或多个状态停靠在持久内存\(文件\)的控制条。  
  
## 语法  
  
```  
class CDockState : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDockState::Clear](../Topic/CDockState::Clear.md)|清除停靠状态信息。|  
|[CDockState::GetVersion](../Topic/CDockState::GetVersion.md)|检索存储条状态的版本号。|  
|[CDockState::LoadState](../Topic/CDockState::LoadState.md)|从注册表或.INI文件中检索状态信息。|  
|[CDockState::SaveState](../Topic/CDockState::SaveState.md)|保存状态信息传递给注册表或INI文件。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDockState::m\_arrBarInfo](../Topic/CDockState::m_arrBarInfo.md)|某些属性中存储的停靠状态信息的指针与每个控件条的项。|  
  
## 备注  
 停靠状态包含该栏的大小和位置，以及它是停靠的。  当检索存储的停靠状态，`CDockState` 检查栏的位置时，因此，如果该线条到当前屏幕设置不可见，`CDockState` 缩放条的位置，使其可见。  `CDockState` 的主要目的是保存许多的控制条整个状态和识别二进制格式将保存和加载到注册表，应用程序的.INI文件或状态，则为 `CArchive` 对象的内容的一部分。  
  
 该线条可以是任何可控制条，包括工具栏、状态栏或对话栏。  `CDockState` 对象编写并读取来回文件。`CArchive` 对象。  
  
 [CFrameWnd::GetDockState](../Topic/CFrameWnd::GetDockState.md) 检索所有框架窗口的 `CControlBar` 对象的状态信息并将它放入 `CDockState` 对象。  然后可以编写 `CDockState` 对象的内容存储的 [序列化](../Topic/CObject::Serialize.md) 或 [CDockState::SaveState](../Topic/CDockState::SaveState.md)。  如果以后希望还原控件条的状态在框架窗口中，可以在 `Serialize` 或 [CDockState::LoadState](../Topic/CDockState::LoadState.md)加载该状态，则使用 [CFrameWnd::SetDockState](../Topic/CFrameWnd::SetDockState.md) 应用所保存的状态于框架窗口的控制条。  
  
 有关停靠控件条的更多信息，请参见位于 [控制条](../../mfc/control-bars.md)、 [工具栏:停靠和浮动](../../mfc/docking-and-floating-toolbars.md)和 [Windows框架](../../mfc/frame-windows.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## 要求  
 **Header:** afxadv.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)