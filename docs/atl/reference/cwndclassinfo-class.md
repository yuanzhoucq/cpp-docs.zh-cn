---
title: "CWndClassInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWndClassInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWndClassInfo class"
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CWndClassInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供注册窗口选件类的信息的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CWndClassInfo  
  
```  
  
## 成员  
  
### 公共方法  
  
|||  
|-|-|  
|[Register](../Topic/CWndClassInfo::Register.md)|注册 Window 类。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_atom](../Topic/CWndClassInfo::m_atom.md)|唯一标识注册窗口选件类。|  
|[m\_bSystemCursor](../Topic/CWndClassInfo::m_bSystemCursor.md)|指定光标资源是否引用一个系统或光标到模块资源包含的光标。|  
|[m\_lpszCursorID](../Topic/CWndClassInfo::m_lpszCursorID.md)|指定光标资源的名称。|  
|[m\_lpszOrigName](../Topic/CWndClassInfo::m_lpszOrigName.md)|包含现有窗口选件类的名称。|  
|[m\_szAutoName](../Topic/CWndClassInfo::m_szAutoName.md)|保存窗口选件类的一个ATL生成的名称。|  
|[m\_wc](../Topic/CWndClassInfo::m_wc.md)|维护窗口中 **WNDCLASSEX** 结构的选件类信息。|  
|[pWndProc](../Topic/CWndClassInfo::pWndProc.md)|指向现有窗口选件类的窗口过程。|  
  
## 备注  
 `CWndClassInfo` 管理窗口选件类的信息。  可以通过三宏通常使用 `CWndClassInfo`，`DECLARE_WND_CLASS`、 `DECLARE_WND_CLASS_EX`或 `DECLARE_WND_SUPERCLASS`之一，如下表所述:  
  
|宏|说明|  
|-------|--------|  
|[DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md)|`CWndClassInfo` 新的windows选件类注册信息。|  
|[DECLARE\_WND\_CLASS\_EX](../Topic/DECLARE_WND_CLASS_EX.md)|`CWndClassInfo` 新的windows选件类注册信息，包括类的边界。|  
|[DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md)|`CWndClassInfo` 基于现有选件类，但在窗口选件类注册信息使用不同的窗口过程。  此方法调用创建超类。|  
  
 默认情况下，[CWindowImpl](../../atl/reference/cwindowimpl-class.md) 包括 `DECLARE_WND_CLASS` 宏创建基于新的windows选件类的窗口。  DECLARE\_WND\_CLASS为控件提供默认样式和背景色。  如果要指定样式和背景色，从 `CWindowImpl` 派生您的选件类并包含 `DECLARE_WND_CLASS_EX` 宏在类定义中。  
  
 如果要创建基于现有窗口选件类的窗口中，从 `CWindowImpl` 派生您的选件类并包含 `DECLARE_WND_SUPERCLASS` 宏在类定义中。  例如：  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/CPP/cwndclassinfo-class_1.h)]  
  
 有关windows选件类的更多信息，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [windows选件类](http://msdn.microsoft.com/library/windows/desktop/ms632596)。  
  
 有关使用窗口的更多信息在ATL，请参见文章 [ATL窗口选件类](../../atl/atl-window-classes.md)。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)