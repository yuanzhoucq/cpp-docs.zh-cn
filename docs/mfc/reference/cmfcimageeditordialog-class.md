---
title: "CMFCImageEditorDialog Class | Microsoft Docs"
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
  - "CMFCImageEditorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImageEditorDialog class"
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCImageEditorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCImageEditorDialog` 选件类支持图像编辑器对话框。  
  
## 语法  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](../Topic/CMFCImageEditorDialog::CMFCImageEditorDialog.md)|构造 `CMFCImageEditorDialog` 对象。|  
  
## 备注  
 `CMFCImageEditorDialog` 选件类提供的对话框:  
  
-   使用修改图像中的各个像素的图像区域。  
  
-   修改像素的绘图工具在图像区域。  
  
-   指定绘制工具使用的颜色调色板。  
  
-   显示操作的预览区域编辑。  
  
 下面的插图显示了图像编辑器对话框。  
  
 ![CMFCImageEditorDialog 对话框](../../mfc/reference/media/imageedit.png "ImageEdit")  
  
 一种使用 `CMFCImageEditorDialog` 对象将它将编辑的 `CBitmap` 图像。  不要生成一个大图像，因为编辑区域的图像的大小限制，调整逻辑像素大小以适合区域。  调用 `DoModal` 方法启动一个模式对话框。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## 要求  
 **标头:** afximageeditordialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)