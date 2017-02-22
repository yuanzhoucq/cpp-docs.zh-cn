---
title: "COleInsertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleInsertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleInsertDialog class"
  - "对话框, OLE"
  - "Insert Object dialog box"
  - "OLE Insert Object dialog box"
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleInsertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE对象插入对话框。  
  
## 语法  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleInsertDialog::COleInsertDialog](../Topic/COleInsertDialog::COleInsertDialog.md)|构造 `COleInsertDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleInsertDialog::CreateItem](../Topic/COleInsertDialog::CreateItem.md)|在对话框中创建选定的项。|  
|[COleInsertDialog::DoModal](../Topic/COleInsertDialog::DoModal.md)|显示OLE对象插入对话框。|  
|[COleInsertDialog::GetClassID](../Topic/COleInsertDialog::GetClassID.md)|获取 **CLSID** 与该选定的项。|  
|[COleInsertDialog::GetDrawAspect](../Topic/COleInsertDialog::GetDrawAspect.md)|是否指示绘制该项作为图标。|  
|[COleInsertDialog::GetIconicMetafile](../Topic/COleInsertDialog::GetIconicMetafile.md)|具有处理该图元文件与此项目的图标样式的窗体。|  
|[COleInsertDialog::GetPathName](../Topic/COleInsertDialog::GetPathName.md)|具有完整路径在对话框中选定的文件。|  
|[COleInsertDialog::GetSelectionType](../Topic/COleInsertDialog::GetSelectionType.md)|获取对象的类型中选择。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleInsertDialog::m\_io](../Topic/COleInsertDialog::m_io.md)|控件对话框的行为类型 **OLEUIINSERTOBJECT** 的结构。|  
  
## 备注  
 当您要调用此对话框时，请创建选件类 `COleInsertDialog` 对象。  在 `COleInsertDialog` 对象构造后，可以使用 [m\_io](../Topic/COleInsertDialog::m_io.md) framework初始化控件值或状态在对话框中。  `m_io` 机制是类型 **OLEUIINSERTOBJECT**。  有关使用此对话框选件类的更多信息，请参见 [DoModal](../Topic/COleInsertDialog::DoModal.md) 成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此选件类。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) 结构。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)