---
title: "CDragListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDragListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDragListBox class"
  - "drag list box [C++]"
  - "dragging list items"
  - "列表框"
  - "Windows [C++], 列表框"
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CDragListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除了提供Windows函数以外列表框，`CDragListBox` 选件类允许用户滚动列表框项，例如文件名，在列表框中。  
  
## 语法  
  
```  
class CDragListBox : public CListBox  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDragListBox::CDragListBox](../Topic/CDragListBox::CDragListBox.md)|构造 `CDragListBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDragListBox::BeginDrag](../Topic/CDragListBox::BeginDrag.md)|调用由结构，在拖动操作开始。|  
|[CDragListBox::CancelDrag](../Topic/CDragListBox::CancelDrag.md)|调用由结构，在对拖动操作已取消。|  
|[CDragListBox::Dragging](../Topic/CDragListBox::Dragging.md)|调用由框架在拖动操作过程。|  
|[CDragListBox::DrawInsert](../Topic/CDragListBox::DrawInsert.md)|绘制在拖动过程中插入参考线列表框。|  
|[CDragListBox::Dropped](../Topic/CDragListBox::Dropped.md)|调用由结构，在项目中删除后。|  
|[CDragListBox::ItemFromPt](../Topic/CDragListBox::ItemFromPt.md)|返回正在拖动的项的坐标。|  
  
## 备注  
 列表框获得此功能允许用户按一个列表项在任何方式是最有用于它们。  默认情况下，列表框将移动到个项列表的新位置。  但是，`CDragListBox` 对象可自定义以复制项目而不是将它们。  
  
 列表框控件与 `CDragListBox` 选件类不能有 **LBS\_SORT** 或 **LBS\_MULTIPLESELECT** 样式。  有关说明列表框样式，请参见 [列表框样式](../../mfc/reference/list-box-styles.md)。  
  
 若要使用拖动到现有对话框的列表框应用程序，添加列表框控件添加到对话框模板使用对话框编辑器然后将成员变量\(分类 `Control` 和变量的类型 `CDragListBox`\)与您的对话框模板的列表框控件对应。  
  
 有关给控件的更多信息。成员变量，请参见 [定义的成员变量快捷对话框控件的](../../mfc/defining-member-variables-for-dialog-controls.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例TSTCON](../../top/visual-cpp-samples.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)