---
title: "COleConvertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleConvertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleConvertDialog class"
  - "“转换”对话框"
  - "对话框, OLE"
  - "OLE Convert dialog box"
  - "OLE 对话框, Convert"
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleConvertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) 结构。  
  
## 语法  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleConvertDialog::COleConvertDialog](../Topic/COleConvertDialog::COleConvertDialog.md)|构造 `COleConvertDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleConvertDialog::DoConvert](../Topic/COleConvertDialog::DoConvert.md)|执行在对话框中指定的转换。|  
|[COleConvertDialog::DoModal](../Topic/COleConvertDialog::DoModal.md)|显示OLE更改项目"对话框中。|  
|[COleConvertDialog::GetClassID](../Topic/COleConvertDialog::GetClassID.md)|获取 **CLSID** 与该选定的项。|  
|[COleConvertDialog::GetDrawAspect](../Topic/COleConvertDialog::GetDrawAspect.md)|指定是否绘制项目作为图标。|  
|[COleConvertDialog::GetIconicMetafile](../Topic/COleConvertDialog::GetIconicMetafile.md)|具有处理该图元文件与此项目的图标样式的窗体。|  
|[COleConvertDialog::GetSelectionType](../Topic/COleConvertDialog::GetSelectionType.md)|获取选定内容的类型中选择。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleConvertDialog::m\_cv](../Topic/COleConvertDialog::m_cv.md)|控件的行为的结构。|  
  
## 备注  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此选件类。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)