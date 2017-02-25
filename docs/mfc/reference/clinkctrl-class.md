---
title: "CLinkCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinkCtrl class"
  - "控件 [MFC], 链接"
  - "链接 [C++], link control"
  - "SysLink control"
  - "网页, link control"
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见SysLink控件的功能。  
  
## 语法  
  
```  
class CLinkCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CLinkCtrl::CLinkCtrl](../Topic/CLinkCtrl::CLinkCtrl.md)|构造 `CLinkCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CLinkCtrl::Create](../Topic/CLinkCtrl::Create.md)|创建链接控件并将它附加到 `CLinkCtrl` 对象。|  
|[CLinkCtrl::CreateEx](../Topic/CLinkCtrl::CreateEx.md)|用扩展样式创建链接控件并将它附加到 `CLinkCtrl` 对象。|  
|[CLinkCtrl::GetIdealHeight](../Topic/CLinkCtrl::GetIdealHeight.md)|检索链接控件的理想的高度。|  
|[CLinkCtrl::GetIdealSize](../Topic/CLinkCtrl::GetIdealSize.md)|根据该链接的指定宽度加在一起来链接文本的首选高度当前链接控件为;否则为。|  
|[CLinkCtrl::GetItem](../Topic/CLinkCtrl::GetItem.md)|检索链接控件项的状态和属性。|  
|[CLinkCtrl::GetItemID](../Topic/CLinkCtrl::GetItemID.md)|检索链接控件项的ID。|  
|[CLinkCtrl::GetItemState](../Topic/CLinkCtrl::GetItemState.md)|检索链接控件项的状态。|  
|[CLinkCtrl::GetItemUrl](../Topic/CLinkCtrl::GetItemUrl.md)|检索链接控件项表示的URL。|  
|[CLinkCtrl::HitTest](../Topic/CLinkCtrl::HitTest.md)|确定用户是否单击该指定的链接。|  
|[CLinkCtrl::SetItem](../Topic/CLinkCtrl::SetItem.md)|设置链接控件项的状态和属性。|  
|[CLinkCtrl::SetItemID](../Topic/CLinkCtrl::SetItemID.md)|设置链接控件项的ID。|  
|[CLinkCtrl::SetItemState](../Topic/CLinkCtrl::SetItemState.md)|设置链接控件项的状态。|  
|[CLinkCtrl::SetItemUrl](../Topic/CLinkCtrl::SetItemUrl.md)|设置链接控件项表示的URL。|  
  
## 备注  
 “链接控件”窗口提供了一种简便方法嵌入超文本链接。  实际控件是呈现清单的文本并生成相应的应用程序的窗口，当用户单击一个嵌入链接时。  多个链接在控件内支持，并且可由零开始的索引访问。  
  
 此控件\(并 `CLinkCtrl` 选件类\)若要在Windows XP下的程序可用和更高版本上运行。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [SysLink控件](http://msdn.microsoft.com/library/windows/desktop/bb760706)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CLinkCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)