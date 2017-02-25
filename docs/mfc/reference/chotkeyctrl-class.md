---
title: "CHotKeyCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHotKeyCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHotKeyCtrl class"
  - "hot key controls"
  - "Windows common controls [C++], CHotKeyCtrl"
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CHotKeyCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见快捷键控件的功能。  
  
## 语法  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHotKeyCtrl::CHotKeyCtrl](../Topic/CHotKeyCtrl::CHotKeyCtrl.md)|构造 `CHotKeyCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHotKeyCtrl::Create](../Topic/CHotKeyCtrl::Create.md)|创建一个快捷键控件并将它附加到 `CHotKeyCtrl` 对象。|  
|[CHotKeyCtrl::CreateEx](../Topic/CHotKeyCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个快捷键控件并将它附加到 `CHotKeyCtrl` 对象。|  
|[CHotKeyCtrl::GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md)|从一个快捷键控件检索一个快捷键的虚拟键代码和修改键标志。|  
|[CHotKeyCtrl::GetHotKeyName](../Topic/CHotKeyCtrl::GetHotKeyName.md)|检索键名，在本地字符集，分配给一个快捷键。|  
|[CHotKeyCtrl::GetKeyName](../Topic/CHotKeyCtrl::GetKeyName.md)|检索键名，在本地字符集，分配给指定的虚键控代码。|  
|[CHotKeyCtrl::SetHotKey](../Topic/CHotKeyCtrl::SetHotKey.md)|设置一个快捷键控件的快捷组合键。|  
|[CHotKeyCtrl::SetRules](../Topic/CHotKeyCtrl::SetRules.md)|定义了无效的组合和默认修饰符组合的快捷键控件。|  
  
## 备注  
 “快捷键控件”是让用户创建一个快捷键的窗口。  “快捷键”是用户可以按快速执行操作的组合键。  （例如，用户可以创建活动特定窗口并在Z顺序将它放到顶层\)的快捷键快捷键控件显示用户的选择并确保用户选择一个有效的组合键。  
  
 此控件\(并 `CHotKeyCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 当用户选择了组合键时，应用程序可以从控件检索指定的组合键和使用 **WM\_SETHOTKEY** 消息设置在系统的快捷键。  每当用户按此后快捷键，来自系统的任何部分，windows指定在 **WM\_SETHOTKEY** 消息接收指定 **SC\_HOTKEY**的 `WM_SYSCOMMAND` 消息。  此消息激活接收它的窗口。  快捷键保持活动状态直到调用 **WM\_SETHOTKEY** 退出的应用程序。  
  
 此结构与取决于 **WM\_HOTKEY** 消息和Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) 和 [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) 功能的快捷键不同支持。  
  
 有关使用 `CHotKeyCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)